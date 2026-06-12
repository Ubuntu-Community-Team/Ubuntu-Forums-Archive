---
title: "[SOLVED] PLEASE HELP! Error 12: Invalid device requested"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by philidox on 2008-05-25
I finally got my dual boot going and I ran into a wall.  Everytime I attempt to load Windows from the grub menu list.  I get this:

Error 12: Invalid device requested

Press any key to continue...

I can load ubuntu just fine.  I followed a howto guide on dual booting with linux installed first. This is the url: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Pumalite on 2008-05-25
You are trying to boot Windows from a logical partition. Windows requires a primary partition, preferably sda1.
Post screenshot of Gparted
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

---

### Post by philidox on 2008-05-25
> **Pumalite said:**
> You are trying to boot Windows from a logical partition. Windows requires a primary partition, preferably sda1.
Post screenshot of Gparted
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

Thanx alot I was abile to eliminate that error 12 but I cannot boot to windows just yet(I'm so close!).  I went to the page you recommended and I lack only one thing, I cannot set the logical partition as a primary.  I used the gparted and ubuntu live cd and everytime I try add the lba attribute it wont let me any suggestions?

---

### Post by Pumalite on 2008-05-25
Post:
sudo fdisk -l

---

### Post by RemThe on 2008-05-25
I have the similar problem. I get an error 12.

Fdisk -l:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb27a6dec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         304     2441848+  82  Linux swap / Solaris
/dev/sda2           13056       19457    51424065    f  W95 Ext'd (LBA)
/dev/sda3   *         305       13055   102422407+  83  Linux
/dev/sda5           13056       19457    51424033+   7  HPFS/NTFS

Grub Menu:

> title		Windows NT/2000/XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1

I would appreciate any help.

---

### Post by hal8000 on 2008-05-25
> **RemThe said:**
> I have the similar problem. I get an error 12.

Fdisk -l:



Grub Menu:



I would appreciate any help.


Windows must always have the first partition.
I see no other way except for a reinstall.
You have used 3 primary partitions for swap and linux,
unless someone has a better way, it will be better to start again,
repartition and load windows first, then install linux.

You dont have to install windows first just create a primary partition
Boot with the live cd then 
sudo fdisk /dev/sda

d (for delete partition)
5 (to delete partition 5 and so on in reverse order)

n (for new partition)
p for primary
1 for partition 1
press enter for 1st cylinder
size (enter +40000M   for 40G) etc
w  to make changes and reboot.

You will need to reboot so that the kernel sees the new partition table.

An alternative is to use gparted or maybe some windows software like acronis.
The only consolation is its better to repartition when you dont have much data on your system., e.g. fresh install.

---

### Post by Pumalite on 2008-05-25
I'd advise to start from scratch after saving data. Put Windows in a primary partition in sda1 (at the beginning of the drive). Install Ubuntu last. Use Gparted Live CD to repartition your drive:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by RemThe on 2008-05-25
Thank you for your reply.
I Had Vista on the first parts of my hard disk. And Xp on the last. 
I thought that it would be fine because i was not moving xp anywhere.
But i do remember that now.

Is there no other way to do this without removing my xp? It has a lot on it.

---

### Post by Pumalite on 2008-05-25
As a matter of fact; if you plan to have XP, Vista and Ubuntu, you will have to install them in that order.

---

### Post by RemThe on 2008-05-25
> **Pumalite said:**
> As a matter of fact; if you plan to have XP, Vista and Ubuntu, you will have to install them in that order.

I love Microsoft... i really do... :(

Thats life. Thank you for your response. :)

---

### Post by Pumalite on 2008-05-25
You are welcome. Good luck.

---

### Post by meierfra. on 2008-05-25
It is possible to boot Windows from a logical partition. Both I and Herman (for hermanzone) have succesfully done it. But as far as I know neither he nor I have  been   able to teach somebody else  how to do it. So reinstalling  probably  is the easiest and fasted way to go.

But  if  you hate the idea of reinstalling, let me know and I'll try my best to show you  how to fix you current install.

---

### Post by philidox on 2008-05-26
Wow I must give Ubuntu its praise because I never imagined that one 700mb disc could be so useful.  To solve my issue I just deleted both partitions.  I installed Window( as the first AND primary partition) like I normally do then I just simply put in the ubuntu os cd and INSTALLED UBUNTU FROM WITHIN WINDOWS, like any other exe file.  How can one cd do both live cd and installed an entire os from within an os?  That was amazing!

---

