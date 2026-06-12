---
title: "Dual-Booting 2 versions of Ubuntu"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Aeph on 2008-02-15
I already have Gutsy installed on my PC, and I want to install it again on an external hard drive so I can use it elsewhere. I also plan to setup the new install using my computer. My question is this: Will GRUB crap itself if there are two of the same distro available. If so, then I will probably install Linux Mint on the external instead. Should 2 Gutsy installs be a problem?

---

### Post by Herman on 2008-02-15
GRUB won't 'crap itself', you can install as many operating systems as you like, all the same or all different. The problem with GRUB is normally in the user, not GRUB.

Regards, Herman  :)

---

### Post by jken146 on 2008-02-15
Grub will be OK, as long as you give the 2 isntalls different titles.  This will require some editing of the /boot/grub/menu.lst file -- the one you use should be the one on the internal disk and the internal Ubuntu should be the default.

---

### Post by Herman on 2008-02-15
You'll learn a lot from it.

When you are finishing the installation, GRUB will probably be installed to MBR in the internal hard drive. (Unless you're smart enough to take steps to direct it elsewhere).
You'll need to re-install the internal hard drive's GRUB to MBR in the internal hard drive, and re-install the USB disk's GRUB to MBR in the USB disk.
Those two jobs are simple enough.

You can boot the USB disk either by making an entry for it in your installed GRUB, or from your internal installed [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), or you can boot it from the BIOS in some computers directly by pressing the F8 or F12 or some other key at the right time during boot up.

Not all computers have a BIOS that can boot a USB drive at all.  

There are two kinds of USB installs. One kind is when you run the Ubuntu installation CD and install to the USB drive as if it was another internal hard drive and you make a regular installation.
Each time you boot it in a computer with very different hardware you'll probably have to run [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html") to set up the /etc/X11/xorg.conf file (for the right video, monitor and keyboard and mouse drivers).
The /etc/X11/xorg.conf files get backed up each time, so when you go back to your own computer you can restore the original /etc/X11/xorg.conf file with a cp command if you want, that will save you some time.

Another kind of USB installation can be done by copying the files from a Live CD to a partition in the hard drive and booting the files as a Live CD. That way it sets itself up for any hardware automatically just as a real LiveCD would, for almost any computer you want to plug it into. 
Unlike a real LiveCD you can rig it up to save your settings, added software and files, that's called 'persistence'. 
To do that you can make another partition and providing it is named 'casper-rw', you can have it mounted at boot time and any changes you make such as added software and settings will be saved in the 'casper-rw' partition. You use a special boot option in your GRUB menu to get the kernel to mount the 'casper-rw' file system.
 That is one way to get the advantages of a live CD and the advantages of a real installation. The only problem is the way the Live CD kernel unmounts the casper-rw partition seems a bit rough, it leaves a few error messages, but they don't seem to be anything too much to worry about.

An operating system in a USB is extremely useful, especially Ubuntu, but you should be extra careful not to drop the USB while it's spinning and also be aware of the temperature inside the USB box, not very many of them have a case fan, I haven't seen one with a case fan yet. Hard drives get hot and need cooling like most other PC parts, especially if you use them for a while.
Heat and shock are probably the two biggest killers of hard disk drives.

A USB flash memory stick would be much more durable, but those are small and they're expensive if you work out how much you pay for one on a per GB basis.
If you set up SSH networking in your home computer and set up port forwarding, you can access files in your home computer from a USB stick anywhere on the internet and get around the limitation of the USB stick's small size that way.

Good luck with it and have fun,
Regards, Herman :)

---

