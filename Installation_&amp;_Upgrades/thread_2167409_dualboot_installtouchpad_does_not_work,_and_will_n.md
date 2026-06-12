---
title: "dualboot install:touchpad does not work, and will not boot to Win7"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2013-08-13
New Net book: 

Win7 preinstalled.  Just installed Ubuntu 12.04LTS created 4 new partitions (Swap, Grub, OS, Data).  Now the touchpad does not work and I cannot boot into windoze.  I figure the mount point for win7 is not correct, but I do not know how to change it.  The touchpad not working is an unknown.  Wireless mouse will work.  My partitions are: PQService(winrestore), Win7 OS&data, systemReserved(winloader), swap(linux), /boot(grub),/ (OS-Ubuntu12.04), and /home(my data).  These is the same partition scheme I used on this Acer Aspire TimelineX laptop.


Netbook is an Acer Aspire ONE AO0725 10.6-in 64bit, 320-GB HD. and has not been included in my profile.

---

### Post by jlh68 on 2013-08-13
Well I got the touchpad to work.  found solution:    [Ctrl]+[Fn]+[F7}  did the trick.


Now to get the dual boot to work.

---

### Post by oldfred on 2013-08-15
Best to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by oldrocker99 on 2013-08-15
There are quite a few Linux-based (for that matter, I think they're ALL Linux-based) rescue disks out there; I used one to repair GRUB a few months ago. That might be the best solution.

---

### Post by jlh68 on 2013-08-24
I have a couple of them, and they are as you said "disks".  I would use one except I am working with a netbook that does not have an optical drive.  I have not been able to install a rescue disk .iso onto a Flash drive yet.  I have seen several methods, and they all seem complicated.  A lot more complicated than making a "live Ubuntu" Flash drive.

---

