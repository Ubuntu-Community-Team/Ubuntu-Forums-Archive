---
title: "live installer CD &quot;crc error system halted&quot;"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by domurtag on 2008-11-02
Hi,

My Windows XP laptop died yesterday. The error message (in French) that is displayed at startup is shown at the end of this post.

I decided to try and recover the data by installing Ubuntu on a separate partition. But once I choose any options (other than "Test memory") for the live installer menu, I get the message:

> crc error

-- System halted


I googled this message and it seems this indicates a hardware problem, possibly with the hard disk. Is there anything I can do to try and get a working OS installed, so I can attempt to recover the data?

Thanks in advance,
domurtag

Windows error message:

> Windows n'a pas pu demarrer car le fichier suivant est manquant ou endommage:

\WINDOWS\SYSTEM32\CONFIG\SYSTEM

Vous pouvez tenter de reparer ce fichier en demarrant le programme d'installation de Windows XP avex le CD-ROM original d'installation. Choisissex "R" dans le premier ecran pour demarrer le reparation.

---

### Post by Partyboi2 on 2008-11-02
If you are trying to recover your windows data then try booting the ubuntu live cd and mounting your windows partition and copying your data you want to keep to another medium (usb stick, external hard drive, dvd etc...) You should be able to do this without the need of having to install ubuntu.

For the crc error have you tried running a memory test (memtest)? It should be one of the options at the ubuntu main menu screen.

---

