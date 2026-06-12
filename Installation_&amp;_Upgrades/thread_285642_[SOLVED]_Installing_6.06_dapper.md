---
title: "[SOLVED] Installing 6.06 dapper"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by werdna5225 on 2006-10-27
I have two hard drives.  A new one with windows xp, and an old one that used to have windows xp but now has ubuntu on it.  The only way I can get ubuntu to boot is if I have both hard drives plugged in and the one with ubuntu on it the master.  How can I get ubuntu to boot without having to have this other hard drive plugged in?  I am also a complete noob in the area of linux systems.

---

### Post by pay on 2006-10-27
Well you would have to reinstall grub after you changed your harddrives.

---

### Post by Archmage on 2006-10-27
Another possibile solution:

You need to change the jumper from "Master, Slave present" to "Master, no Slave present" on your old ide.

---

### Post by werdna5225 on 2006-10-31
I have both hard drives set to jumper cable select.  Whichever one  Iplug in to the master cable that is the one that boots.  How can I get it to give me the choice to choose which operating system to boot.

---

### Post by az on 2006-10-31
> **werdna5225 said:**
> I have both hard drives set to jumper cable select.  Whichever one  Iplug in to the master cable that is the one that boots.  How can I get it to give me the choice to choose which operating system to boot.

Plug the Ubuntu drive as master and then edit the grub menu to point to the windows hard drive.

Find the following stanza in /boot/grub/menu.list

title           Windows 
root            (hd0,0)
savedefault
makeactive
chainloader     +1

and change that to what it should be:
root            (hd1,0)

(That's probably it...   hd1,0 would be the 0 (first) partition on the second hard drive - the first partition on the first hard drive is as above, hd0,0 .  It's zero-indexed, get it?)

---

### Post by werdna5225 on 2006-10-31
> **azz said:**
> Plug the Ubuntu drive as master and then edit the grub menu to point to the windows hard drive.

Find the following stanza in /boot/grub/menu.list

title           Windows 
root            (hd0,0)
savedefault
makeactive
chainloader     +1

and change that to what it should be:
root            (hd1,0)

(That's probably it...   hd1,0 would be the 0 (first) partition on the second hard drive - the first partition on the first hard drive is as above, hd0,0 .  It's zero-indexed, get it?)
When I try to save the file I get the error message:
Could not save the file /boot/grub/menu.lst
You do not have the permissions necessary to save the file.  Please, check that you typed the location correctly and try again.

I am trying to save to the location:

Name:menu.lst
Save in folder:  grub
Character coding: current locale (UTF-8)

---

### Post by az on 2006-10-31
> **werdna5225 said:**
> When I try to save the file I get the error message:
Could not save the file /boot/grub/menu.lst
You do not have the permissions necessary to save the file.  Please, check that you typed the location correctly and try again.

I am trying to save to the location:

Name:menu.lst
Save in folder:  grub
Character coding: current locale (UTF-8)
Use sudo.


sudo nano /boot/grub/menu.list

or

sudo gedit /boot/grub/menu.list

---

### Post by werdna5225 on 2006-11-01
Now I am getting the error message   Error 21: Selected disk does not exist.  Is there a way to find out the address of the drive?  Like the (hd0,0)? Or the kernel name like linux has?

---

### Post by az on 2006-11-03
> **werdna5225 said:**
>  Is there a way to find out the address of the drive?  Like the (hd0,0)? Or the kernel name like linux has?

It's the bios that will determine that.  In some buggy BIOSes, the drive order is screwed up.  You have a /boot/grub/device.map file which is useful for fixing that if that is the case.

I can't tell you more without knowing what your bios thinks is going on.  Maybe you can see that in the BIOS configuration (setup) screen?

---

### Post by werdna5225 on 2006-11-03
I finally got it fixed.  I re-installed Ubuntu while I had both hard drives plugged in, windows is master and ubuntu is slave.I also put in a new cable cuz the other was messed up.  Thank You for all the help.

---

