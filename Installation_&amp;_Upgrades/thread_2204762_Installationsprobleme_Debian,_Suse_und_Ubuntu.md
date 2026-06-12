---
title: "Installationsprobleme Debian, Suse und Ubuntu"
date: 2014-02-10
forum: Installation &amp; Upgrades
---

### Post by Peter_Breitschuh on 2014-02-10
Nachdem Win8.1 soweit recht ordentlich lief, wollte ich Debian 7.3.0 x64 installieren. Der Installatinsvorgang blieb irgendwann hängen und ich bemerkte unter anderem auch Meldungen wie "Kernel panic". Nach mehreren vergeblichen Versuchen probierte ich es mit Debian 7.2 als Live-System, ebenfalls erfolglos. 

Danach ein Versuch mit OpenSuse 13.1, welches ebenfalls nach kurzer Zeit ohne für mich erkennbare Fehlernachricht stoppte. 

Der nächste Versuch mit Kubuntu 13.10 lief zunächst erfreulich, dauerte zwar endlos lange, aber endlich konnte ich über das Bootmenü Kubuntu starten. 

Nachdem das System vollständig geladen war, wunderte ich mich, dass  die Maus sich zwar bewegen ließ, jedoch keine Reaktion auf die 
gewählten Anwendungen erfolgte, bis sich plötzlich nach langer Zeit ein Fenster öffnete. 

Danach konnte ich feststellen, dass vom Klick bis zur Reaktion immer ca. 5 Sekunden und mehr vergingen. 

Ein  Blick ins Syslog zeigt, dass pro Sekunde 5 bis 6 Eintrgäge erfolgten  mit dem Text "EDID Checksum is invalid, remainder ...." (differend  remainders). 

Meine erste Idee war, das System zu aktualisieren,  aber ich habe keine Ahnung, wie ich das machen muss und wo ich einen  entsprechenden Befehl finde ...

Anschließend war ich froh, wieder Win8.1 zu benutzen, würde aber trotzdem gern mit einem funktionierenden Linux arbeiten. 


MfG inl1ner


Die Hardware:

- Mainboard Asus SaberTooth 990FX R2.0 Rev. 1.xx, BIOS AMI 2005
- Prozessor AMD FX 8350, Model 2 Stepping 0
- RAM 2 x 8 GB GeIL Evo Leggera 1866MHz CL10
- RAID-Controller AMCC 3ware/LSI 9650SE-8LPML
- 2 x Samsung SSD 840 pro 256 GB als RAID-1 (System)
- 5 x Samsung HD642JJ als RAID-5 (Daten)
- GraKa Asus Radeon HD 7750 DCSL 1GD5
- Monitor Dell Ultrasharp U2713HM, Auflösung 2560x1440,
  angeschlossen per DisplayPort
- DVD/BR LiteOn BD-ROM iHOS104
- Evoluent VerticalMouse 3 Wireless

Partitionierung der SSD (Disk 1, Basic MBR): 
- 100GB NTFS Win8.1
- 80GB NTFS leer für künftige Verwendung
- 40GB Ext4 Linux Root
- 16GB Swap

Partitionierung der HDD (Disk 2, Basic GPT): 
- 75GB NTFS Windows XP SP3 für Notfälle
- 1,3TB NTFS Daten
- 1TB Ext4 Linux Home

---

