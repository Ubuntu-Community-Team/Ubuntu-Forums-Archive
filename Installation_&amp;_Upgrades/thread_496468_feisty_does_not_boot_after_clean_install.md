---
title: "feisty does not boot after clean install"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by usaar33 on 2007-07-09
I was able to install Kubuntu 7.04 fine, but upon booting up, I get the infamous 
/bin/sh: can access tty; jub control turned off (initramfs)"

error.

I have searched through this forum and the other solutions do not help.

The most disturbing part is how my /dev/disks directory is quite different than what the Live CD shows.  The installation does not have an entry for the hard drive that grub itself has been booting off of (I have two hd's - Linux is on the Master and the other drive is a bootable FAT32 with Win98).  There is a /dev/sdb1, but no sdba (and hd* are not present either).

Consequently, I can only mount my file system when I boot from the live cd.  

I have upgraded everything (and have been trying even the latest kernel).  I have also tried disabling ACPI, but to no avail.



My system is:
-MSI Motherboard (I forget the model)
-Athlon XP
-2 PATA HDs

---

### Post by Pumalite on 2007-07-09
Here is a collection of fixes; they come without warranty:

/bin/sh:can't access tty;job control turnedoff

Describe your new note here.

when I boot, the screen shows

Starting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

See if something works. Hope it helps.

---

### Post by usaar33 on 2007-07-09
Unfortunately, none did.

I just gave up and installed Dapper - and it worked without any issues.

---

