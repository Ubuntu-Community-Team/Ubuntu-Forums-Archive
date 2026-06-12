---
title: "need to uninstall grub...Dual Boot using XP Bootloader"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by ganja_guru on 2005-06-26
Hi guys,

i have windows xp installed on a sata raid-0 and ubuntu installed on an IDE drive...i need to setup a dual boot scenario using the XP bootloader..this guide tells me how to do it

[http://www.linuxsolved.com/forums/ftopic125.html](http://www.linuxsolved.com/forums/ftopic125.html)


what i basically need to do is uninstall grub from the MBR and install it to a root superblock...i only have experience with lilo and that doesnt seem to work for me..so how do i ...


1) uninstall grub from mbr of /dev/hda
2) install it to a /boot 


p.s - does /boot *have* to be in a seperate partition or is it ok if its a folder in / ?

---

### Post by mrcbrown on 2005-06-26
[QUOTE=ganja_guru]Hi guys,

i have windows xp installed on a sata raid-0 and ubuntu installed on an IDE drive...i need to setup a dual boot scenario using the XP bootloader..this guide tells me how to do it

[http://www.linuxsolved.com/forums/ftopic125.html](http://www.linuxsolved.com/forums/ftopic125.html)


what i basically need to do is uninstall grub from the MBR and install it to a root superblock...i only have experience with lilo and that doesnt seem to work for me..so how do i ...


1) uninstall grub from mbr of /dev/hda
2) install it to a /boot 


p.s - does /boot *have* to be in a seperate partition or is it ok if its a folder in / ?[/QUOTE]
 Why not just use grub to load XP? That's how I personally have always done it, but for a friend one he was building a XP box for a client, but they wanted to 'play around' with Linux, so we installed XP first, and then skipped the boot loader install on Fedora.

As for /boot - it just needs to exsist, my master partition is just my drive, 200GB of goodness which includes /boot - so it doesnt HAVE to be it's own gig - but a lot of linux tutorials suggest it.

---

### Post by ganja_guru on 2005-06-26
thanks for the reply..yeah thats a problem cause i cannot use grub/lilo since my windows is on a raid0 sata drive...and i DO NOT want to mess with that drive..thats why i need to know how to install grub to the superblock, so i can copy the .lnx file to windows and include it in boot.ini as said by the guide..

---

### Post by irusun on 2005-06-26
You cannot "uninstall" grub from the mbr - you can only write over it with another boot loader (in this case, the Windows one).

Not sure about the "superblock" terminology, but I'm guessing this is what you want to do...

To install grub on a partition (rather than to the mbr), it's best to use a grub boot disk/cd.  After booting the grub disk, at the command line, you can do the following:

First, find the partition that actually holds grub files,.  Grub may be in the /boot directory or it may be on its own partition:

grub> find /boot/grub/stage1
or
grub> find /grub/stage1

Next, set the GRUB's root device to the boot directory of the OS (for example /boot in Linux).  GRUB’s root device is the partition that the GRUB files are located (usually on the boot partition).

For example, if the GRUB files are located on your first logical partition, then:

Example:
grub> root (hd0,4)

Once you've set the root device correctly, run the command "setup".  To install GRUB into the "boot sector" of a partition instead of the MBR, specify a partition into which you want to install GRUB (which would generally be the /boot partition).

Example:
grub> setup (hd0,4)

Then, use a windows boot disk/cd to reinstall the windows mbr.

EDIT: changed "setup" section to reflect mingus' advice below...

---

### Post by mingus on 2005-06-26
A caution . . . there is a common error that occurs when installing grub if there is a separate partition for /boot (sometimes this is necessary).

Grub is installed by writing a copy of its stage1 program to a boot sector, which is what you are going to copy to Windows.  When this stage1 file is written, it is given a pointer to find its stage2.  Stage1 is not the loader itself, it just calls the loader pgm stage2.

The error occurs when the wrong path is given for stage2, which prevents stage1 from finding it.  This can happen in more than one way:  Example:  /boot is on hda1 and / is on hda2 and you do:

#grub
grub> find /boot/grub/stage1
hd0,1
grub> root (hd0,1)

Grub cannot read the BIOS table, so it does not know that /boot is separate.  It returns hd0,1 because it is using the filesystem for the find, and /boot is hung off of /.  So it thinks the boot files are on hd0,1 when in reality they are on hd0,0.  

When you install with the setup command, regardless where, grub will see the installation files but will use the wrong pointer (that is, it will use what you told it to, which was wrong).  When you boot, grub will freeze.

Also, since you are chain-loading from W$, install the loader on the same partition that /boot is physically on.

---

### Post by ganja_guru on 2005-06-26
thank you very much for the quick replies!..will try it out and get back to you

---

### Post by mingus on 2005-06-27
I prob should have included in my post above that the same error can occur using the script grub-install because it assumes the image files are under / . . . the solution is to add a pointer to /boot, for example like so if to the MBR . . .
#sudo grub-install --root-directory=/boot /dev/hda

---

### Post by ganja_guru on 2005-06-28
its working fine now..thanks everyone!

---

