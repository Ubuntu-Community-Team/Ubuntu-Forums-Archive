---
title: "Installing on an exsisting Win 7 box with three 3 drive"
date: 2014-11-29
forum: Installation &amp; Upgrades
---

### Post by redwdc on 2014-11-29
Hi,

I have an older (? 2008 with Intel dual core) system with Win 7 (upgraded from Vista), 2 GB RAM and 3 SATA HDDs:

[LIST]
[*]250 GB Win boot drive (I could reformat it but then I'd have to rebuild the Windows system)
[*]500 GB Now blank
[*]2 TB    Win programs and Data (an early xmas present)
[/LIST]
I want to put Ubuntu on the 500 GB drive.  CMOS says it's the 2nd drive if that makes any difference.

So, how should I partition the 500 GB drive?

---

### Post by yancek on 2014-11-29
Well there are numerous options but the simplest if you are inexperienced is to create on 25-30GB partition to put the entire filesystem on and then a 2-4GB swap.  You can then later create additional partitions on which you can store data and access it from either windows or Ubuntu.  You will need to format the partition with some windows filesystem as a default windows install is not capable of writing to or reading a Linux filesystem but a Linux system can do both.  The link below has a lot of useful information on Linux in general and is a tutorial on installing Ubuntu, good to read it before starting.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Impavidus on 2014-11-30
Use manual partitioning (the something else option of the installer). Best to create the partitions beforehand using gparted on the live disk. Make a swap partition 2-4GB in size. You can make the rest into one big root partition or (as many prefer) make a ca. 25GB root partition and use the remainder of the drive for /home or data partitions, or space for an additional Linux install. If you keep enough unallocated space to work with, you can change this later. Your 500GB drive is probably called /dev/sdb, but you have to check that in gparted. In the installer, instruct to install the boot loader on this 500GB drive (/dev/sdb probably), not on a partition like /dev/sdb1 or on a different drive. This will keep the Windows boot loader intact (probably on /dev/sda). Then change the boot order in the bios to the 500GB drive first and you will get a menu to boot either Windows or Ubuntu. If the 500GB drive breaks or if you want to remove Ubuntu, change the boot order back to the Windows drive first and you can boot Windows without using grub (the Ubuntu boot loader).

---

### Post by redwdc on 2014-11-30
Impavidus

Thank you for the reply.

Are there any advantages/disadvantages to a larger swap partition other than wanting to use hibernate or that I will be adding new RAM later.  The same question for the / partition also.

---

### Post by oldfred on 2014-11-30
You actually do not want to use swap. It is overflow for lack of RAM when you load too many applications at once. And is really slow compared to RAM.

I have a dual core laptop from 2006, bought a week before Vista. While it said Vista ready it was a little light on specs for Vista. It has 1.5GB of RAM and runs 64 bit Ubuntu well if not running Unity. I immediately change to fallback/gonme-panel which is more lightweight. But if I try to load more than one larger app and a couple of little ones thens it does get real slow or gray screen, so I know I am using swap.

Most would say your 2GB of RAM is probably better with 32 bit, but you really are on the cusp of which may be better. If planning on adding RAM, I would definitely install the 64 bit version as changing is a new full install, not an upgrade.
Also depending on video system whether Unity will run or not. If adding RAM or have a good video card, I might try Ubuntu with Unity. Otherwise Xubuntu, Lubuntu or fallback/gnome-panel are lighter weight gui that will work with older hardware better.

Applications are in / (root). And your data files are in /home. Your /home can be inside / or a separate partition. I use 25GB for /, and keep /home inside / but have all data in my data partition(s). Most data folders are linked so it is automatically stored elsewhere. My / including /home is about 11GB and 2GB of that is /home. And /home is only that large because of .wine for Picasa which is about 1.5GB.

---

### Post by nerdtron on 2014-11-30
My recommendation for this:

Since you already have a 2Tb drive with all you data on it. Then do a full automated install on the 500 GB drive.
1. Disconnect the 250GB windows drive and the 2TB data drive.
2. Now be sure that only the 500 GB drive is connected, boot the the Ubuntu installer (either DVD or USB).
3. On the Ubuntu installer, start the full installation. I think it's called "Erase everything and Install Ubuntu"

Since the other drives are disconnected, you don't have to risk any data loss or accidental format of data drive.
Also if you mess up Ubuntu installation, just reinstall it and no damage will be done.

---

### Post by redwdc on 2014-11-30
oldfred Thank you for the reply.  That was what I wanted to know.


nerdtron thank you, But wouldn't your suggestion leave me having to install boot management after the fact, so to speck?

---

### Post by oldfred on 2014-11-30
If you only have the one drive installed the auto installer will install grub to that drive's MBR (if BIOS, not UEFI).
Default install is always installing grub to the drive seen as sda.
Only if you have other drives connected must you use Something Else as that is the only install option that gives a choice on which drive to install grub2's boot loader into.

Once booted into Ubuntu and have other drives reconnected run this and it will scan other drives for operating systems and add then to grub menu. All installs must be in same boot mode either BIOS or UEFI. If older hardware with only BIOS then that issue does not apply.
sudo update-grub

You probably will have to go into BIOS and set Ubuntu drive as default boot drive when other drives are connected.

---

### Post by Impavidus on 2014-11-30
Disconnecting the Windows drives is a safe way to make sure you don't wipe your Windows system. It won't give you a correct grub menu though. To fix this after reconnecting the Windows drives, change the boot order to boot from the Ubuntu drive. Then edit the file /etc/default/grub (you'll need root permissions for that) and change the line```
GRUB_TIMEOUT=0
```(I think that's the line) into```
GRUB_TIMEOUT=10
```This will enable the menu and show it for the default of 10 seconds. Then run```
sudo update-grub
```to detect Windows and apply changes.

---

### Post by redwdc on 2014-12-01
Thanks to all,

Mainly I was looking for reasonable partition sizes which I got from oldfred.

I ended up using the manual partitioning tool provided.  Once you've used fdisk this is asy.

---

### Post by redwdc on 2014-12-01
Thanks to all,

Mainly I was looking for reasonable partition sizes which I got from from oldfred.

I ended up using the manual partitioning tool provided, once you've used fdisk this is easy.

---

