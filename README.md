

---

# 🛫 Der Dümmste Fliegt

**Ein interaktives Multiplayer-Quizspiel für Livestreams mit OBS-Overlay, Supabase & VDO.Ninja.**

![Logo](logo.svg)

---

## 📦 Projektüberblick

Dieses Projekt ist ein browserbasiertes Spiel, das in Livestreams eingebunden werden kann. Es ermöglicht dir:

* Eine Lobby für Mitspieler zu erstellen
* Fragenrunden zu moderieren
* Einstellung der Rundenlänge
* Kamerabilder der Mitspieler (per VDO.Ninja) im OBS-Overlay einzublenden

---

## 🚀 Live-Demo

> Öffne die `index.html` lokal oder hoste sie auf einem Webserver.
> **Supabase-Anbindung ist erforderlich** für die Spiel-Logik und Synchronisation.

---

## 🧰 Verwendete Technologien

* **HTML + TailwindCSS**: UI-Styling
* **Tone.js**: Soundeffekte
* **Supabase**: Auth, Realtime-Database & Hosting
* **VDO.Ninja**: Kamera-Streams für das Overlay
* **Vanilla JavaScript**: Spiellogik, Routing, Zustandssynchronisation

---

## 📂 Projektstruktur

```
index.html            - Hauptdatei (Frontend + Logik)
logo.svg              - Logo des Spiels
Supabase              - Realtime Backend (nicht im Repo enthalten)
```

---

## 🛠 Setup

### 🔑 Supabase einrichten

1. Projekt auf [supabase.com](https://supabase.com) anlegen

2. Tabelle `games` mit Feldern:

   * `id` (UUID, PK)
   * `lobby_code` (text, unique)
   * `game_data` (jsonb)

3. Aktiviere **Anonymous Auth** unter Auth > Settings > Provider

4. Füge deine Supabase-URL und den `anon`-Key in der `index.html` ein:

```js
const SUPABASE_URL = 'https://...supabase.co';
const SUPABASE_ANON_KEY = 'eyJh...';
```

---

## ▶️ Anwendung starten

1. Öffne `index.html` im Browser
2. Klicke auf **"Neue Lobby erstellen"**
3. Teile den generierten Spieler-Link
4. Binde den OBS-Overlay-Link im Stream ein (z. B. als Browserquelle)

---

## 🎥 Kameraintegration (VDO.Ninja)

1. Erstelle einen Gruppenraum unter [https://vdo.ninja](https://vdo.ninja)
2. Sende deinen Spielern den Einladungslink
3. Kopiere für jeden Spieler den **Solo-Link**
4. Füge diesen Link im Host-Dashboard beim entsprechenden Spieler ein

⚠️ **Wichtig**: Verwende **immer** den individuellen Solo-Link, *nicht* den allgemeinen Raumlink!

---

## 🧪 Spielregeln

* Jeder Spieler hat 3 Leben (Herzen)
* In jeder Runde muss ein Spieler eine Quizfrage beantworten
* Zuschauer stimmen nach jeder Runde ab, wer rausfliegen soll
* Bei den meisten Stimmen verliert ein Spieler ein Herz
* Spieler mit 0 Herzen scheiden aus
* Der letzte verbleibende Spieler gewinnt

---

## 🔐 Sicherheit

* Nutzt **anonyme Authentifizierung** – keine Registrierung notwendig
* Alle Spielzustände werden in Supabase gespeichert
* Jeder Lobby-Code ist eindeutig und 5-stellig

---

## ❓FAQ

**Q: Kann ich das Spiel öffentlich hosten?**
A: Ja, du kannst `index.html` z. B. auf GitHub Pages oder Vercel bereitstellen.

**Q: Wie viele Spieler werden unterstützt?**
A: Es gibt keine harte Begrenzung, aber empfohlen werden max. 10–12 wegen des Overlays.

---

## 📄 Lizenz

MIT License – feel free to use, modify and share.

---
