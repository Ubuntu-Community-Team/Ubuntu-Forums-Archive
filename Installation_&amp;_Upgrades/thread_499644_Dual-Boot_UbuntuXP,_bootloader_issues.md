---
title: "Dual-Boot Ubuntu/XP, bootloader issues"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by ThreeDee912 on 2007-07-12
Just finished installing Ubuntu 7.04, using the directions from [here]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/"). I followed the directions, and clicked the "Advanced" button to change where the boot loader is put. I set it to "(hd0,1)", as the ext3 partition is the 2nd partition on the disk.

After installing, I restarted, and waited. XP booted up, and went to the login screen. No sign of Ubuntu anywhere. Did I place the boot loader in the wrong place? Or is something else wrong?

---

### Post by Pumalite on 2007-07-12
Check with this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You could also reinstall Grub following this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Herman on 2007-07-12
> After installing, I restarted, and waited. XP booted up, and went to the login screen. No sign of Ubuntu anywhere. Did I place the boot loader in the wrong place? Or is something else wrong? Yeah maybe, that installation guide is for Toshiba Laptops, which have something called an 'Express Media Player'. That has software that installs to the first track of the hard disk that might not be compatible with our GRUB boot loader. For most of us it's easier and better to simply install GRUB bootloader's IPL to MBR and boot with GRUB. 

GRUB is the world's best bootloader and it leaves NTLDR well and truly in the dust. 
GRUB is fully customizable, you can have a lot of fun and learn a lot with GRUB. See my third sig link for details.
GRUB is even better than Windows own NTLDR even for dual booting more than one Windows with, because GRUB can 'hide' one Windows partition from another. NTLDR doesn't have that functionality.
GRUB is far more flexible, GRUB understands file systems, it doesn't just rely on sector numbers to find your operating system and boot it, it can find your bootloader files even if the partition has been moved somewhere else on your disc with partitioning software.
GRUB is much better supported here in Ubuntu Web Forums, if you try to use other bootloaders you might have to wait for a long time before you get any help, but with GRUB you will probably be able to get help almost right away.

I agree with Pumalite, you should install GRUB to MBR with [Super Grub Disk]("http://geocities.com/supergrubdisk/")  or with the Ubuntu Live CD as in Catlett's how-to. 

...Unless you have a Toshiba laptop maybe...

Regards, Herman  :)

---

### Post by ThreeDee912 on 2007-07-12
The second link's instructions seemed to work. Thanks a lot.

EDIT: Nevermind. Now I'm stuck in a BusyBox terminal. :(

---

### Post by Herman on 2007-07-12
There are tow kinds of busy box terminals, which is it you have? 
[busybox or tty error]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#busybox")        /bin/sh: can't access tty; job control turned off
or
[Target filesystem doesn't have /sbin/init]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Target_filesystem_doesnt_have_")    /bin/sh: can't access tty; job control turned off?

---

### Post by Pumalite on 2007-07-12
Here is a smorgasboard of fixes (no warranties) see if they can help you:

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

---

### Post by ThreeDee912 on 2007-07-13
Woops, should be more specific. I usually ask that of other people at a OS X help forum that I usually visit.

Anyway, it's "/bin/sh: can't access tty; job control turned off"

I'll try Pumalite's suggestions now.

---

### Post by ThreeDee912 on 2007-07-13
After entering "modprobe piix" and pressing enter, it seems like nothing is happening.

---

### Post by Pumalite on 2007-07-13
Read carefully all the fixes I posted. there are several possibilities there and you are the only one that can choose depending on your hardware.

---

### Post by Pumalite on 2007-07-13
Did you type 'exit'?

---

### Post by ThreeDee912 on 2007-07-13
Typed exit, pressed enter, did nothing, probably because the prompt never re-appeared.

Thanks for the help, though. I'm probably doing something really stupid and don't even realize it.

---

