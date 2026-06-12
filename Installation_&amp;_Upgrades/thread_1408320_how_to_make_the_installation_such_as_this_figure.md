---
title: "how to make the installation such as this figure"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by snake_eyes on 2010-02-16
Hello,


How to make the installation such as this figure?

> /dev/sda1 996M 51M 894M 6% /boot
/dev/sda2 117G 672M 110G 1% /
/dev/sda3 30G 18G 9.9G 65% /var
/dev/sda5 20G 6.9G 12G 38% /usr
/dev/sda7 7.8G 147M 7.3G 2% /tmp
/dev/sda8 352G 202G 133G 61% /home
/dev/sdb1 458G 287G 148G 66% /disk1

Cheers,

---

### Post by darkod on 2010-02-16
> **snake_eyes said:**
> Hello,


How to make the installation such as this figure?



Cheers,

First of all, in case you don't know, on one hdd you can have only 4 partitions either primary or extended. But inside an extended partition you can have more logical ones, which allows you in fact to have more than 4.
Linux is labeling the 4 partitions /dev/sda1 to /dev/sda4. The logical ones are /dev/sda5 onwards. So you could have only:
/dev/sda1 primary
/dev/sda2 extended
/dev/sda5 logical inside /dev/sda2
/dev/sda6 logical inside /dev/sda2

Don't be confused where are /dev/dev/sda3 and /dev/sda4, they don't need to exist but the logical partitions will always be /dev/sda5 and up.

For this setup, having a 1GB /boot is too much, you can see yourself it uses about 51MB right now. 100MB to 200MB is enough for /boot.
Also in that list the swap partition is missing because it doesn't show but I guess that is /dev/sda6 which is missing in the list.

Start the installer and in step 4 select Manual partitioning. Thn start creating the partitions one by one, as per the list:

1. Create 200MB primary partition, filesystem ext4, mount point /boot.
2. Create xxxGB primary partition, filesystem ext4, mount point /
3. Create xxxGB primary partition, filesystem ext4, mount point /var
4. Create xxxGB logicl partition, filesystem ext4, mount point /usr (this will automatically start creating them as logical inside one big extended partition)
5. Create swap, filesystem swap area, mount point swap
etc, continue

I hope it's not complicated the way I wrote it. :)

---

### Post by snake_eyes on 2010-02-16
Thank for your quick response....

Can you explain to me for what is the RAID? and is the ubuntu support it? we can install the ubuntu with any distribution on RAID? what is the different between RAID 1 RAID 2 RAID 3 etc....

---

### Post by darkod on 2010-02-16
RAID is a way to use more drives with the idea that if one fails your system still keeps working and the data is safe. With exceptions.
Mostly used types are RAID0, RAID1 and RAID5.
RAID0 is an exception that you data is safe, that's why they decided to call it 0. You take two equal disks and during the setup of the RAID array it splits them into small blocks. Then when you write to the array, it writes on one disk, then the other, and it goes like that. Because it is accessing two disks, the speed to write/read is in theory faster, but if one disk fails, you loose all the data because the other will have only half of it so you can't recover it.
For RAID0 the usable space is all of it, 2x the size of the hdds.

RAID1 is mirror, you write to one disk and the other is a copy. If one disk fails, you haven't lost anything. But the usable space is only as big as the one hdd, like the other is lost space.

RAID5 is created with 3 or mor disks, and also the data is protected if one disk fails. The usable space for N disks is N-1. So if you use three disks of 1TB you have usable 2TB of the array.

If you need more details you'll find plenty of tutorials and guides on google.

Ubuntu supports raid but it's better to use the Alternate Install cd, not the standard desktop live cd. It's also better to use Software RAID but only if you don't plan to dual boot with windows. It won't work dual booting, not if you want windows on the raid too.

---

### Post by snake_eyes on 2010-02-16
In my case I have Fujitsu Simens server with RAID, I'm not planing to use the server with multiple boot (Windows and Linux), I wanna use it only for Ubuntu.

I'm using this server since 2 years when we (In the department) testing it, now I wanna format it in order to setup the RAID, I didn't touch any server before even I didn't try to prepare any instance with RAID.

In my case also I 6 HD I should when the server is up, when I remove any hardisk shouldn't make any disaster, my question is when I run the simens bootable disk in order to setup the raid, after preperation is the setup will be removed during the Ubuntu installation? please note that I'm using the "use entire disk" option in order to install Ubuntu.

---

### Post by darkod on 2010-02-16
> **snake_eyes said:**
> In my case I have Fujitsu Simens server with RAID, I'm not planing to use the server with multiple boot (Windows and Linux), I wanna use it only for Ubuntu.

I'm using this server since 2 years when we (In the department) testing it, now I wanna format it in order to setup the RAID, I didn't touch any server before even I didn't try to prepare any instance with RAID.

In my case also I 6 HD I should when the server is up, when I remove any hardisk shouldn't make any disaster, my question is when I run the simens bootable disk in order to setup the raid, after preperation is the setup will be removed during the Ubuntu installation? please note that I'm using the "use entire disk" option in order to install Ubuntu.

I don't have much experience with linux servers too, but for a server it would be logical to have dedicated RAID controller (and not the simulations of RAID desktop motherboard have in their BIOS).
In this case the correct way is probably to use your RAID controller setup function / setup cd, to set it as what ever type of RAID you want. That will create the raid array as single device.
Then when you start the install with the ubuntu alternate cd (or the ubuntu server cd), it will either see it as single device right away, so you just use the guided setup option(s), or it might ask you something like "RAID devices detected, do you want to turn them on?". Say Yes and then it should see it as single device so you just continue with guided install.

Anyway, play with it, best way to learn. :)

---

### Post by snake_eyes on 2010-02-16
> **darkod said:**
> 
Anyway, play with it, best way to learn. :)

this is the best answer ;), anyway thank you a lot dear...

---

