---
title: "Harddisk AWOL during install"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by rogier.de.groot on 2007-05-16
Hi all. I'm trying to install feisty server on an old P3 system - with two plain old IDE drives. But when I get to the partitioner, one of the has suddenly become a SCSI drive (/dev/sda) and the other is just plain missing! After going through dmesg I think the ata_piix module is to blame, but I don't know how to disable it - probably with some boot parameter, but I don't know which (where the list?).
Please help!

---

### Post by rogier.de.groot on 2007-05-16
Ok, so I switch to a terminal (alt-f2) during the first installation screen, modprobe -r ata_piix and ata_generic, and modprobe ide_generic - presto! harddisk back again! Guess I'm going to have to mess with this after installation too, but I'll cross that bridge when I get to it...

---

### Post by rogier.de.groot on 2007-05-17
Well, if anyone comes across this problem aswell, after the installation was finished, ubuntu suddenly saw *both* harddisks, but saw them as /dev/sda and /dev/sdb! Weird, but hey, it works now and I'm not going to try anything funny to get them back to /dev/hdx.

---

