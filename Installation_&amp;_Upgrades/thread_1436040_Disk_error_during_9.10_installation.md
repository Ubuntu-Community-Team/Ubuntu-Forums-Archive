---
title: "Disk error during 9.10 installation"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by nrobinson on 2010-03-22
Hello,

I got my sister who lives several thousand km away to install 32 bit ubuntu 9.10.

Her pc has a single IDE hdd. During installation the option "use whole disk" was selected.

At 23% the instillation failed while copying the files to the hdd.
The error was something like "Error copying files ... please clean the instillation cd, etc..."

She ran a check of the instillation disk integrity from the try/install/etc menu that appears after booting to the disk.

This check was passed.

Is there any way using the live cd that I can get her to check her hdd for problems before I send her off to buy another one?

Thanks,
Nathan

---

### Post by lemming465 on 2010-03-25
First have her boot with the memtest86+ option and test her RAM for least 20 minutes, or maybe overnight.  Assuming the memory checks out at OK, see [the faulty hardware help page]("https://help.ubuntu.com/community/FaultyHardware") for some advice on using either smartctl or badblocks to verify the disk integrity.

---

### Post by QIII on 2010-03-25
Start the memtest just before bed and let it run.

20 minutes is definitely not enough.

---

### Post by bumanie on 2010-03-25
Sometimes an alternate cd installation of ubuntu overcomes these issues as it is text based - it may be worth a try, however doing a memtest first (as suggested above), will not do any harm. It will at least rule out a problem with ram if all comes up OK. Sometimes is worth doing an [md5 checksu]("https://help.ubuntu.com/community/HowToMD5SUM")m of your download to ensure the download was not corrupted in any way.

---

