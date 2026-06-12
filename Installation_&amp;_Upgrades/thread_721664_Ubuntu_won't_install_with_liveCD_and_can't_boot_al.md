---
title: "Ubuntu won't install with liveCD and can't boot alternative CD"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by fox.esq on 2008-03-11
First, I've tried loading Ubuntu 7.10 with the liveCD.  The menu appears and I'm able to select install, it will then go into the next screen where you see the Ubuntu name and logo and that orange bar will bounce back and forth, then going into some kind of loading.  When it is done loading it will pop into another screen that's blank except for a blinking cursor.  After a couple of seconds later the screen will go black and my monitor will state 'no signal'.  From there, even after waiting for an hour, there will still be no signal and I'll have to reset the computer.

I've tried a few different methods suggested in this forum including starting in safe mode which is not helpful.

I've also downloaded the alternate CD installer.  Problem is, when I try to boot from it, the CD won't be recognized and will request a proper booting media.  Is there a trick not clearly mentioned to burning the alternate CD; I had no problems with getting the liveCD to burn and work up to the point mentioned above?

I intend to install Ubuntu on a separate internal hard drive that is currently blank. My #1 hard drive is dedicated to Windows XP home, #2 I would like dedicated to Ubuntu 7.10. (But this stuff isn't an issue yet because I haven't been able to get this far, but perhaps it's worth preemptory advice).

Here are the specs on my computer:

P5W DH Deluxe Asus Motherboard.
4x1Gig PC6200 DDR2-800 RAM OCZ brand
Intel Core2Duo E6600 Processor
2 Western Digital WD1600YS 160GB 3.0 Gb/s 16 MB Cache 7200 RPM SATA Hard Drives
ATI X1650 PRO 512MB DDR2 PCI Express Video Card w/DVI, VGA & TV-Out (HIS brand)
Acer AL1916W LCD 19" monitor
and an ancient IDE HP CDROM writer from 1999 (my newer DVD-RW died while trying to burn this stuff, but I used a new DVD-ROM CD-RW to burn the alternative CD installer)

The 2 hard drives are connected via the Intel ICH7R SATA1 and SATA3 connectors, and the CD drive is connected via the Intel ICH7R IDE connector.

I'm not savvy with Linux technical terms so please keep responses intelligible to lay persons.

THANKS FOR YOUR HELP!!!

---

### Post by Pumalite on 2008-03-11
Installing with the Alternate CD is a good idea. You probably have a bad burn. Try burning a new CD after doing md5sum on your iso, burning at 4x or less, in CD-R, checking CD integrity after burn and before install.

---

### Post by Bonanzaman on 2008-03-11
OK, I am experiencing pretty much the same issue... sent PM to PUMALITE, he suggested trying the Alternate CD, md5sum check, slow burn, integrity check, all of which I performed
and ran the drill....no errors....tried text install.....getting return now:

[ 53.911537] ata1.00:cmd C8/00:08:00:00:00:..........eo tag 0cdb 0X0 data 4096 in

.......repeats with first number changes.

(The new disc boots perfectly on my work machine, like the others); I am churning out lots of nice plastic coasters!

Not sure where to go from here???

---

### Post by Pumalite on 2008-03-11
Here is a guide and a collection of boot parameters to try, alone or in combinations:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
First try the most common ones:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791

---

### Post by Bonanzaman on 2008-03-11
Thanks, Puma....1st 3 boot param changes and the install finally kicked off! We're gonna have some more challenges, I'm sure....but progress is good!

---

### Post by Pumalite on 2008-03-11
You are welcome. Good luck.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by fox.esq on 2008-03-11
What does the md5sum on the iso do and how do I do it?  Also, I'm using the Infrarecord program: is there a particular way to setup the burn?

---

### Post by Pumalite on 2008-03-11
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by fox.esq on 2008-03-11
Ok, the md5sum checks out; the hash comparisons match.  I think my CD-RWs may be messed up instead of my burner.  I'm going to have to go buy some.  I'll get back to you tomorrow.  Thanks for you help!

---

### Post by Pumalite on 2008-03-12
OK. Good luck.

---

### Post by fox.esq on 2008-03-12
Ok, I've tried 2 different CD burners at 4X with 4 different fresh, brand-new CD-R, My computer won't boot from the alternate CD.  Something is fundamentally wrong with the program!  It must be missing some kind of boot prompt or command.  Ubuntu 7.10-alternate-i386.iso doesn't work!  All the hash checks I do, even checking the CD, match the one listed on the site.

I noticed on the LiveCD file there are a couple of .exe programs, one that's called cdboot.  These .exe and .inf files are missing on the alternate CD.  Maybe that has something to do with the problem.

---

### Post by Pumalite on 2008-03-12
You probably have some hardware incompatibility. Did you try the boot parameters that I suggested some posts back?

---

### Post by fox.esq on 2008-03-12
I did not realize that was intended for me.  However, that stuff doesn't make any sense to me.  Also, are you talking about the alternate cd or the LiveCD?  The problem I'm having with the alternate cd is that my bios is just not recognizing it as a bootable media, whereas the livecd was recognized.  In lay person terms, how should I employ the boot parameters? I have no idea where to begin and what hardware could be the cause of the hang-up.

---

### Post by Pumalite on 2008-03-12
If your BIOS is not recognizing your Alternate CD as a bootable media, then you have a bad burn. Do md5sum on Alternate iso, burn at 4x or less, on CD-R, check CD integrity after burn and before install. Make sure you bur it as 'image' and not as 'data'
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

