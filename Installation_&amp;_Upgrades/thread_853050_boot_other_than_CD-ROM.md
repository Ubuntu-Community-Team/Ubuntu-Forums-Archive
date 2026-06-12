---
title: "boot other than CD-ROM"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by forumjanus on 2008-07-08
Hi
My parents' PC runs XP and I want to install Xubuntu to see if it can run faster.
I have downloaded an Xubuntu ISO image and verified that it has no errors. I have tried to burn it 10 times on a CD but it keeps failing.
So now I want to boot from somewhere else than the DVD/CD-ROM.
How can I do that?

My setup boot order looks like this:
1. Removable Device [Disabled]
2. ATAPI CD-ROM [ASUS CRW-5232AS]
3. Other Boot Device [Onboard ATA100 Boot Device/SCSI]
4. IDE Hard Drive [IBM-DTLA-307030]

For "1. Removable Device" I can choose between Leagacy Floppy, LS-120, ZIP, ATAPI MO, USB FDD, USB ZIP.


The PC specifications is as follows:

Mainboard: ASUS A7V
Chipset: VIA KT133
Processor: AMD Athlon @ 800MHz
Physical Memory: 384MB (3 x 128 SDRAM)
OS: Microsoft Windows XP Professional 5.01.2600

I have tried to boot to the Recovery Console and run "diskpart /add \Device\HardDisk0 800" but it says it cannot partition the disk.
The point was to make a small partition and put the ISO image on there and then boot up from that, but I don't know if that is possible.

Any help would be appreciated.
Thank you

---

### Post by timcredible on 2008-07-08
you can get a free xubuntu cd if your cd burner doesn't work - it's on this site.

---

### Post by avtolle on 2008-07-08
Take a look at [https://help.ubuntu.com/community/Installation/#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation/#Installation%20without%20a%20CD) which will give you a few options to consider.

---

### Post by forumjanus on 2008-07-12
> **avtolle said:**
> Take a look at [https://help.ubuntu.com/community/Installation/#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation/#Installation%20without%20a%20CD) which will give you a few options to consider.

Thank you for the reply. 
I tried UNetbootin with which I put the xubuntu image on my USB pendrive but it stopped at 4%. I didn't have time to try again, but I'll try again next time we visit my parents. I hope it works then, I'll let you know.

---

