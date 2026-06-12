---
title: "Installation Troubles"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by jgreath on 2005-09-15
I know that 5.10 (Breezy Preview) is not supported, but I was hoping to get some help anyway.  My installation stops at the disk partitioning step.  My only option on the dialog is to continue or go back.  Selecting either of these options does nothing, and all that's displayed on the dialog is its title ("Partition Disk") and what I assume is supposed to be a list of disks to partition but is instead filled with "??? ???"

Is there a problem with my disc image or my PC?  Or is this a known problem with the Breezy Preview?

---

### Post by jackmacokc on 2005-09-15
what kind of disk are you using? pata or sata

---

### Post by jgreath on 2005-09-15
All of my disks are PATA.

It's an nForce 3 motherboard.  I know that I needed a SATA kernel module to mount my disks in Slackware 10.1, though.  Not sure why, but when I took that module out my system refused to boot.

I'm going to give this a shot -- [http://ubuntuforums.org/showthread.php?t=63751](http://ubuntuforums.org/showthread.php?t=63751)

---

### Post by jgreath on 2005-09-15
Okay, that worked.  I got it installed, but now it's not recognizing my USB keyboard or mouse.

These devices work up until I select which OS to boot from GRUB.  They also work with Windows XP Pro and they were just fine throughout my experiences with Gentoo and Slackware.
If it were just the mouse, I could figure it out on my own, but I can't do anything at all without a keyboard and I've never had these problems before.

---

### Post by jgreath on 2005-09-16
Got that all working!  Turns out that I had acpi=off in my GRUB configuration, removing that setting entirely fixed it.

---

