---
title: "[SOLVED] No Network in HH and Installation Stalls at GRUB"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by sapph on 2008-06-10
Okay.  So my WinXP install dies, and I figure I'll grab that linux disc I've had and try it.  Turns out to be Ubunutu.  Installs just fine, everything seems to work ok.  Being a good little Windows lapdog, the first thing I do is check for updates.  It turns out my disc was for GG and there is a new version available, so I tell it to go ahead and upgrade to HH.

Once the upgrade finished, my network wouldn't work anymore.

In both the GG LiveCD and full installation, the NICs (I have two, each attached to a different router) were configured in 'roaming mode'.  Worked fine.  My normal configuration is either static or DHCP - my IP addresses are reserved so either one typically works.  However, after the upgrade every single packet on both NICs is being dropped.  

Attempted fixes:
Changing from 'roaming' to DHCP.  No effect.
Changing from 'roaming' to static.  No effect.
Manually changing network settings using [FONT="Fixedsys"]ifconfig[/FONT].  No effect.
Manually changing network settings by modifying [FONT="Fixedsys"]/etc/network/interfaces[/FONT].  No effect
Booting from a freshly burned HH LiveCD.  Same as HH install: no effect.
Booting from the original GG LiveCD.  Success.

So, I figured it was some bug from HH that I didn't feel like dealing with and told the GG LiveCD to do a fresh install ('guided', whole disk, /dev/hda).

It is here that I am damned.

Since then any attempt to install - whether it be GG or HH - has stalled at 94%.  The bold text on the progress windows says '**[SIZE="3"]Installing GRUB boot loader[/SIZE]**'.  The small text says '*Running "update-grub"...*'

Attempted fixes:
Letting it sit for over 14 hours to see if it could just get over it.  No effect.
Disabling all other hard drives in BIOS.  No effect.
Physically disconnecting all other hard drives.  No effect.
Using [FONT="Fixedsys"]cfdisk[/FONT] to delete all partitions and [FONT="Fixedsys"]dd if=/dev/zero of=/dev/hda bs=512 count=1[/FONT] to blow away the mbr.  No effect.

Specs:
CPU: Intel Core 2 Duo 6400 @ 2.13GHz
RAM: 4GB (about 3.2GB end up being available due to 32-bit memory address limitations)
Video: NVidia GeForce 8800 GTS
Audio: On board (NForce chipset)
Hard Drive capacity (of /dev/hda): 200GB (usable capacity: 182 GB).

So: what can I do?  In either case, the install issue must be resolved.  If someone can /also/ resolve the HH network issue, that's gravy.  But to be honest, all I care about at this point is getting an OS installed.

---

### Post by sapph on 2008-06-10
Anyone?

---

### Post by lswest on 2008-06-10
I'd suggest seeing if it will install GRUB on a seperate partition (last step of the install wizard go to advanced and set GRUB to install on the partition you created with Ubuntu) and then follow the how-to either on [my blog]("http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html") or [this one (not written by me)]("http://ubuntuforums.org/showthread.php?t=224351")  It will give you more info about the problem with the install, and if it fails, you can use a 3rd party app to boot your OS after you install GRUB to the partition.

---

### Post by dstew on 2008-06-10
So, we have good reason to believe that the disk is good, because the Live CD system runs, and the installer ran perfectly before on the same computer in the same drive, correct? It seems you cleaned up the drive as best you could, so it is not that some remnant of grub is causing the problem.

If the installer got all the way to update-grub without failing, essentially everything is installed. You can boot a Live CD system, and check the hard disk partition for errors using fsck -a on the command line. If there seem to be no errors, you can try to finish installing grub to the hard disk system yourself from the Live CD. Find out which partition has the Linux system on it and mount it to the Live CD file system (I think all you need to do is find it in Places, right click and mount it). Look to see if the /boot/grub directory exists, and if the stage2 file and menu.lst are in there. If so, it should be simple to finish the installation. If those files are not there, or if there is no /boot/grub directory, it will be harder.

---

### Post by Herman on 2008-06-10
Just make sure it's the officially released version of Hardy Heron, the Beta and release candidate CDs both had problems with installing GRUB, but no-one should be using those anymore now. There might be some in circulation that people downloaded a while back and might still install.
[FONT=Bitstream Vera Sans Mono]
md5sum ubuntu-8.04-desktop-i386.iso[/FONT]
[FONT=Bitstream Vera Sans Mono]8895167a794c5d8dedcc312fc62f1f1f  ubuntu-8.04-desktop-i386.iso[/FONT]

---

### Post by sapph on 2008-06-10
dstew:  There is no /grub directory.

---

### Post by meierfra. on 2008-06-11
Try  the method in post 2 of this thread:
[URL="http://ubuntuforums.org/showthread.php?t=808994#2"]
http://ubuntuforums.org/showthread.php?t=808994#2[/URL]

---

### Post by sapph on 2008-06-11
That got me grub.  For some reason, menu.lst didn't get created, even after multiple attempts.  So I manually created it.  It took a few tries to get all the syntax right, but as of right now, I am typing this from an OS installed on my HDD.

Thanks, everyone. :)

---

