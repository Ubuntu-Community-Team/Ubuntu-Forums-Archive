---
title: "Removing Linux from Harddisk"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by sixfoottallrabbit on 2007-01-14
Hey,

I have a partitioned drive which is split into 3 main parts. Two contain OSs: both Windows XP and Ubuntu Linux. The other partition I use for storing files, documents and program files; this partition is much bigger than the other two. So basically, the Windows and Linux partitions contain only the system files for each operating system. GRUB is being used to select which operating system I want to boot from.

I recently tried to upgrade to Edgy Eft but failed miserably, so I was planning on removing Linux until EE is released on the shipit CDs.

Is it ok for me to just use partitioning software and remove the Linux partition? No other partitions would need to be removed? Would this also remove GRUB so it automatically boots from Windows?

Just, what do I need to do to remove it?

And when is Edgy Eft planning on being released on shipit CDs?

---

### Post by bulldog on 2007-01-14
Well you can remove the partition with linux or just format it NTFS,this will not remove GRUB,you need to use the windows install cd in recovery mode to make that happen.
In recovery mode type fixboot and after that fixmbr and windows should boot again from it's own boot loader.

If you wait for Edgy to be shipped to you,I'm afraid you will have to wait quite a while,because that's not gonna happen.
You can download Edgy just fine,so if you want Edgy you have to do so.

---

### Post by happy-and-lost on 2007-01-14
If I were you, I'd wait for the Feisty Fawn to be released and do a fresh install then. Restoring the Windows MBR goes like thus... (Courtesy of Novell's website)

> 7.5.2. Restoring the MBR of Windows XP

Boot from the Windows XP CD and press R during the setup to start the recovery console. Select your Windows XP installation from the list and enter the administrator password. At the input prompt, enter the command FIXMBR and confirm with y when asked to do so. Then reboot the computer with exit. 

Once you've reinstated that MBR it'll be safe to remove the Ubuntu partition.

---

### Post by sixfoottallrabbit on 2007-01-14
That sounds pretty easy. Thanks for that.

If I were to just download Edgy and burn it to a CD or DVD to install, how simple is it to make it install over my current Linux installation? I'm not sure why, but when GRUB loads, it lists Ubuntu and it's safe mode 4 times, with Windows XP at the bottom. I, of course, only have it installed once. I'm guessing this is just a mistake in GRUB though and won't cause me any problems if I want to install Edgy over Dapper?

---

### Post by bulldog on 2007-01-14
You have probably two different kernels installed which are listed in menu.lst.
To install Edgy you have to format your current install but you can install on the same partitions.
So if you have valuable data on it,just copy it before installing again.

---

### Post by sixfoottallrabbit on 2007-01-14
So, is this a good plan of action:
1) Fix the MBR of Windows just to ensure my safety when dealing with partitions because I suck at it, so that it boots from Windows when I start.
2) Get some partition formatting software and format the partition with Linux on.
3) Download Edgy, burn to DVD and install into formatted partition.

Sound good?

---

### Post by bulldog on 2007-01-14
You can skip step two,because you can do this when you install Edgy.
But if you want to format,download this [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and burn it to a disk and boot from it.

You will be surprised :D

---

### Post by sixfoottallrabbit on 2007-01-14
Ok, thanks. I guess I'll just do it as I install Edgy.

---

