---
title: "Placing /home &amp; / var on Seperate Harddrives"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by HoodedHooligan on 2012-06-21
This is a complicated question (at least for myself) as well as an learning experience. Here's the issue:

I have a SSD with Windows 7 and I want to dualboot with 12.04. I bought a couple of 1 TB harddrives to place extra files and such. I want /home to have its own HDD and same with /var (because /var is where all the applications are installed, right?) but I have never done a manual installation before.

I'll take any links or suggestions offered but my skill level is very low and I want to get this done as soon as possible for work related reasons.

---

### Post by rukiaEnix on 2012-06-21
Do you mean the manual option installation that comes with Ubuntu installer?

---

### Post by oldfred on 2012-06-21
You can put partitions on any drive you want.

But I prefer to have at least one fully bootable operating system on each drive and have data on other drives. 

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive. Now two 25GB  / (root) partitions on SSD which will alternate working and testing install.

Program files in Linux are not large (unless you install some games) and you can split the hidden user files in /home that are required by system from data that is optional. Then the system can be fully bootable on SSD but all data is on rotating drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by HoodedHooligan on 2012-06-21
Yes I am going to use the normal Ubuntu installer. I hear that it is better to use the "Try Ubuntu Desktop" feature first to use gparted but I leave that up to suggestion.

I am a gamer so there will be a lot of games installed plus I do video/music production and game development so I am constantly downloading new applications and games, that's why I want to take /var off the SSD and put it own its own drive. I don't mind putting /var and /home on the save drive since I can use the last drive as the storage drive for files that I use between Windows and Ubuntu.

---

### Post by HoodedHooligan on 2012-06-21
@oldfred -> the links all are about moving your /home to a new drive but I am doing a new installation so these don't really relate to me (or at least I don't see how). Also none of these talk about moving /var. 

This is what I know so far:
 - /root, /swap and /boot will be on the SSD
 - /home and /var will be on the HDDS

What I don't know:
 - What are the types of partition (primary, etc.)
 - The order of partitions
 - the size that each partition needs to be, etc.

---

### Post by jmate24 on 2012-06-21
so use the alternate install disk. and then partition a /root and swap on the ssd then format and place the /home partition on one 1TB hdd then don't format the other until you are able to install the exFAT (after you finish installing Ubuntu so your large files that are larger than 4GB can be saved and shared) between windows 7 and Ubuntu. When you have booted into your Ubuntu system then go here [http://www.http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm]("http://www.http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm") and follow the instructions to format the 2nd 1TB into exFAT. that should solve your problem. 

P.S. it may not be a bad idea to get a 500GB - 1TB drive for your /var partition be for you start.
P.S.S. First format the 2nd or 3rd 1TB to exFAT in Windows 7.

---

### Post by oldfred on 2012-06-21
You do not need a separate /boot and should not put swap on SSD. So SSD only has / (root). If you format in advance, then in the installer you just choose which partitions to use for what and which format you want. If you want want /var and /home on rotating drive just specify those partitions during install.

If only installing Linux not Windows you can use gpt partitioning as recommended by the Arch site. But have to have a bios_grub partition 1MB unformated just for grub2 to install core.img.

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by HoodedHooligan on 2012-06-25
I found this guide that gives a visual reference:

[www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partition-guide/](www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partition-guide/)

I gonna call this solved. Quick question tho, why should /root be the only one on the SSD. I put /swap and /boot on there too and put /home and /var on their own drives.

---

### Post by oldfred on 2012-06-25
Most desktops do not need a separate /boot. It ends up wasting space as you now have to allocated extra room in two partitions where the extra space could be shared. It also makes repairs slightly more difficult as you have to also mount the /boot which many instructions forget to tell you or only have a footnote that gets skipped.

A few old BIOS only let you boot from the first 137GB, and grub did not boot from RAID or LVM. Grub2 now can so even servers may not have to have a separate /boot but often do.

Many with lots of RAM do not have swap at all or use a swap file. I just put some swap on my rotating drive, just in case I happen to load too much, but rarely see swap used with my 4GB of RAM.

---

