---
title: "Install without bootable CD-ROM"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by jwhiteman on 2007-04-09
I have some older computers I would like to install XUbuntu on, although they have CD-Rom drives, they are not bootable. Is there a HOW-TO or anything that will explain how to do this?

---

### Post by UNITI&#1048;U on 2007-04-09
> **jwhiteman said:**
> although they have CD-Rom drives, they are not bootable.

I'm sorry that doesn't make sense.  Any CD-ROM drive is bootable.  You just have to set in your BIOS for the CD-ROM to be used in the boot sequence.

---

### Post by jwhiteman on 2007-04-09
Sorry,

Not all CD-ROMS are bootable.  THe bios on the machine is older, the cd-rom is older and it is not possible to boot from CD-ROM.

The only options are HDD and FDD.

---

### Post by UNITI&#1048;U on 2007-04-10
> **jwhiteman said:**
> Sorry,

Not all CD-ROMS are bootable.

That's utter nonsense.  I have a CD-ROM drive that is at least 15 years old and I can boot from it just fine in my machine.

> **jwhiteman said:**
> 
THe bios on the machine is older, the cd-rom is older and it is not possible to boot from CD-ROM.

The only options are HDD and FDD.

Then that's a problem with your bios not the CD-ROM drive.  Take that old CD-ROM drive and put it in your newer machine and you can see how you're wrong.

---

### Post by az on 2007-04-10
> **UNITI&#1048 said:**
> That's utter nonsense.  I have a CD-ROM drive that is at least 15 years old and I can boot from it just fine in my machine.


Then that's a problem with your bios not the CD-ROM drive.  Take that old CD-ROM drive and put it in your newer machine and you can see how you're wrong.

Your tone sucks.  Be respectful.

The fact that the BIOS is responsible for the box not booting from the cdrom is completely irrelevant to most people.  If you want to be helpful, explain that instead of being rude.

jwhiteman:

On the install disk, there is an /install folder which contains sbm.  Read the README.  Basically, you write smb to a floppy and then boot it.  SMB will load into memory and probe your hardware.  You will be offered a menu and a way of booting the devices it finds.

It may take a few monutes to probe your hardware - it is obtuse, since the screen is black duting this time and it makes you think your machine is crashed.

Also, to boot the selected device, you need to go into the menu and select "boot it".  I forget what keys to press to enter the menu...

Anyway, that's how you do it.

---

### Post by UNITI&#1048;U on 2007-04-14
> **az said:**
> The fact that the BIOS is responsible for the box not booting from the cdrom is completely irrelevant to most people.  If you want to be helpful, explain that instead of being rude.

That's fine but its completely irrelevant since his claim was that an older CDROM drive was unbootable which is complete nonsense.  Sorry, but when someone makes nonsense claims and when they are pointed out to be wrong and yet the person continues to repeat the false claims, they have to be called out on it.

---

### Post by frankos44 on 2007-05-16
Now now boys... we are all on a learning curve and we are all guilty of making assumptions based open our own experience. It depends on your interpretation of a "bootable CD". Is it a CD that you have managed to boot by some means or another or a BIOS that supports booting a CD or a CD that is capable of being booted?

---

### Post by ginestre on 2007-05-16
I had the same problem, and had this useful (as well as courteous!!! ) reply

[http://ubuntuforums.org/showthread.php?t=438153](http://ubuntuforums.org/showthread.php?t=438153)

Good luck.

---

### Post by Wim Sturkenboom on 2007-05-16
If my memory is correct:

There were times that the CD-rom was connected to the audio card. You needed a special bootfloppy to be able to access te CD-rom and could continue from there.

---

