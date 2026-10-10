---
name: seo-geo-sicherheit
description: Prüft eine statische Webseite (HTML, CSS, JS) auf SEO (Google findet sie), GEO (KI-Assistenten wie ChatGPT können sie verstehen und empfehlen) und Sicherheit. Er vergibt Punkte, erklärt alles in einfachem Deutsch und repariert nur, wenn man ihn darum bittet. Verwenden, wenn jemand eine Webseite prüfen, für Google oder KI-Suche verbessern oder sicherer machen möchte.
---

# SEO, GEO und Sicherheit für Anfänger-Webseiten

Du prüfst eine kleine Webseite, die meistens aus `index.html`, CSS und eventuell Bildern besteht. Die Person, die dich nutzt, ist **Anfänger**. Erkläre deshalb alles in einfachem Deutsch, ohne Fachchinesisch. Wenn ein Fachwort nötig ist, erkläre es in einem kurzen Halbsatz.

## Ablauf

Es gibt zwei Modi. Führe immer nur den Modus aus, der verlangt wird.

1. **Prüfen** (Standard, wenn nichts anderes gesagt wird): Lies alle Dateien der Webseite im aktuellen Ordner. **Ändere nichts.** Schreib einen Bericht nach der Vorlage unten.
2. **Reparieren** (nur wenn die Person „repariere“, „verbessere“ oder „behebe“ sagt): Behebe die Punkte aus dem Bericht. Ändere das Design und die Texte so wenig wie möglich. Prüfe danach erneut und zeig die neue Punktzahl neben der alten.

## Wichtige Regeln

- **Erfinde nie Fakten.** Fehlen Angaben wie Adresse, Öffnungszeiten, Preise oder Telefonnummer, setze einen gut sichtbaren Platzhalter wie `[Adresse eintragen]` und sag am Ende, was die Person selbst ausfüllen muss.
- **Keine fremden Skripte, Tracker oder Dienste** einbauen. Kein Google Analytics, keine Cookie-Banner von Drittanbietern, keine externen Schriftarten, außer die Seite nutzt sie schon.
- **Keine Schlüssel, Passwörter oder Tokens** in Dateien schreiben. Findest du welche, melde das als ersten und wichtigsten Punkt.
- **Arbeite nur im aktuellen Ordner.** Nichts herunterladen, nichts installieren, nichts hochladen.

## Die Prüfpunkte (100 Punkte)

### A · SEO, „Google findet dich“ (40 Punkte)
| Punkt | Was prüfen | Punkte |
|---|---|---|
| A1 | `<html lang="de">` (oder passende Sprache) gesetzt | 3 |
| A2 | `<title>` vorhanden, aussagekräftig, 30–60 Zeichen, enthält Thema + Ort/Marke | 6 |
| A3 | `<meta name="description">` vorhanden, 70–160 Zeichen, lädt zum Klicken ein | 6 |
| A4 | Genau **eine** `<h1>`, danach sinnvolle `<h2>`/`<h3>`-Reihenfolge | 5 |
| A5 | Alle Bilder haben ein beschreibendes `alt` (nicht „Bild1“) | 5 |
| A6 | `<meta name="viewport" ...>` für Handys | 4 |
| A7 | Bilder nicht unnötig groß, `loading="lazy"` für Bilder weiter unten | 3 |
| A8 | Open-Graph-Angaben (`og:title`, `og:description`, `og:image`) für schöne Vorschauen in WhatsApp und Social Media | 4 |
| A9 | Links haben sprechende Texte (nicht „hier klicken“) | 2 |
| A10 | `robots.txt` und `sitemap.xml` vorhanden (bei mehreren Seiten) bzw. nicht nötig bei einer Seite = volle Punkte | 2 |

