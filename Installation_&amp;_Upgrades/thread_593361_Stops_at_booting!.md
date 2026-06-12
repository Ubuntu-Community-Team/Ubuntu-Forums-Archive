---
title: "Stops at booting!"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Phentis on 2007-10-27
Hi everybody! I was trying to install ubuntu 7.10 and 7.04 and after booting intallation stops and appears the following:

[[IMG]http://i.piccy.kiev.ua/i/aa/be/351ebb8d8480bc6d5665f0255862.jpeg[/IMG]](http://piccy.info/view/12addf3aca5b095f6bd4e9bb758d87d7/)

What's the problem? I'm already trying to install ubuntu and other linux distros more than year!

---

### Post by Phentis on 2007-10-27
Still need help!

---

### Post by Phentis on 2007-10-27
up!

---

### Post by Pumalite on 2007-10-27
Post your specs and tell us what iso you are using.

---

### Post by Phentis on 2007-10-27
Using **ubuntustudio-7.10-alternate-i386.iso**

**Motherboard:** Intel iP4, D945GTPL, FSBB1066, DDR2 667*4, 4*SATA2, RAID, VGA+PCI Exp, 1394, LAN, S6.1, mATX
**CPU:** CPU iPentium-4 630 3.0 GHZ, 800 MHz, 2Mb, S775, Box
DDR-II 256Mb PC4300, 533 MHz
HDD WD Caviar 2000JB, 200GB 7200rpm, 8mb, UATA/100
DVD-RW Sony DW-Q28A, bulk
Video Radeon RX1300PRO-TD256E
PCI Express 16x
CC-IDE-Long IDE 40pin x 3/80cm flat cable


Also tried other distro's. None of them couldn't run (Mandriva, Fedora, Ubuntu 6.06, Knoppix(Ran only wih cmd "knoppix nodma")...

---

### Post by Pumalite on 2007-10-27
Is 256 MB of RAM what you have?

---

### Post by Phentis on 2007-10-27
Sorry, I didn't wire. I have 256*4 = 1024 Ram

---

### Post by Pumalite on 2007-10-27
Then you have a bad iso or a bad burn. Download new iso, do md5sum on iso, burn at 4x and try again.

---

### Post by Phentis on 2007-10-27
I tried manu burners! And I even have a original Ubuntu CD which was sent to me by mail! 

May be the problem is that I have **SATA** or **UATA/100** Hard Drive? I Also tried Wubi, but it was the same problem. But in VMWare, everything works fine...

---

### Post by Pumalite on 2007-10-27
I tend to think is your motherboard with chipset 965 with controllers MARVELL.
You need this: Motherboard Intel DG965SSK. I know that one works.

---

### Post by Phentis on 2007-10-27
Sorry, Don't understand what do you mean by saying "You need this: Motherboard Intel DG965SSK."
Do I need to change my motherboard to run Ubuntu?

---

### Post by Pumalite on 2007-10-27
You don't need to change it. Its just that Ubuntu has had problems with chipset 965. I dont know if they have corrected them in Gutsy. While, the board I mentioned, I know it works with Gutsy.

---

### Post by Phentis on 2007-10-27
What's gutsy? Is it a different distro of which I tried to install?

Sorry for such questions :)

---

### Post by Phentis on 2007-10-28
So isn't there any way to install Ubuntu or other distro on my PC??

---

### Post by Phentis on 2007-10-28
Up!

---

### Post by Pumalite on 2007-10-28
Try Ubuntu Alternate CD, download the iso from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

---

### Post by sayuki288 on 2007-10-28
why don't you just reinstall your OS again

---

### Post by Phentis on 2007-10-30
So I redownloaded Ubuntu, burned it with 4x speed, and it was the same problem... Also, the following has appeared:

[B]This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp 0000:05:01_0c Try the "8139too" driver instead.[/B]

What does it mean??

---

### Post by Phentis on 2007-10-30
Up!

---

### Post by Pumalite on 2007-10-30
Looks like incompatible motherboard.

---

### Post by gmoser on 2007-10-30
me, I would try to systematically remove variables from the equation one by one...

I had an issue booting live cd of many distros (and marked the cd's bad; when in fact it was my setup...)

Do you have onboard vga?  Remove the video card and boot.  

Then if you suspect the SATA, remove them and try an IDE disk.

One by one remove stuff and see what happens.

---

