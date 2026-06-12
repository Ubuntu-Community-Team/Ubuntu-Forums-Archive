---
title: "feisty not working"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by tyler1175 on 2007-06-19
I just built a new pc with an intel dp965lt motherboard,e6600, and a sata dvd drive. It will boot from cd and install fine but when I reboot after installing it says  error loading operating system. I think it might a problem with grub and my motherboard.

---

### Post by bulldog on 2007-06-19
Make sure you're booting from the hdd and not from the sata dvd.
They are both master devices and it possible your sata dvd is connected to your first sata connector.

---

### Post by tyler1175 on 2007-06-20
> **bulldog said:**
> Make sure you're booting from the hdd and not from the sata dvd.
They are both master devices and it possible your sata dvd is connected to your first sata connector.

no thats not it when i tell bios to boot from hard drive first it gives me the same message.but when I tell it to boot from the hard drive that has windows on it it boots into windows fine.I tried installing easybcd boot loader but that didnt work either. So I think its a problem with the motherboard not accepting a boot loader like grub but i'm not sure. Any suggestions?

---

### Post by tyler1175 on 2007-06-20
bump

---

### Post by tyler1175 on 2007-06-20
bump

---

### Post by tyler1175 on 2007-06-24
I tried installing it on another hard drive and get the same message error loading os i'm pretty sure it's a problem with grub and my motherboard. any suggestions?

---

### Post by bulldog on 2007-06-24
Did you check the cd on any errors before installing?
I don't think  your motherboard is the course of your problem.
Is grub installed properly?
Check with the live cd if you have a menu.lst in the grub folder.
If you have found it [mount your ubuntu install first] post it to the forum,and I will have a look at it later today.
Post the output of ```
sudo fdisk -l
``` as well.

---

### Post by tyler1175 on 2007-06-24
checked the cd and it has no errrors, there is a menu.lst file in the grub folder I attached it, and here is the fdisk -l output the 150 gb hdd is for windows and the 320gb hdd is for storage.
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18242   146521088    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29651   238171626   83  Linux
/dev/sdc2           29652       30401     6024375    5  Extended
/dev/sdc5           29652       30401     6024343+  82  Linux swap / Solaris

---

### Post by bulldog on 2007-06-25
OK,looked at your menu.lst ,and didn't see anything wrong with it :p

You have two Vista installations on sda and sdb.
The question should be,on which hdd did you installed GRUB?
It should be installed on sdc,but if you didn't change  anything while you where installing ubuntu,it should be installed on sda by default.

Now the best thing you could do,is install GRUB to sdc,using the live cd.
I will tell you in a minute how you can do so.
A very important thing is **MAKE THE UBUNTU HDD YOUR MASTER BOOT DEVICE IN THE BIOS AFTER INSTALLING GRUB,OTHERWISE YOU WON'T SEE THE GRUB MENU**

Now to reinstall GRUB boot the live cd and perform the next commands,
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)<====In your case it should be (hd2) which is similar with the sdc
```
Exit the grub shell
```
quit
```

---

### Post by tyler1175 on 2007-06-25
YES it worked thankyou!

---

