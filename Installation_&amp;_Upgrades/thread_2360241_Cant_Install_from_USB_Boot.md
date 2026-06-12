---
title: "Cant Install from USB Boot"
date: 2017-05-02
forum: Installation &amp; Upgrades
---

### Post by mythicpaw on 2017-05-02
Hello everyone, 

I couldn't install ubuntu from USB. I use win 10 and used Rufus to bootable USB. USB was booted and installation screen shows up. Asked 4 option and I tried the first Installation from USB but screen crashed. After that, I tried open from USB but the same result.

I'm using the desktop.

Intel i5
Asus rogx GTX 970
8 GB ram DDR 3
2 SSD 500 GB 2 HDD 1 TB 1 External 4 TB
Bios support UEFI and fast boot. My mainboard is gigabyte but not remember spec it was h7 or something like and really old one (over 8 years)
I have dual screen and when crashes only 1 screen shows something other is closed.
Anyway for log where to crash when open? Or any way to understand why crashes. I'm not a newbie but not an expert. I used ubuntu from 7 until 10 version and gone to mac. But need this computer for work

This is screen photo. 

 [http://imgur.com/a/x9eSG](http://imgur.com/a/x9eSG)

[IMG]http://imgur.com/a/x9eSG[/IMG]

---

### Post by ubfan1 on 2017-05-02
At the grub menu screen, (assuming a UEFI boot without the function keys to change options), try typing "e" to edit and add "nomodeset" on the "linux" line at the "quiet splash".  If that works, add the proprietary Nvidia drivers right away:  Software updater, let it update, click on the settings button, then the alternative drivers tab.

---

### Post by mythicpaw on 2017-05-08
Hello,

Thx for info. Installation screen has come and trying install. After completed I will write here results.

---

### Post by mythicpaw on 2017-05-08
Hello Again, Grub said my harddisk dont have boot option. I did 2 partition. First - 498 gb as a root second is 2 gb temp. I also have windows too. That has uefi fast boot and another disk (ssd) and that is master. Soo grub 2 crashed and interrupted installation

---

### Post by ubfan1 on 2017-05-08
With an old system, check for any BIOS updates available from the vendor.  UEFI was just getting started then and many vendors didn't handle it correctly on their first attempt.
Run boot-repair without selecting any repairs, just the report, and post the link here.  That should give us enough information to help you.  Until the report is posted, I'll guess that the Ubuntu bootloaders actually got loaded onto the first disk (Windows, in UEFI), so if you are actually trying to boot the second disk directly, it has no bootloaders.  If you didn't even put a 300M EFI FAT32 partition on the second disk, it definitely doesn't have any bootloaders without a partition in which to put them.

---

### Post by mythicpaw on 2017-05-10
Hello again;

I installed. for Uefi problem I deleted a previus installed OS on master disk and put ubuntu there. Then I installed 2nd os on other disk. I will install grub again.

Ubuntu working fine thx all for response I will close thread.

---

