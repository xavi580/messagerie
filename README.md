# Backend — Messagerie temps réel

Serveur API (Express) + temps réel (Socket.io) avec authentification JWT et persistance JSON locale.

## Lancer

```bash
npm install
npm start
```

Le serveur écoute sur `http://localhost:3000`.

## Points d'entrée (API REST)

| Méthode | Route | Description |
| --- | --- | --- |
| POST | `/api/auth/register` | Créer un compte (`username`, `email`, `password`) |
| POST | `/api/auth/login` | Se connecter (`email` ou `username` + `password`) |
| GET  | `/api/auth/me` | Récupérer le profil courant |
| GET  | `/api/users?q=` | Rechercher des utilisateurs |
| GET  | `/api/conversations` | Liste des conversations |
| POST | `/api/conversations` | Créer/retrouver une discussion (`userId`) |
| GET  | `/api/conversations/:id/messages` | Historique des messages |

## Événements Socket.io

- `message:send` → envoyer un message
- `message:new` → réception d'un nouveau message
- `typing` → indication de saisie
- `presence` → statut en ligne / hors ligne

## Notes

- Les données sont stockées dans `data/db.json` (simple à comprendre ; remplacez par MongoDB/PostgreSQL en production).
- Changez `JWT_SECRET` avant toute mise en production.
