---
title: "Replaced parts and now I cant install Ubuntu!!"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by Slimo on 2007-12-16
I used to run Ubuntu 7.10 without any problems, then I installed a new motherboard (ASUS P5GC-MX), new CPU (Intel Core 2 Duo 2.2GHz), new RAM (Silicon 1Gb DDR2-667)  and a new GeForce 8600 GT graphics card.

I formatted my 250Gb hard drive and booted with the Ubuntu live cd in the drive.  The BIOS detected all the components.  The live cd menu loaded, but then whatever I tried (install, install in safe mode, check cd for defects) took me to busybox, where a whole lot of text came down:

[ 676.593602] ata1.00: exception Emask 0x0 SAct 0x0SErr 0x0 action 0x2 frozen
[ 676.593648] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x12 data 4096 in

etc

Can anyone explain what is going on here?  I am sure I installed all the new parts correctly as the BIOS detects everything.

Incidentally, I tried installing Windows XP as well and it installed from the cd, but then when you have to restart and take the cd out, I got a screen saying "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

I have checked in the BIOS and the 1st boot device is the hard drive.

PLEASE HELP!!!

---

### Post by Pumalite on 2007-12-16
What is the chipset of your Asus motherboard?. Could you post a link to your motherboard?

---

### Post by Slimo on 2007-12-16
According to the manual specifications, the chipset is:

Northbridge: Intel 945GC
Southbridge: Intel ICH7

Here is the link:

[http://www.asus.com/products.aspx?l1=3&l2=11&l3=498&l4=0&model=1574&modelmenu=2](http://www.asus.com/products.aspx?l1=3&l2=11&l3=498&l4=0&model=1574&modelmenu=2)

Thanks!

---

### Post by Pumalite on 2007-12-16
Your motherboard is fine. Give me the specs of your drives and life history of them.

---

### Post by kajillin on 2007-12-16
umm shouldnt your first boot be your cd-drive then hdd? maybe try the text based installer? and just for shits-n-giggles make sure all the connections are tight, cuz u never know. And did you make sure you were static free, cuz ive fried more than a few hdd by mistake myself.

---

### Post by Slimo on 2007-12-16
I have a single Seagate 250Gb drive (if you need more detailed specs it will have to wait a few hours until I'm home :-)

In the past I have used both Windows XP and Ubuntu (Edgy to Gutsy) on the hard drive.  After I installed my new hardware I formatted the drive after it wouldn't boot.  I have had it about 2 years, haven't had any problems up until now.

Hope this helps.

---

### Post by kajillin on 2007-12-16
well google did a study and they said the average lifespan of a hdd is two years, so maybe u should get one of them to. or go spend ten bucks on an old one and see if it works then youll know if its your harddrive or your hardware.

---

### Post by Slimo on 2007-12-16
Thanks for the advice.  I will have a play around with boot order when I get home - have tried a few variations but doesn't hurt to try again (with a plan this time, lol).

Should be able to test the hard drive using my external USB case in another comp.

---

### Post by Pumalite on 2007-12-16
You can test your hard drive with TestDisk:[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

