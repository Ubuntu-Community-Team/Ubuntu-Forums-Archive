---
title: "Major Help Needed with 7.10 Upgrade"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by odin_dax on 2008-01-11
Lucikly, I have everything backed up. I also want everyone to know I'm using a Knoppix LiveCD that I don't know how to use fully.

I clicked up on the upgrade button to go from 7.04 to 7.10, but I enountered several update or keep pop-ups. After one of these, I don't know which, the install quit at about midway. I got an error message, but I don't know what it said, but it was something about a command line code to retry the installation.

Anyway, the system got rebooted, but then the GRUB disappeared! It hangs at "GRUB Loading, please wait..." Also, I can't insert any live CD's of Ubuntu past 6.10, they aren't recognized and the screen stays black. Earlier LiveCD's don't show a GRUB menu.lst file.

In Knoppix, I looked at the menu.lst file. Everything is commented out except the OS's. There are at least ten, all saying Ubuntu 7.10, but with different kernal numbers.
They all point to (hd0,1)
All of them say: 
/boot/vmlinuz-(kernal number) root=UUID=(all the same number) ro (either single or quiet splash)
Next line below /boot...
/boot/initrd.img.(kernal number)

The newest entry says:
Ubuntu 7.10, kernal 2.6.22-14-386
(hd0,1)
/boot...
/boot...

Two questions. 
How do I fix the GRUB?
How do I "fix" the install?

---

### Post by SunnyRabbiera on 2008-01-11
I can suggest using your knoppix disk to try and repair the system.
If you have everything backed up I would use knoppix to reformat the drive and then try a reinstall.

---

### Post by odin_dax on 2008-01-11
> **SunnyRabbiera said:**
> I can suggest using your knoppix disk to try and repair the system.
If you have everything backed up I would use knoppix to reformat the drive and then try a reinstall.

I've actually tried installing other versions again. Like I said, the Fiesty or Gustsy CD's won't load, but I did try 6.10. After reboot, it disappeared like all the others.

If it helps, I have a CD of GParted, but I couldn't get a menu.lst file pulled from Thunar.

---

### Post by odin_dax on 2008-01-11
*bump*

---

### Post by odin_dax on 2008-01-12
Wow, this is the first time the community hasn't been able to help, let alone get back to me.

---

