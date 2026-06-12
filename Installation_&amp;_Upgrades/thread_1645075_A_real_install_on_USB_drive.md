---
title: "A real install on USB drive"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by Sidrabs on 2010-12-14
Hello,

I was looking for discussion about installing Ubuntu (or any other distro, on that matter) on USB flash drive. Just to find that there is wild misunderstanding about what "Install" means, when we are talking about USB flash drive.

In most of the tutorials, there are instructions about how to create "Live USB Flash drive", just like "Live CD". That is good for carrying around and doing some stuff on random PCs, but it does not provide you with real installation though. With real I mean a normal Linux installation where one can configure users, install new packages and keep files.

Stangely, the latter is not referenced too much, and I'd like to know why so. It seems totally reasonable thing to carry around a normally set up OS on a Flash drive, instead of just "Live boot version". It's almost like another laptop, but you have to borrow some hardware to run it :) Are there any underwater stones one should know? One is the slowness of typical USB Flash drive, that's for sure. The other is that you want to have at least 4GB drive, if want any serious work on that installation. Then there could be issues about the fact that this installation will be forced to adapt to any random PC the drive is plugged in, but I'm not sure if there are any serious consequences from that. Is there anything else?

---

### Post by ajgreeny on 2010-12-14
You may need to choose your format type as ext2, to avoid too many writes to the flash drive, as ext2 will not be writing a new journal every time a file is changed but will wait until you shutdown, I think.

The possibility of hardware problems is a real one, however, particularly if the machine you normally use it on needs a proprietary graphics driver, which will then override the open source drivers that could otherwise be used on other hardware.  However, any problems of this sort will simply mean that the system will not be able to boot; it should not cause any problems to the hardware itself.

I'm sure there must be other things to think about as well, but never having done this, I will have to defer to others with more knowledge.

---

### Post by C.S.Cameron on 2010-12-14
On full installs I use a separate /home partition and make it ext2.
I start with a FAT32 partition so a Windows machine can see it when transferring files.
On a 4GB stick I don't normally use swap.
I don't load any proprietary drivers as dual monitors seem to work ok with generic ones now.

There is a application named switchconf that lets you choose between xorg.conf files at boot.
In the old days, circa 8.04, xorg.conf files controlled the loading of graphic drivers. 
At boot you could choose between various Nvidia settings or to use the generic driver. You could have either Nvidia or ATI, not both.

I can't think of a lot of things that a Full install will do that a well configured Persistent install won't do, except perhaps install video drivers. Security might be a little weak also. 
OK, the start screen sucks a bit, I've been using UNetbootin for disk image installs because I prefer it's start screen. 
A grub2 iso install might be preferred to a UNetbootin install except usb-creator and wubi are not available when it's plugged into a windows machine
Both can be made persistent using casper-rw and home-rw partitions.
You can change out iso images and edit the menuentry with a new version of Ubuntu. Keeping the home-rw partition works but you should probably start a new version with an empty casper-rw partition.

Sorry, did you say "discussion" or did you say "rambling"?

Edit:
As for slowness I understand that there is a method to get Ubuntu running in RAM that is insanely fast and works on a flash drive. I have not tried it yet.

---

### Post by jimmers on 2010-12-14
Hi,
I run 3 Ubuntu Distros on USB Drives, Lucid which is a Clone of my Lappie, Maverick which I use just to see how it performs, and Jaunty somewhere in the desk drawer, all are installed on a Kingston DataTraveler G2 16 GB, with no problems, all I did was do a clean install, use the whole disk, and just made sure that I selected the Advanced Option (ie SDB1 or Kingston DataTraveler), and I have no problems upgrading or installing any app.

---

