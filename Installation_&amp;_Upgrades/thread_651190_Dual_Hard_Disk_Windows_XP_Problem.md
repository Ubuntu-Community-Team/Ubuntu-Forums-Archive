---
title: "Dual Hard Disk Windows XP Problem"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by eskimo on 2007-12-27
Hi to you, i'm an happy linux user. I love photography and i need Adobe Lightroom with better performance than wine emulation or virtual box emulation. So i bought a second hard disk to install windows xp. 
So my configuration was:
/dev/sda (serial ata)   linux partitions, system, data
/dev/sdb  (serial ata)  free...

i started iinstall windows and it didn't find any windows partitions on first hard disk (i wanted to install it on the second), so it didn't wanted to install its boot loader on first hard disk.
So i removed first hard disk (with linux on it) and i installed windows. I was ok. So i switched on first hard disk to modify grub to start win on second hd (hd1,0).
Nothing.

After some tries i have a windows on second hard disk that works only if he became tha first, by switching off the linux one. 

PLEASE SOMEONE KNOWS HOW TO INSTALL WIN ON SECOND HARD DISK WITH A PREEXISTENT LINUX ON THE FIRST??? SO THAT ARE EACH OTHER ON DIFFERENT HARD DISK...PLEASE KNOW THAT I WOULDN'T REINSTALL MY LINUX.

thank you!
Paolo

---

