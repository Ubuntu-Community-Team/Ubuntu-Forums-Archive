---
title: "Ubuntu won't boot, ACPI problem"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by Zhor on 2007-07-27
I have installed Kubuntu Feisty using the Wubi installer (which uses the alternate ISO) on my work supplied laptop (I still need to use ACAD LT 2008 or I could work in Kubuntu only!)  I have enjoyed it so much I decided to attempt to install it on a pc at home.  It is an older self built computer running Windows XP without issues:

ECS K7AMA BIOS version: 062710 08/12/2002
AMD ATHLON XP 1700+
1 GIG DDR1 RAM (FSB 266)
GeForce4 TI4200

It installs fine, but on the first boot I get this:


[      0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI

and it hangs and won't continue.
I have done much googling and have tried adding

acpi=force apm=off

to the Grub boot menu.lst file after the first kernel entry

kernel /wubi/boot/linux find=/wubi/boot/lunix setup_iso=kubuntu-7.04-alternate-i386.iso quiet splash ro

and I still get the same error.  Anybody have any other ideas?

---

### Post by yaddoshi on 2007-07-28
Have you tried adding acpi=off and pci=noacpi yet?

---

### Post by Zhor on 2007-07-28
Thanks for the response.  I hadn't tried acpi=off yet; I had tried turning off the acpi in bios but it just gave me more errors.  When I try acpi=off pci=noacpi it hangs before I get to any errors.   I get a blinking cursor.  The visible lines are:

  Booting 'Ubuntu'


(hd0,0)
Filesystem type is ntfs, partition type 0x7
  [Linux-bzImage, setup0x1c00, size0x1a82cc]
  [Linux-initrd @ 0x1f85e000, 0x7918a5 bytes]

_

The underline represents the location of the blinking cursor.  The system is unresponsive.

I tried acpi=off pci=noacpi with these bios options: APM, APM/ACPI, ACPI, and DISABLED.  All have the same result.

---

### Post by rillip on 2007-07-29
when I have worked on pci issues in the past I use the form

noacpi acpi=off

Don't know if this will help or not though, haven't run in to this exact error

---

### Post by pcmanlin on 2007-07-29
i think there is some problem in grub for linux, but it results from the problem of bios. the code of bios used bigger space than most situation, but grub used some of space allocated to bios, so it crashed.

try another bootloader, such as grub 4 dos.

if you like, i can offer you a testing cd iso(just < 10m) for testing. 
in the cd, i used the grub i modified to boot, maybe you can use it to reinstall your grub.

---

### Post by Zhor on 2007-07-29
rillip: I tried noacpi acpi=off and I get the origional error plus

[    22.569267] PCI: Fatal: No config space access function found'Loading, please wait...
no block devices found
_

pcmanlin:  I would like to give your iso a try.

---

### Post by CutterXYZ on 2007-07-29
I have the same error message on two old computers, but it doesn't prevent Ubuntu from booting on them. It displays the message and boots anyway.

---

### Post by Zhor on 2007-07-29
Sorry, tried it again and got it to do something:

[    22.569267] PCI: Fatal: No config space access function found'Loading, please wait...
no block devices found
                 Check root= bootarg cat /proc/cmdline
                 or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

'help' gives me:

Built-in commands:
----------------------
. : alias bg bread cd chdir command continue echo eval exec exit export false fg getopts hash help jobs kill let local pwd read readonly return set shift times trap true type ulimit umask unalias unset wait [ [[ ash basename busybox catg chmod chroot chvt clear cmp cp cut deallocvt dumpkmap echo egrep env expr false fbset fdflush fgrep grep hostname ifconfig ip kill ln loadfont loadkmap ls mkdir mkfifo mknod mkswap mktemp more mount mv openvt printf ps pwd readlink reset rm rmdir sed setkeycodes sh sleep sort stat sync tail tee test touch tr true tty umount uname uniq yes


(initramfs) _

I have had experience replacing xorg.conf after messing around trying to get my ATI X1600 Mobility working on my laptop, but I'm not sure what to do here.

Anything to get Ubuntu on more of my computers!  :)

---

### Post by Pumalite on 2007-07-30
This is a Smosgarbord of fixes that I've picked up here and there. See if one fits you and apply it. What do you have to loose?

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

### Post by Zhor on 2007-08-01
I tried modprobe piix command.  Result follows:

/bin/sh: cant access tty; job control turned off
(initramfs)modprobe piix
(initramfs)exit
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!


Busybox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

I also tried installing direct from the alternate iso.  It halted after the origional error:

[ 0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI

That's the only line showing.  I'm going to do some experimenting with Grub for DOS and also the live cd, as I've only been using the alternate.

---

### Post by Ken McCoy on 2008-01-02
I had the same problem - eventually I solved it by using the alternate installation CD of Gutsy Gibbon 7.10 with the nodma parameter. It also refuse to read the hdb - a protected partition installed by the Compaq rescue CD used to back up files/system. I think the nodma parameter might have had something to do with fixing that. 

Compaq Presario 5700 series
Pentium II 450MHz
356MB RAM
Iomega ZIP disk drive
floppy
cd-burner

Cheers! ken

---

### Post by Zhor on 2008-01-04
Thanks Ken.  I should have posted my solution earlier.  I just rummaged around and used a different motherboard.  The funny thing is I think it was an older MB, installed and boots with no problems.  I guess sometimes hardware is just not compatible.  Thanks for all the responses!

---

