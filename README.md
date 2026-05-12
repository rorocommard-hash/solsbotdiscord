# 🌟 Sol's RNG Tracker — Bot Discord

Bot Discord qui surveille les Globaux obtenus sur **Sol's RNG** (Roblox) et ping les joueurs dans un channel dédié.

---

## ⚙️ Installation

### 1. Prérequis
- **Node.js** v18 ou supérieur ([nodejs.org](https://nodejs.org))
- Un **bot Discord** créé sur [discord.com/developers](https://discord.com/developers/applications)

### 2. Cloner / télécharger
Place tous les fichiers dans un dossier.

### 3. Installer les dépendances
```bash
npm install
```

### 4. Configurer `config.json`

| Champ | Description |
|---|---|
| `token` | Token de ton bot Discord (onglet **Bot** sur le portail dev) |
| `clientId` | Application ID (onglet **General Information**) |
| `notificationChannelId` | ID du channel où les globaux seront annoncés |
| `pollIntervalSeconds` | Fréquence de vérification en secondes (60 = 1 min) |

**Comment obtenir l'ID d'un channel ?**
Active le mode développeur dans Discord (Paramètres → Avancé), puis clic droit sur le channel → *Copier l'identifiant*.

### 5. Inviter le bot sur ton serveur
Sur le portail dev → **OAuth2 → URL Generator** :
- Scopes : `bot`, `applications.commands`
- Permissions : `Send Messages`, `Embed Links`, `Mention Everyone`

### 6. Lancer le bot
```bash
npm start
```

---

## 📋 Commandes

| Commande | Description |
|---|---|
| `/link <username>` | Lie ton username Roblox à ton Discord |
| `/unlink` | Supprime ton lien |
| `/links` | *(Admin)* Liste tous les comptes liés |
| `/stats` | Affiche tes stats Sol's RNG |

---

## 🔔 Fonctionnement des notifications

Le bot vérifie l'API de Sol's Tracker toutes les X secondes (selon `pollIntervalSeconds`).  
Quand un **Global** est détecté pour un joueur lié, le bot envoie un embed dans le channel configuré et ping le joueur Discord.

---

## ⚠️ Notes

- L'API utilisée est **https://api.sol-tracker.com** (tracker communautaire non-officiel).  
  Si l'endpoint change, modifie la fonction `fetchSolsData` dans `index.js`.
- Les données sont sauvegardées localement dans `linked_users.json`.
- Pour faire tourner le bot 24h/24, utilise **PM2** : `npm install -g pm2 && pm2 start index.js`
