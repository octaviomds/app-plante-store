# Laravel 13 - MongoDB - Docker

## Prerequis

- PHP >= 8.2
- Composer >= 2.x
- Docker & Docker Compose

---

## Installation du projet

```bash
# Methode 1
composer create-project laravel/laravel demo-project "13.*"

# Methode 2
composer global require laravel/installer
laravel new demo-project
```

---

## Configuration MongoDB

Dans le fichier `.env` :

```env
DB_CONNECTION=mongodb
DB_HOST=127.0.0.1
DB_PORT=27017
DB_DATABASE=demo_database
DB_USERNAME=
DB_PASSWORD=
```

Driver MongoDB :

```bash
composer require mongodb/laravel-mongodb
```

---

## Docker

Demarrer les containers :

```bash
docker compose up -d --build
```

Commandes utiles :

```bash
docker compose ps                        # etat des containers
docker compose logs mongodb              # logs du container MongoDB
docker compose exec app bash             # entrer dans le container app
docker compose down                      # arreter et supprimer les containers
```

---

## Base de donnees (MongoDB Shell)

```bash
# Connexion
docker compose exec mongodb mongosh -u admin -p secret --authenticationDatabase admin

# Selectionner la base
use demo_database

# Creer une collection
db.createCollection("users")

# Creer un index unique
db.users.createIndex({ email: 1 }, { unique: true })
```

---

## Migrations

```bash
php artisan make:migration create_users_collection   # creer une migration
php artisan migrate                                  # executer les migrations
php artisan migrate:status                           # etat des migrations
php artisan migrate:rollback                         # annuler le dernier lot
php artisan migrate:fresh --seed                     # reset complet + seeders
```

---

## Installation de la plateforme

```bash
composer require demo/platform
php artisan demo:install
php artisan demo:admin
php artisan serve
```

---

## Mise a jour

```bash
composer update demoplatform --with-dependencies
php artisan migrate
php artisan optimize:clear
```

---

## Publication et cache

```bash
php artisan demo:publish
php artisan view:clear
php artisan optimize:clear
```

---

## Informations

```bash
php artisan about
```

---

## Recapitulatif des commandes

| # | Commande | Description |
|---|----------|-------------|
| 1 | `composer create-project laravel/laravel demo-project "13.*"` | Creer le projet |
| 2 | `docker compose up -d --build` | Demarrer Docker |
| 3 | `composer require demo/platform` | Installer le package |
| 4 | `php artisan demo:install` | Initialiser la plateforme |
| 5 | `php artisan migrate` | Executer les migrations |
| 6 | `php artisan demo:admin` | Creer l'administrateur |
| 7 | `php artisan serve` | Demarrer le serveur |
| 8 | `composer update demoplatform --with-dependencies` | Mettre a jour |
| 9 | `php artisan demo:publish` | Publier les ressources |
| 10 | `php artisan view:clear` | Vider le cache des vues |
| 11 | `php artisan about` | Infos de l'application |
UTISATION DE TRELLO:

https://trello.com/home
