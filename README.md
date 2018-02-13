# Koalitionsvertrag zwischen CDU, CSU und SPD in Maschinenlesbarer Form

Die Datei [koalitionsvertrag-2018.md](koalitionsvertrag-2018.md) wurde aus der Seite <https://interaktiv.morgenpost.de/koalitionsvertrag-analyse/> extrahiert.

**Keine Gewährleistung für inhaltliche oder typographische Übereinstimmung mit dem Koalitionsvertrag veröffentlicht unter:**

- <https://www.spd.de/fileadmin/Dokumente/Koalitionsvertrag/Koalitionsvertrag_2018.pdf>
- <https://www.cdu.de/system/tdf/media/dokumente/koalitionsvertrag_2018.pdf?file=1>

## Format

Das Quellformat hier ist [Markdown](https://de.wikipedia.org/wiki/Markdown)

## Weitere Formate

Mittels [Pandoc](https://de.wikipedia.org/wiki/Pandoc) kann von Markdown in andere Formate konvertiert werden.

- Koalitionsvertrag 2018 im HTML Format: [koalitionsvertrag-2018.html](koalitionsvertrag-2018.html)
- Koalitionsvertrag 2018 im OpenOffice/LibreOffice Format: [koalitionsvertrag-2018.odt](koalitionsvertrag-2018.odt)
- Koalitionsvertrag 2018 im E-Book Format: [koalitionsvertrag-2018.epub](koalitionsvertrag-2018.epub)
- Koalitionsvertrag 2018 im MS Office Format: [koalitionsvertrag-2018.docx](koalitionsvertrag-2018.docx)
- Koalitionsvertrag 2018 im PDF Format (generiert aus Markdown): [koalitionsvertrag-2018.pdf](koalitionsvertrag-2018.pdf)

Skript für Konvertierung:

```
pandoc -o koalitionsvertrag-2018.docx --toc --toc-depth 2 koalitionsvertrag-2018.md 
pandoc -o koalitionsvertrag-2018.epub --toc --toc-depth 2 koalitionsvertrag-2018.md 
pandoc -o koalitionsvertrag-2018.odt  --toc --toc-depth 2 koalitionsvertrag-2018.md # LibreOffice/OpenOffice
pandoc -o koalitionsvertrag-2018.html --toc --toc-depth 2 koalitionsvertrag-2018.md
pandoc -o koalitionsvertrag-2018.pdf  --toc --toc-depth 2 koalitionsvertrag-2018.md
```


# Zweck

Einmal in Text-Form gebracht, lässt sich der Text einfach analysieren und in andere Darstellungsformen bringen.

## Worthäufigkeit

Die 1000 häufigsten deutschen Wörter kann man hier finden: <http://wortschatz.uni-leipzig.de/Papers/top1000de.txt> (via <https://de.wikipedia.org/wiki/Liste_der_h%C3%A4ufigsten_W%C3%B6rter_der_deutschen_Sprache>)

Ich arbeite mit der Linux-Kommandozeile.

Ich schneide die Liste vor Menschen auf Platz 140 ab:

```
head -n 139 top1000de.txt > top139de.txt
```

Nun kann man sich die häufigsten 20 Wörter berechnen lassen:

```
cat koalitionsvertrag-2018.md | tr -c '[:alnum:]' '[\n*]' | sed 's/.*/\L&/g' | fgrep -v -w -f top139de.txt | sort | uniq -c | sort -nr | head -20
# or
cat koalitionsvertrag-2018.md | sed -e 's/\s/\n/g' | sed 's/.*/\L&/g' | fgrep -v -w -f top139de.txt | sort | uniq -c | sort -nr | head -20
```

### Referenzen:

- <https://unix.stackexchange.com/a/41480/148389>
- <https://unix.stackexchange.com/a/171604/148389>
