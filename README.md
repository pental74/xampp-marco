# xampp

## 🌐 Panoramica Environment Codespaces

Questo repository configura un ambiente di sviluppo completo in GitHub Codespaces con PHP 8.4, Apache, MariaDB e phpMyAdmin, ottimizzato per sviluppo web full-stack.

### ✅ Componenti principali

- `.devcontainer/`: configurazione per Codespaces con Docker Compose multi-servizio.
- `src/`: codice PHP dell'applicazione (document root del web server).

---

## 🧩 Aspetti chiave della configurazione

### Ambiente containerizzato
- **PHP 8.4 + Apache**: immagine custom con estensioni essenziali (MySQL, PDO, ZIP) e Xdebug per debugging.
- **MariaDB 11.3**: database persistente con volume dedicato; credenziali preconfigurate (root/root, user/user).
- **phpMyAdmin**: interfaccia web per gestione database, accessibile su porta 8080.
- **Document root**: impostato su `src/` per isolare il codice applicativo.

### Integrazione VS Code
- Estensioni automatiche: PHP Debug (Xdebug) e Intelephense per intellisense avanzato.
- Porte forwardate: 3000 per l'app PHP, 8080 per phpMyAdmin.
- Sicurezza Git: directory marcata come sicura per evitare warning.

### Persistenza dati
- Volume MariaDB montato localmente in `.devcontainer/mariadb_data/` per mantenere dati tra riavvii.

---

## ▶️ Accesso ai servizi

- Applicazione PHP: `http://localhost:3000`
- phpMyAdmin: `http://localhost:8080`
- Database: host `db`, database `root_db`, utenti `root` o `user`

---

## 🛠️ Note di sviluppo

- Modifica il codice in `src/`; le modifiche sono riflesse immediatamente grazie al volume montato.
- Usa Composer per dipendenze PHP (già installato nel container).
- Per debugging, configura Xdebug nell'estensione VS Code PHP Debug.
- Il container PHP ha Apache con mod_rewrite abilitato per URL rewriting.

---

## 📌 Comandi utili

- Avvia manualmente: `docker compose -f .devcontainer/docker-compose.yml up --build`
- Arresta: `docker compose -f .devcontainer/docker-compose.yml down`
- Accesso container: `docker compose -f .devcontainer/docker-compose.yml exec php-app bash`
- **In caso di NON FUNZIONAMENTO DI PHPMYADMIN, cancellare la cartella mariadb_data/ e riavviate la sessione.**
