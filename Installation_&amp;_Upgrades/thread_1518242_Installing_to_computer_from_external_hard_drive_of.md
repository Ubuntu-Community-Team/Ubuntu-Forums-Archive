---
title: "Installing to computer from external hard drive of 500G"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by .D_D. on 2010-06-26
Hallo.
Following difficulties installing ubuntu from a CD, I've decided to install from USB. The aim is to dual boot my coputer with windows vista, but the CD won't load properly for some reason or another, so would it be possible to use a 500 gigabyte external hard drive to install it, while leaving the stuff I have on the hard drive on there?
Thanks y'all.

---

### Post by alambpencil on 2010-06-26
I would just go for using a usb thumb drive and save the hassle.

---

### Post by tommcd on 2010-06-26
> **.D_D. said:**
> Hallo.
Following difficulties installing ubuntu from a CD, I've decided to install from USB. The aim is to dual boot my coputer with windows vista, but the CD won't load properly for some reason or another ...
How did you burn the CD? Did you burn the CD at the slowest possible speed?
Did you run the "check disc for defects" option when you boot the CD?
Is your computer's BIOS set to boot from the cdrom drive as the first boot device?
What specific problems are are you having when trying to boot off of and install from the live CD?

Installing from the live CD is the easiest option. If you can burn a good CD this would be the way to go.

---

### Post by varunendra on 2010-06-26
> **.D_D. said:**
> Hallo.
Following difficulties installing ubuntu from a CD, I've decided to install from USB. The aim is to dual boot my coputer with windows vista, but the CD won't load properly for some reason or another, so would it be possible to use a 500 gigabyte external hard drive to install it, while leaving the stuff I have on the hard drive on there?
Thanks y'all.
The most convenient & promising suggestion:
> **tommcd said:**
> Installing from the live CD is the easiest option. If you can burn a good CD this would be the way to go.


The next safest, convenient & really advisable solution is:
> **alambpencil said:**
> I would just go for using a usb thumb drive  and save the hassle.


Now if you're having some really weird problem with cd install, you don't have a thumb drive, nor can you borrow one from someone  for half an hour, then YES, YOU CAN install using the external HDD  while keeping all the stuff intact!

Just create a 700MB or more FAT or FAT32 primary partition on the  external HDD (or empty an existing one- formatting it with FAT/FAT32  filesystem), boot with live cd & goto  system>administration>startup disk creator and make the external  HDD a live USB disk selecting the FAT/FAT32 partition as the  destination.
**[[COLOR=Red]WARNING:[/COLOR] Selecting a non-FAT partition as  destination will wipe out all the partitions on the Hard-disk!!]**

[COLOR=Red]**Be Cautious!**[/COLOR] You must empty &  dedicate a primary partition on the external HDD to setup files. So if  you don't already have it, then you'll need to resize existing one to  create room for the dedicated one; and that kind of operation  (resizing-moving partitions) always involves some level of risk of  losing data!
Therefore if you do it, be extremely careful!


Post here if you need detailed guidance. I'll be happy to help, but  again, get a thumb drive if you can!8-)

---

### Post by .D_D. on 2010-06-26
Why thank you, I should be able to use a pen drive, I imagine someone will have one....
The problem with the CD (it was burned at the slowest speed, yes, etc), is that once the BIOS is set to boot the computer from CD, and it tries, the screen just shows what looks like a sheet of paper and a person in a circle (I have no idea) at the bottom, and consistently whirrs for hours on end... Pressing buttons just produces beeping...
Anyhoo, finding a pen drive sounds like the simplest option, so i'll try that as soon as I can find one, thanks y'all.

---

### Post by varunendra on 2010-06-26
> **.D_D. said:**
> The problem with the CD (it was burned at the slowest speed, yes, etc), is that once the BIOS is set to boot the computer from CD, and it tries, the screen just shows what looks like a sheet of paper and a person in a circle (I have no idea) at the bottom, and consistently whirrs for hours on end... Pressing buttons just produces beeping...
Anyhoo, finding a pen drive sounds like the simplest option, so i'll try that as soon as I can find one, thanks y'all.

You're welcome!
By the way, try press & holding shift key while the computer is booting from cd. See if it brings up any options.

---

