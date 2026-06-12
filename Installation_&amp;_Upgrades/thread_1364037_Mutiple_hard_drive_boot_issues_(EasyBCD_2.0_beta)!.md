---
title: "Mutiple hard drive boot issues (EasyBCD 2.0 beta)?!?"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by markjs on 2009-12-25
I always run one operating system per hard drive because I like to screw around a lot with things for the sake of learning, and I find it is the best way that if anything terrible should happen, that at least Windoze will boot since it is what I most frequently need and know best. 

The trouble I have is that it seems that questions about how to set up multi-boot options rarely even mention multiple physical hard drives.  Information on this particular subject is largely unheard of!

I once got Grub to handle this on the Ubuntu side, but being as I am so much more comfortable and trained in Micro$oft operating systems, I have decided I would like to set this up on the drive dedicated solely to Windoze 7.  For that and all my Windoze installs I use EEasyBCD Beta 2.0.  I tried my first run of it and there was an option for Grub not being installed and it of course was not on the 7 drive, so what it did is put it there.  So it gives ubuntu as an option in the Windoze boot loader, and then it goes to Grub on that drive.  My only trouble now, is how do I get the version of Grub to then send the process on to the separate hard drive on which Ubuntu is installed?

Ideally I want to become as good with Ubuntu as Windoze, because I am increasingly troubled with security issues and want to support open source, but in the mean time, can anyone help me with this one simple issue?  It would be much appreciated, and I would love to be able to pass the knowledge along and use it on customer&#347; computers if I can talk them into giving Ubuntu a chance.

---

### Post by markjs on 2009-12-26
OK, I can´t imagine why nobody has answered this.  I figured it out without any help.  I just booted it to Ubuntu and then when the meu came up and I edited it from hda 0,0 to hda 1.0 (that is the grub on the Windoze hard drive).  Now it gives me all the options!

Thanks for being here if not for helping today

---

### Post by markjs on 2009-12-26
OK, well maybe I am not as smart as I thought....

That little edit trick works but has to be done on every boot.  I am assuming that the file that needs to be permanently modified is on the Win7 drive, and it has to reflect the second hard drive has ubuntu.  I can for the life of me figure out what file is is, much less how to edit more permanently.

---

### Post by oldfred on 2009-12-26
I do not know EasyBCD but have seen a few users who seem to like it. I am now 90% linux from about 3 years ago when I was mostly windows.

I also like having each operating system on a separate drive and that boot loader in that drive's MBR. I am more familiar with grub and now grub2 so I make my Ubuntu drive first in BIOS and select windows from the grub menu.

When you install Ubuntu grub will automatically install to the boot drive usually the windows one and overwrite the windows boot loader. That is normally not a problem since grub will boot the windows but both drives have to work for either system to boot. I like to make the Ubuntu drive first and then grub installs there. In the install of Ubuntu you can use the advanced button about 2/3 the way thru to tell it where to install grub. You can also run this command to load grub to another drive.  You do have to be sure which drive is which as it will just say sda, sdb, etc.
sudo dpkg-reconfigure grub-pc

I assume you still need grub in the mbr of the ubuntu drive for EasyBCD to chainboot Ubuntu from windows.

---

### Post by markjs on 2009-12-28
Well as it turns out using EasyBCD isn so easy.  The only way I have found to make sure you know what drive you are dealing with with it is to unplug all the others!

Once I learned the syntax to use I just set it all up in menu.lst and that was MUCH easier!

---