### B · GEO, „KI-Assistenten verstehen und empfehlen dich“ (30 Punkte)
| Punkt | Was prüfen | Punkte |
|---|---|---|
| B1 | Gleich oben steht klar: **Wer** ist das, **was** wird angeboten, **wo** und **für wen** | 8 |
| B2 | Ein **FAQ-Abschnitt** mit 3–6 echten Fragen und kurzen, klaren Antworten | 7 |
| B3 | **Strukturierte Daten** (JSON-LD), passend zum Thema, z. B. `LocalBusiness`, `Organization`, `Person`, `Event` oder `FAQPage`. Nur echte Angaben, sonst Platzhalter | 7 |
| B4 | Fakten als Text, nicht nur im Bild (Preise, Zeiten, Ort sind lesbar) | 4 |
| B5 | KI-Suchbots werden nicht ausgesperrt: Falls es eine `robots.txt` gibt, blockiert sie weder `Googlebot` noch `OAI-SearchBot` (ChatGPT-Suche) noch `PerplexityBot`. Hinweis: Für die ChatGPT-Suche zählt der OAI-SearchBot. Das Training von KI-Modellen (`GPTBot`) darf man trotzdem verbieten | 4 |

**Ehrlich bleiben:** Keine Prüfung kann garantieren, dass ChatGPT eine Seite empfiehlt. Sag das immer dazu. Eine `llms.txt` ist ein freiwilliger Bonus. Es ist nicht bewiesen, dass sie wirkt, deshalb gibt es dafür keine Punkte.

### C · Sicherheit (30 Punkte)
| Punkt | Was prüfen | Punkte |
|---|---|---|
| C1 | **Keine Schlüssel, Passwörter, Tokens** oder privaten Daten im Code | 10 |
| C2 | Keine eingebundenen fremden Skripte von unbekannten Seiten. Wenn doch nötig: von bekannten Anbietern und mit fester Version | 5 |
| C3 | Links mit `target="_blank"` haben `rel="noopener noreferrer"` | 3 |
| C4 | Formulare schicken Daten nur an ein bekanntes Ziel (z. B. Netlify Forms) oder sind nur ein `mailto:`-Link. Keine Formulare, die Passwörter oder Bankdaten abfragen | 5 |
| C5 | Alle Links und Bilder nutzen `https://` | 3 |
| C6 | Sicherheits-Header vorbereitet: Datei `_headers` für Netlify mit `X-Content-Type-Options: nosniff`, `Referrer-Policy: strict-origin-when-cross-origin`, `X-Frame-Options: DENY`, `Permissions-Policy: camera=(), microphone=(), geolocation=()` und einer passenden `Content-Security-Policy`. Für GitHub Pages zusätzlich eine `<meta http-equiv="Content-Security-Policy" ...>` im `<head>`, weil GitHub Pages keine eigenen Header erlaubt | 4 |

Achtung bei C6: Die Content-Security-Policy darf die Seite nicht kaputt machen. Erlaube genau das, was die Seite wirklich nutzt (z. B. eigene Bilder, eingebundene Schriften). Prüfe nach dem Reparieren, ob die Seite noch normal aussieht.

## Vorlage für den Bericht

Schreib den Bericht genau so:

```
# Prüfbericht: [Name der Seite]

**Gesamt: XX von 100 Punkten**
SEO: XX/40 · GEO: XX/30 · Sicherheit: XX/30

## Das ist schon gut
- (2–4 Punkte)

## Das fehlt noch (wichtigstes zuerst)
| Nr. | Problem in einfachen Worten | Warum wichtig | Punkte |
|---|---|---|---|

## Das musst du selbst eintragen
- (Platzhalter, echte Daten, die nur du kennst)

Sag „repariere alles“, dann behebe ich die Punkte.
```

Beim Reparieren schreibst du am Ende:

```
**Vorher: XX → Nachher: YY von 100 Punkten**
Geändert: (kurze Liste der Dateien und was sich geändert hat)
Bitte noch selbst eintragen: (Platzhalter-Liste)
```