### Post by Pumalite on 2007-12-27
Have you tried changing the boot order in BIOS?
More or less you painted yourself in that corner.
Windows should be installed first in sda1. (that's the ideal)

---

### Post by mamlouk on 2007-12-27
I think [Mathew J. Miller](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) posted a method to install Linux on an already installed Windows computer.

Basically, what he did is install Windows on a partition, and Ubuntu on another, without installing grub on the MBR. After that, he copied the first 512kb from the Ubuntu partition and placed them in a .bin file in the Windows partition, and added a line in boot.ini.

If you follow the same procedure, you will be able to keep both your Linux and Windows in 2 separate partitions, and having the Windows boot loader do the work for you.

---

### Post by psusi on 2007-12-27
What exactly happens when you try to boot windows?  I think you will need to use the map command in grub to trick windows into thinking hd1 is actually hd0.

---

### Post by Pumalite on 2007-12-27
Good luck.

---

### Post by bernied on 2007-12-27
If the linux disk is still booting fine, then try this entry in your /boot/grub/menu.lst file:
```
title windows
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Like psusi said, this uses the map command to fool windows into thinking it is on the first disk.

[EDIT]It is possible that grub won't see those sata drives as hd0 and hd1. You can find out what grub sees in a grub console - this is available either at boot, by pressing the 'c' key, or if grub is not booting, from a linux live cd, use the command 'grub' or 'sudo grub'. Once you have a live cd, use TAB-autocompletion - type 'root (' then hit the TAB key, you should get a list of drives, as grub sees them.

---

### Post by bernied on 2007-12-27
If you can no longer boot linux, then check the jumpers on the disks (these can be set to master, slave or auto-detect - which doesn't always work - better to set the linux one to master, and the windows one to slave), and check that both disks are seen in the bios. If that fails, get a live cd, and see that the linux disk is still visible.

---

### Post by jmorales on 2007-12-27
Sounds kind of like the problem that I'm having on my system that I posted here [http://ubuntuforums.org/showthread.php?t=650848](http://ubuntuforums.org/showthread.php?t=650848) Essentially having the two OS already installed on their own drives and having Ubuntu as the main drive. But I haven't gotten any feedback so I'm curious to see if any of these work for you so that I can try them

---

### Post by psusi on 2007-12-27
> **bernied said:**
> If you can no longer boot linux, then check the jumpers on the disks (these can be set to master, slave or auto-detect - which doesn't always work - better to set the linux one to master, and the windows one to slave), and check that both disks are seen in the bios. If that fails, get a live cd, and see that the linux disk is still visible.

They are SATA not IDE, so no jumpers, no master/slave.

---

### Post by bernied on 2007-12-27
> **psusi said:**
> They are SATA not IDE, so no jumpers, no master/slave.
Sorry, I'm a few steps behind. Did you try the grub console to see how grub sees the disks?

---

### Post by eskimo on 2007-12-28
now i have problem booting with linux, i don't know wath i did but it can't find my root filesystem 
searching by UUID, and if i do  ls /dev/disk/by-uuid/   i can't find /dev/sda1 
...now i'll try to find a solution for this, and then i will try
map (hd1) (hd0)
map (hd0) (hd1)


if no lucky i'll reinstall all systems and **** off to windows....
thanks...noone tried to install windowws on a second hard drive with a linux installed on first??

---

### Post by Pumalite on 2007-12-28
I suggest that if you reinstall, install XP in the whole first drive. Then get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and resize XP partition. In the new partition:
10 GB for '/'
1 GB for /swap
The rest for /home
Install Ubuntu to that partition. Go Manual and use the partitions already made.
Let Grub install to the MBR; you'lll have dual boot.
Use the 2nd drive for storage.

---

### Post by eskimo on 2007-12-28
ok thank you for advices, but i'm not a novice, i know the law. Win on first and linux on second. I cant'understand why i can't install win xp on second hd....
now i can reboot with my linux (due to UUID...) and i retry with map...

---

### Post by bernied on 2007-12-28
> **eskimo said:**
> if no lucky i'll reinstall all systems and **** off to windows....
thanks...noone tried to install windowws on a second hard drive with a linux installed on first??
You are certainly not the first to do this, and there is no law. These people are merely quoting a recipe which just works - it does not mean it is the only way.

I have my windows on a separate hard-drive. It was installed first but this is irrelevant. You can boot from either disk if you have grub set up properly.

You don't have to reinstall, you just need to know how booting works, and you need to know how different components of your system recognise your disks.

What is important for you is how grub is detecting your disks. You can work this out using the grub console, as described in one of my earlier posts. You can also find this described in Herman's site (see below).

It is also important to know whether your linux install still works with both disks attached - it sounds like your disk numbering changes when you add that second disk, so when you boot you get that error of not being able to find your root filesystem. Perhaps this can be corrected in the bios?

Herman (who hangs out here) has an extensive [guide to grub](http://users.bigpond.net.au/hermanzone/p15.htm) and dual-booting.

Google is also useful.

I am sorry I am unable to help more - the thing that is unfamiliar to me is the sata setup, I have no experience with sata drives and how they are recognised by grub.

---

### Post by psusi on 2007-12-28
The reason for the difficulty in having windows not on the first disk is that the windows boot loader is kind of stupid and assumes it is on the first disk, rather than use the boot disk ID passed by the bios in the CL register.  Apparently this was done because the PC BIOS was never standardized and 20 years ago, not all of them could be relied on to pass the boot device ID, and none of them could be told to boot from a disk other than the primary one.

---

### Post by bernied on 2007-12-28
> **psusi said:**
> The reason for the difficulty in having windows not on the first disk is that the windows boot loader is kind of stupid and assumes it is on the first disk...
Yes, but the [grub map command](http://www.gnu.org/software/grub/manual/grub.html#map) should be able to sort this out for you. Or does it not work for sata?

I prefer to think of windows as selfish, rather than stupid. Those lovely microsoft folk could easily have changed this long ago, but chose not to.

---

### Post by psusi on 2007-12-28
Yes, the map command is there just for that reason and will work, but you have to configure it yourself.

---

### Post by eskimo on 2007-12-29
Hit o you guys, it's almost all ok!!!
i've added  map (hd0) (hd1)   map (hd1) (hd0)   to grub's menu.lst and now everything works...

but still remains the UUID problem, in fact my first partition of my first hard disk (linux root) and whole hd aren't ok, if i try to access with fsidk or vol_id it gives me error.... with gparted i noticed that it's not mounted only on root (/) but also on /dev/.static/dev !!! what did happen? how to return to / without damage? because now i have to boot with /dev/sda1 and not with UUID, but it works....
thank you very much....
Paolo

---

### Post by bernied on 2007-12-29
To check whether you are using the right UUID:
```
tune2fs -l /dev/sda1 | grep UUID
```
Maybe it has been changed - somehow?

---

### Post by psusi on 2007-12-30
> **eskimo said:**
> Hit o you guys, it's almost all ok!!!
i've added  map (hd0) (hd1)   map (hd1) (hd0)   to grub's menu.lst and now everything works...

but still remains the UUID problem, in fact my first partition of my first hard disk (linux root) and whole hd aren't ok, if i try to access with fsidk or vol_id it gives me error.... with gparted i noticed that it's not mounted only on root (/) but also on /dev/.static/dev !!! what did happen? how to return to / without damage? because now i have to boot with /dev/sda1 and not with UUID, but it works....
thank you very much....
Paolo

Huh?  What do you mean fdisk gives you an error?  What was the command, and what was the error?  What do you mean it's mounted on /dev/.static/dev?

---

