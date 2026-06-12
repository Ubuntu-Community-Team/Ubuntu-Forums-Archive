---
title: "[SOLVED] Cant start Vista without external HD?"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by StupidMonkey on 2007-08-25
Okay, I just installed Ubuntu to my USB external hard drive, and its what im using right now. ^_^

When I shut down the computer, unplug my USB external hard drive and start my computer up, I get something like this this:

GRUB 1.5
Error 21

No idea what that means and when I search all I get is something about the live CD (but im not using the live CD).

If I start up my computer with the USB hard drive plugged in, I get to select which OS I want (a few Ubuntu and a couple Vista with (loader) next to it). Itll ask me to repair and restart, which it does and vista comes up with no problem.

How do I get vista to load up like it was before (without having to use the external hard drive)?

Thanks in advance.

---

### Post by logos34 on 2007-08-25
Grub installs by default to the MBR of Bios boot disk (hd0), even though your linux installation is on another drive.  However, the config files Grub needs are located on the linux root partition (/boot/grub/menu.lst), so when you disconnect it you get the error.

You have two options:

1. Restore the Vista boot loader to the mbr of that disk and reinstall Grub to the mbr of the linux drive.  But this means you will have to use the Bios to select your boot OS.

2. [Use Vista boot loader to chainload Grub/linux]("http://neosmart.net/wiki/display/EBCD/Linux").  (Better idea).

[Restoring Vista boot loader using EasyBCD]("http://neosmart.net/gallery/v/neosmart/EasyBCD/1_60/Bootloader+Management.png.html")

OR

On the Vista install DVD (in the "boot" folder) there is a little program called "bootsect.exe".

To restore the Vista bootloader run:
[B]
bootsect.exe /nt60 c:[/B]


for further options/info see:

bootsect.exe /help 

Then use EasyBCD to configure Vista boot loader to boot linux.

---

### Post by StupidMonkey on 2007-08-27
After using FreeBCD, I wasnt able to load up anything. Though im pretty sure that was me. =D>

The Vista DVD way worked, thanks! I dont mind using the BIOS.

-----

New problem though, I want to boot to the external HD with Ubuntu on my WindowsXP system as well, and my BIOS doesnt support it (even updated the thing).

Im guessing GRUB would be my fix? (ive read some stuff about it but would like to know if this is possible) If so, would it be possible to have it load WindowsXP by default with minimal wait (it takes long enough as it is) and have it boot my external HD when I have it plugged in? (If not, I wouldnt mind navigating to it)

---

### Post by logos34 on 2007-08-27
> **StupidMonkey said:**
> After using FreeBCD, I wasnt able to load up anything. Though im pretty sure that was me.

The Vista DVD way worked, thanks! I dont mind using the BIOS.

Ok, great.  Glad to hear that's fixed.  But didn't you try EasyBCD?  It's the best to my knowledge.

> New problem though, I want to boot to the external HD with Ubuntu on my WindowsXP system as well, and my BIOS doesnt support it (even updated the thing).

Im guessing GRUB would be my fix? (ive read some stuff about it but would like to know if this is possible) If so, would it be possible to have it load WindowsXP by default with minimal wait (it takes long enough as it is) and have it boot my external HD when I have it plugged in? (If not, I wouldnt mind navigating to it)


Well, you can't put Grub on the USB because your bios doesn't support booting usb devices, and you obviously can't have it on the XP drive unless you want a repeat of your initial problem.  There is[ this workaround--'Booting the kernel from a bootable CD'.  You'd essentially be making a USB-capable Grub Boot CD]("https://help.ubuntu.com/community/BootFromUSB?highlight=%28usb%29").  If it works, then set the cdrom first in the Bios boot order, XP disk second...when the disk is in you boot ubuntu, otherwise windows starts.  This has the virtue of leaving XP bootloader untouched.

It seems to be working for t[his person in this thread.]("http://ubuntuforums.org/showthread.php?t=527264&page=4")

---

### Post by logos34 on 2007-08-27
On second thought, you might want to first try the method described in the 'Booting via Grub'  section in that howto I gave you.  Try it with a standard Gnu Grub boot CD or floppy.  It may work as long as your system can detect, if not boot, the usb hard disk.

[http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM](http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM)

[https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28grub%29](https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28grub%29)

---

### Post by StupidMonkey on 2007-09-13
School started, lost my free time. Thanks for the links. After some trial and error, I was able to get to the Ubuntu loading screen using the bootable CD. :)

After some loading, it goes to a checklist and runs through some things. Then, I get a screen with this error:

> "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. 
Would you like to view the X server output to diagnose the problem?"

EDIT: Fixed. Thanks. :)

---

