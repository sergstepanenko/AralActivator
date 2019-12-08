# AralActivator
Script zum automatischen Aktivieren von gekauften Aral Karten (Aral "SuperCard").

## Problemstellung
Aral Karten können ohne Aktivierung nicht verwendet werden.
Das händische Aktivieren vieler Aral Karten kostet Zeit - diese wollen wir uns sparen.
Aral Karten kauft man idR nur, wenn es Rabatte gibt wie z.B. hier (Nov. 2019):

https://www.mydealz.de/deals/aral-supercard-fur-50-kaufen-5-geschenkt-1465573

https://www.mydealz.de/deals/aral-supercard-einkaufen-und-tanken-fur-30-kaufen-5-supercard-einkaufen-und-tanken-geschenkt-jeweils-36-monate-gultig-1477242

## Eigenschaften von Aral (Tank-)Karten
Die Karten kommen per Post.
Jeder Bestellung, die idealerweise nur eine zu aktivierende Karte enthält ist ein Lieferschein mit folgenden relevanten Informationen beigelegt:
- Bestellnummer (9-stellig[?])
- Aktivierungscode (6-10-stellig [Lt. Webseite, Stand 27.11.2019])

Zudem stehen auf jeder Aral Karte Folgende Infos:
- Aral SuperCard Nr. (19-stellig, meist sind mind. die ersten 8 Stellen gegeben)
- Registrierungscode (4-stellig)
- Seriennummer (10-stellig) [irrelevant]
Per E-Mail bekommt man dann einen Aktivierungscode, der für die gesamte Bestellung(?) gilt - meistens muss man sowieso nur eine Karte aktivieren.

## Haltbarkeit und Einlösebedingungen
- SuperCards sind ab Aktivierungsdatum 3 Jahre lang' gültig
- Manche der gratis Karten werden erst zu einem bestimmten Datum automatisch von Aral aktiviert

## Grundsätzliche Idee
Die Aral E-Mails mit den Bestellnummern + Aktivierungscode abgreifen und dann automatisch alle Karten aller Bestellungen hier aktivieren:
https://www.aral-supercard.de/services/bestellungen/
Der Kartenwert einzelner Bestellungen bzw. Karten lässt sich hier extrahieren:
https://www.aral-supercard.de/services/bestellungen/detailansicht/<Bestellnummer>

## Installation (Windows)
1. Installiere Python 3
2. Installiere folgende python Module:
mechanize
3. Starte AralActivator.py per Doppelklick.

## Anleitung [Vollautomatische Version - empfohlen]
1. Sammle alle Mails mit Aral Aktivierungscodes und füge deren Inhalt in eine Datei namens "mails.txt" ein. Dieser Schritt wird mit einer der nächsten Versionen noch automatisiert!
Tipp: Im GMail Webmailer findest du die Mails z.B. so:
`subject:("aktivierung ihrer aral supercard")`
Die mails.txt Datei muss in dem Ordner liegen, in dem sich auch das Script befindet.
2. Starte das Script. Es wird dich beim ersten Start nach deinen Aral-Supercard.de Zugangsdaten fragen.
3. Das Script wird nun alle Karten aus deiner Aral Bestellübersicht aktivieren zu denen es in den Mails die passenden Aktivierungscodes findet.
Am Ende wird ggf. eine Übersicht der fehlgeschlagenen Aktivierungen angezeigt.

## Anleitung [Halbautomatische Version]
1. Lege alle zu aktivierenden Aral Karten samt Lieferschein auf eine Oberfläche in der Nähe deines PCs.
2. Sammle die Inhalte aller Aral Aktivierungs-Mails und kopiere sie in eine Textdatei mit dem Namen 'mails.txt'.
Kopiere diese in den Ordner, in dem auch das Script liegt.
Tipp: Im GMail Webmailer findest du die Mails z.B. so:
`subject:("aktivierung ihrer aral supercard")`
3. Starte das Script. Es sollte alle Bestellnummern samt Aktivierungscodes automatisch erfassen und dich nach den restlichen Informationen fragen.
4. Solltest du keine Lust mehr auf weitere Aktivierungsvorgänge hast, beende das Programm übers Menü und nicht über das "X", sodass der status gespeichert werden kann.

Du kannst bei jedem Start neue mails in die mails.txt legen - es macht nichts, wenn bereits hinzugefügte Mails in der Datei verbleiben.

Tipps für die halbautomatische Version:
Füge maximal 10 zu aktivierende Karten/EMails gleichzeitig ein es sei denn du bist sehr gut organisiert, hast gute Augen und eine große Fläche zum Ausbreiten von Karten samt Lieferscheinen.

## Fehler und deren Bedeutung
1. "Email crawler failed: Length mismatch":

Vermutlich hat Aral die Textbausteine der Aktivierungs-Mails geändert. Bitte lass' mir eine (zensierte) Fassung deiner Mails zukommen, damit ich das aktualisieren kann.

## Dateien und deren Inhalt
vouchers.json:
Enthält alle vom Script gesammelten Infos zu deinen Karten.
Du solltest diese Datei nicht löschen - nur dann kann der Activator auch in Zukunft zuverlässig funktionieren (z.B. bereits hinzugefügte Bestellungen/Karten überspringen).
settings.json:
Enthält die Einstellungen des Scripts

settings.json:
Enthält die aral-supercard.de Zugangsdaten und alle möglichen Einstellungen.
requires_account --> Falls deaktiviert lassen sich Codes auch manuell und ohne aral-supercard.de Account aktivieren (nicht empfohlen).

## Bekannte Fehler auf der Aral Webseite
Wenn man eine komplette Bestellung aus Versehen mehrfach aktiviert, enthält die Detailansicht (/services/bestellungen/detailansicht/<Bestellnummer>) mehrere Einträge, obwohl eigentlich nur eine Karte aktiviert wird.
Screenshot:
TODO

## TODOs (Geordnet nach Prioritäten)
- IMAP E-Mail Crawler ergänzen
- Mehr Fehlertoleranz

## Links
Karten hier 'manuell' bzw. ohne sich einzuloggen aktivieren:
https://www.aral-supercard.de/services/karte-aktivieren/
Mehrere Karten/Bestellungen hier (einfacher) aktivieren, wenn man eingeloggt ist:
https://www.aral-supercard.de/services/bestellungen/

Hier Guthaben abfragen (Captcha notwendig!):
https://www.aral-supercard.de/services/kartenguthaben-abrufen/