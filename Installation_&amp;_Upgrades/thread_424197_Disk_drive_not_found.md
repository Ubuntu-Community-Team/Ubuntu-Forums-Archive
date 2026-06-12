---
title: "Disk drive not found"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by dialbat on 2007-04-26
Hello  there!

I'm installing Ubuntu 7.04 on HP XW4100. No fancy hardware. I've installed Linux CentOS/RedHAt/Mandrake an  others many times no problem.
When i install Ubuntu, after bunch of regular steps i get "disk not found, please select driver".
I have Western Digital hdd, i can't find controller thats being used, but I've tried some of the drivers with out success. It's an IDE drive, not even SATA.

Any idea?

Thank you

PS. same thing with 6.10 version.

---

### Post by ludichrisspeed on 2007-07-26
I have the same issue, the drivers for Western Digital aren't condusive to installing a clean linux OS.  I can't seem to work it out....help!

---

### Post by Pedricko on 2007-08-05
I too am having this problem.

---

### Post by Pumalite on 2007-08-05
Sometimes going to BIOS>IDE Configuration>Set to 'Enhanced Support fo PATA+SATA' works. Try it.
Set Mode to Auto

---

### Post by dabl on 2007-08-05
Here's a thread that might help: [http://ubuntuforums.org/showthread.php?t=517844](http://ubuntuforums.org/showthread.php?t=517844)

Says there you need to go into BIOS and set the HDD mode to "AUTO" for that drive. :)

---

### Post by Pedricko on 2007-08-05
The only options I can change are:

Multisector transfer mode
Transfer Mode
Translation Mode

This disk is IDE, and worked in Dapper.

---

### Post by Pumalite on 2007-08-05
I would go with dabl and set Mode to Auto. I couldn't help you with you specific BIOS. Maybe dabl can help.

---

### Post by Pedricko on 2007-08-05
Looks like I'll just install dapper (which I've had to request a CD for) and dist-upgrade, as there is no way around this.

---

