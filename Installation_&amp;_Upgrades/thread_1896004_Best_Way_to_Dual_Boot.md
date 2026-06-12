---
title: "Best Way to Dual Boot?"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by martin11ph on 2011-12-16
In relation to my thread at [http://ubuntuforums.org/showthread.php?t=1895592](http://ubuntuforums.org/showthread.php?t=1895592) , I am planning to reformat all my drives in hopes of solving the problem. Before I do so, I would like to ask what would be the best way to accomplish this. 

I will be installing:
1. Ubuntu 9.1 and upgrade it
2. Windows 7 Ultimate 64-bit

on a HP Pavilion dv7-4190us laptop with 2 physical drives at 500GB each. Please advise me as to:
1. What should I install first?
2. Where should I install each? (the automatic install of Ubuntu did not allow me to install it on same drive as Windows)

Thanks a lot and hope I gave everything needed.

---

### Post by fantab on 2011-12-16
> **martin11ph said:**
> I will be installing:
1. Ubuntu 9.1 and upgrade it
2. Windows 7 Ultimate 64-bit

on a HP Pavilion dv7-4190us laptop with 2 physical drives at 500GB each. Please advise me as to:
1. What should I install first?
2. Where should I install each? (the automatic install of Ubuntu did not allow me to install it on same drive as Windows)

First of all don't UPGRADE, instead download latest Ubuntu 11.10 and install. Upgrades are never without issues and are messy more often than not. If it is not too much, ALWAYS use MANUAL option when partitioning or Installing.


[LIST=1]
[*]Install WINDOWS FIRST on /dev/sda1 about 25-30GB. Create other NTFS partitions according to your needs.
[*]Install UBUNTU on the /dev/sdb1 - 15-20GB ext4 /, and go on to partition as per your need. Personally, I would advice you to not create a /home partition instead have a huge Linux ext4 partition to save your DATA which you mount manually or automount later. The advantage is in case something goes wrong you don't have to worry about losing your data. Also this scheme will help in future when you have to upgrade to a newer version of Ubuntu.
[/LIST]
**Install GRUB on /dev/sdb ONLY** and **set your BIOS to boot /dev/sdb first.**

---

### Post by martin11ph on 2011-12-16
> **fantab said:**
> **Install GRUB on /dev/sdb ONLY** and **set your BIOS to boot /dev/sdb first.**

Good day. Thank you for the information you shared. I will have a problem with this part. This is also the reason for the other thread mentioned earlier. My BIOS does not allow me to select which of the physical drives to boot first. It seems to boot sda always.

Edit:
Downloading Ubuntu 11.10 64-bit now.

---

### Post by fantab on 2011-12-16
> **martin11ph said:**
> Good day. Thank you for the information you shared. I will have a problem with this part. This is also the reason for the other thread mentioned earlier. My BIOS does not allow me to select which of the physical drives to boot first. It seems to boot sda always.

Edit:
Downloading Ubuntu 11.10 64-bit now.

In that case Install Windows first and when installing Ubuntu install GRUB to /dev/sda ONLY. Also check what kind of Partition table you are using. Use DOS/MSDOS and not GPT since you will be dual booting with Windows. Also GPT is recommended for HDD more than 2TB.

Or What you can do is Install Windows and Ubuntu to the same HDD


[LIST]
[*]/dev/sda1 - NTFS - 25-30GB Primary Win7- Primary
[*]/dev/sda2- NTFS - Data - Primary
[*]/dev/sda3- Ext4 -  15-20GB Ubuntu / - Primary
[*]/dev/sda4- SWAP- 2-4GB - Primary
[/LIST]
And you can use the entire second HDD /dev/sdb as /dev/sdb1 - Linux ext4- Data Partition- Primary.

For Partitioning and other HDD management use **[Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php")**, as it partitions the HDD at boot it safer than other methods.

---

### Post by Mark Phelps on 2011-12-16
My recommendation is to connect only one drive at a time -- and do the complete OS install to that drive -- one drive for each OS.

Then, when done, connect your Ubuntu drive to be the boot drive, boot into it, open a terminal and enter "sudo update-grub".  That will regenerate the GRUB menu.  After that, you should see a menu and be able to select your OS.

---

### Post by oldfred on 2011-12-16
I prefer each system on each drive like fantab's first suggestion and Mark Phelps suggestion.

How old is system? Only older IDE systems booted from primary master. All new SATA based systems do have BIOS settings to set boot drive, but some are not obvious. Some BIOS have it under the boot device selection as a second menu under hard drive, others have it as a total different entry sometimes even on a different BIOS page.

If you can only boot from one system then with Mark Phelps suggestion you will have to install grub to sda after reconnecting the Windows drive. Make sure that the Windows drive stays as sda & Ubuntu is sdb. Often the order plugged into system ports.

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

You may need liveCD to install grub2's boot loader to sda if you disconnect drives. 
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

