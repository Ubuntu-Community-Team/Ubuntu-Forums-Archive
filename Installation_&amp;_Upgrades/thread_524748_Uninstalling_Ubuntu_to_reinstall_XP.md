---
title: "Uninstalling Ubuntu to reinstall XP"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by bertfallen on 2007-08-13
Okay, I've had enough of Ubuntu to be fair. And would like to go back to XP, I didn't dual boot, and I have the XP disc, but when I restart my computer and hold the F8 key to get the options to load from other drives, it just by passes it and carries on loading Ubuntu.

I installed Ubuntu Studio previously, before doing that I never got this problem,so I think it has something to do with that. Anyway, I also cant get into Bios. I need help, how do I completely reformat everything so I can just install XP, or uninstall Studio so I can try and load from a different drive...

---

### Post by dabl on 2007-08-13
Holding down the F8 key is a Windows thing -- if you don't have Windows installed, holding the F8 key won't do anything.

Does your Windows CD not boot, when it is in the CD ROM drive?  How did you install Ubuntu if your CD ROM drive doesn't boot a bootable CD?

When the computer is first powered on, do you not get an indication of how to enter BIOS (aka "Setup", sometimes)?  What kind of PC is this -- you should be able to Google the make and model, and find out what the BIOS entry key-press is.  :)

---

### Post by bulldog on 2007-08-13
Well,if you can't get into the BIOS,you have a problem for sure.
If you have a floppy drive you can try to make a bootable floppy on another machine,put fdisk on it and try if you can boot into it.
Remove all the linux partitions and ubuntu is gone,but GRUB will still be in the MBR of the hdd.

But the problem persist,you need to set 'boot from cd-rom first' before you can install windows again.
There should be a way to clear your BIOS by short cutting some pins on the motherboard,see your manual for instructions.
Maybe you get in your BIOS again,which is important to reinstall windows.
Another way which you can try is to put your machine off and disconnect the power for a few minutes and try again if you can get into the BIOS.

---

### Post by bertfallen on 2007-08-13
> **dabl said:**
> Holding down the F8 key is a Windows thing -- if you don't have Windows installed, holding the F8 key won't do anything.

Does your Windows CD not boot, when it is in the CD ROM drive?  How did you install Ubuntu if your CD ROM drive doesn't boot a bootable CD?

When the computer is first powered on, do you not get an indication of how to enter BIOS (aka "Setup", sometimes)?  What kind of PC is this -- you should be able to Google the make and model, and find out what the BIOS entry key-press is.  :)

I'm sure I got it too work once while Ubuntu was installed.

When I put the disc in the CD it opens it up but just shows me all the files nothing else. And the setup file is an EXE so I cant run it.

Yes, It says 'Hold F2 to enter Bios, or F12 to network boot' And I held F2 but it just carried on loading Ubuntu, also when it loads the GRUB it says Pres 'Esc' To enter Setup, and I did that once, but it didn't do anything just carried on...

> **bulldog said:**
> Well,if you can't get into the BIOS,you have a problem for sure.
If you have a floppy drive you can try to make a bootable floppy on another machine,put fdisk on it and try if you can boot into it.
Remove all the linux partitions and ubuntu is gone,but GRUB will still be in the MBR of the hdd.

But the problem persist,you need to set 'boot from cd-rom first' before you can install windows again.
There should be a way to clear your BIOS by short cutting some pins on the motherboard,see your manual for instructions.
Maybe you get in your BIOS again,which is important to reinstall windows.
Another way which you can try is to put your machine off and disconnect the power for a few minutes and try again if you can get into the BIOS.

If its a problem with the HDD I have two more I can use to replace it.

---

### Post by bulldog on 2007-08-13
> **bertfallen said:**
> I'm sure I got it too work once while Ubuntu was installed.

When I put the disc in the CD it opens it up but just shows me all the files nothing else. And the setup file is an EXE so I cant run it.

Yes, It says 'Hold F2 to enter Bios, or F12 to network boot' And I held F2 but it just carried on loading Ubuntu, also when it loads the GRUB it says Pres 'Esc' To enter Setup, and I did that once, but it didn't do anything just carried on...



If its a problem with the HDD I have two more I can use to replace it.

It's not the hdd,I think you push the F2 too late!
Power on the machine and tap several times on the F2 till you see the BIOS.

---

### Post by bertfallen on 2007-08-13
> **bulldog said:**
> It's not the hdd,I think you push the F2 too late!
Power on the machine and tap several times on the F2 till you see the BIOS.

Nope, just tried did the same thing.

---

### Post by dabl on 2007-08-13
It acts like that keyboard isn't connected, or something is haywire in the BIOS (which Ubuntu certainly did not change).  Do the keyboard lights flash when you power it on? If the BIOS were set to boot from the CD ROM drive first (which apparently it is not), then any bootable CD (Windows, Linux, whatever) should boot, and it should not be going to the hard drive boot sector.  Showing you the files on the Win XP CD is not "booting" -- it's just "viewing" or "opening".  So something is very wrong with the hardware setup on that PC, and those wrong settings are irrelevant to what operating system it MIGHT boot if it would boot from the CD.  That's my two cents' worth.

As a previous poster said, if you know the make and model of the PC, then you can Google the manufacturer and learn the motherboard model.  Once you know the motherboard model, you can go to that manufacturer and find where the jumper is located, that will let you restore the factory defaults in BIOS.  I think that's what you're probably going to have to do, since the keyboard doesn't seem to function during the boot sequence.  :(

---

