---
title: "Getting rid of GRUB post-uninstall?"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by DaveNF2G on 2006-08-26
Because I know about 1% more about Linux than a friend of mine does, he asked me to figure out how to put his computer back to Windows.  

Unfortunately, he used a Windows boot floppy to reformat the hard drive where Linux was installed, then he didn't know what to do next.  The computer no longer has a non-DOS partition (come to think of it, he must have run fdisk also), so Linux is completely gone.

When attempting to boot the computer from the hard drive, GRUB still attempts to take control.  I'm not sure how GRUB is even still present!  I see these messages after the BIOS loads:

GRUB Loading stage1.5..

GRUB Loading, please wait...
Error 17

Then the computer freezes.  I don't see any options in the BIOS setup for specifying a boot loader, so how do I "turn off" GRUB without have Linux available on the machine in the first place?  I can't install Windows until I can boot the machine.

](*,)

---

### Post by Tomosaur on 2006-08-26
Grub installs itself to the MBR. You can stop Grub showing up by allowing windows to fix the MBR, and for this you will need the recovery CD. All you need to do is boot from the recovery CD and type 'FIXMBR', and hey presto, Grub go bye bye. If you don't have a recovery CD, you may be able to find something on the internet to fix the MBR, but I'm not personally aware of anything specific.

Also, if you insert a Windows installation CD, the pc should use that to boot rather than the hard drive. If this fails, try getting into the BIOS during startup and set the CD drive to boot first - pop in the cd, save, and reboot. The windows installer should come up.

---

### Post by DaveNF2G on 2006-08-26
Unfortunately, I can't boot from a CD until I install CD drivers, which I can't do because I can't get past GRUB.

The boot order is set for CD, Floppy, HD already, but it makes no difference.  GRUB gets in the way no matter what order I attempt.

---

### Post by DaveNF2G on 2006-08-26
OK, I got it.

First, the floppy drive was not seated properly, so the computer wasn't even seeing it.  Once I fixed that, I could boot from a rescue floppy without interference from GRUB.

Then, I was able to perform fdisk /mbr and that took GRUB right out of the picture!

Thanks for the assist.  You got me pointed in the right direction.

---

