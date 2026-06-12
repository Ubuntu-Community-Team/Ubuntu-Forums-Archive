---
title: "how to remove ubuntu 11.10 from dual boot win XP with out win XP CD?"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by gokulsurendiran on 2012-06-08
Hi all,

I'm using windows xp & ubuntu 11.10 dual boot. I wanted to remove ubuntu and i don't have windows cd.

Even if XP is crashed I don't mind, i just wanted to get rid of Ubuntu.

Thanks,
Gokul

---

### Post by wilee-nilee on 2012-06-08
If this is a dual boot and you are getting the grub menu, you can install a bootloader that will boot XP direct so you can remove Ubuntu, it is called lilo.

Here are the commands, make sure you have the HD correct by running this first command and subbing the correct letter for the X in the two lilo commands, no partitions it will be sda, or sdb...etc.

From a live ubuntu cd .
```

sudo fdisk -l
```Commands for install of the lilo bootloader, untick the cd in software sources and make sure the universal repo is marked and run a update of the cd then follow these commands inserting the HD letter for the X.
                                  ```
sudo apt-get install lilo
``` ```
sudo lilo -M /dev/sdX mbr 
``` [FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR [/SIZE][/FONT]

---

### Post by gokulsurendiran on 2012-06-10
> **wilee-nilee said:**
> If this is a dual boot and you are getting the grub menu, you can install a bootloader that will boot XP direct so you can remove Ubuntu, it is called lilo.

Here are the commands, make sure you have the HD correct by running this first command and subbing the correct letter for the X in the two lilo commands, no partitions it will be sda, or sdb...etc.

From a live ubuntu cd .
```

sudo fdisk -l
```Commands for install of the lilo bootloader, untick the cd in software sources and make sure the universal repo is marked and run a update of the cd then follow these commands inserting the HD letter for the X.
                                  ```
sudo apt-get install lilo
``` ```
sudo lilo -M /dev/sdX mbr 
``` [FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR [/SIZE][/FONT]

Hi, thanks for the reply.

this is the reply for 1st command,

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS/exFAT
/dev/sda2        40965811   312580095   135807142+   f  W95 Ext'd (LBA)
/dev/sda5        40965813    83194310    21114249    7  HPFS/NTFS/exFAT
/dev/sda6       120840993   160737817    19948412+   7  HPFS/NTFS/exFAT
/dev/sda7       202756428   255117433    26180503    7  HPFS/NTFS/exFAT
/dev/sda8       255119360   310118399    27499520   83  Linux
/dev/sda9       310120448   312580095     1229824   82  Linux swap / Solaris
/dev/sda10       83200698   120840929    18820116    7  HPFS/NTFS/exFAT
/dev/sda11      160746453   202756364    21004956    7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

is everything fine, should I sub 'a' in place of X.

reply for 2nd command

<sudo apt-get install lilo>

It seems to be your first LILO installation. It is absolutely necessary   &#9474;  
 &#9474; to run liloconfig(8) when you complete this process and execute           &#9474;  
 &#9474; /sbin/lilo after this.

how do I do this?

Thanks,
Gokul

---

### Post by wilee-nilee on 2012-06-10
> **gokulsurendiran said:**
> Hi, thanks for the reply.

this is the reply for 1st command,

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS/exFAT
/dev/sda2        40965811   312580095   135807142+   f  W95 Ext'd (LBA)
/dev/sda5        40965813    83194310    21114249    7  HPFS/NTFS/exFAT
/dev/sda6       120840993   160737817    19948412+   7  HPFS/NTFS/exFAT
/dev/sda7       202756428   255117433    26180503    7  HPFS/NTFS/exFAT
/dev/sda8       255119360   310118399    27499520   83  Linux
/dev/sda9       310120448   312580095     1229824   82  Linux swap / Solaris
/dev/sda10       83200698   120840929    18820116    7  HPFS/NTFS/exFAT
/dev/sda11      160746453   202756364    21004956    7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

is everything fine, should I sub 'a' in place of X.

reply for 2nd command

<sudo apt-get install lilo>

It seems to be your first LILO installation. It is absolutely necessary   &#9474;  
 &#9474; to run liloconfig(8) when you complete this process and execute           &#9474;  
 &#9474; /sbin/lilo after this.

how do I do this?

Thanks,
Gokul

Did you notice this?
[FONT=Verdana, sans-serif][SIZE=1]**May show error messages about the rest of lilo missing, ignore, we just want MBR.**

Just run both lilo commands and sub an a for the X
[/SIZE][/FONT]

---

### Post by mastablasta on 2012-06-11
wouldn't it be easier to simply download official windows XP restore disk and use it to restore master boot record. you can't install windows with it but you can "fix it" i believe.
 
you could install recovery console in existing os: [http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
or maybe with service pack disk: [http://support.microsoft.com/kb/322389](http://support.microsoft.com/kb/322389)

---

### Post by wilee-nilee on 2012-06-11
> **mastablasta said:**
> wouldn't it be easier to simply download official windows XP restore disk and use it to restore master boot record. you can't install windows with it but you can "fix it" i believe.
 
you could install recovery console in existing os: [http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
or maybe with service pack disk: [http://support.microsoft.com/kb/322389](http://support.microsoft.com/kb/322389)

Not sure any of that is possible or easy.

If you have an exacting answer that would be great. ;)

Lilo is what is always suggested on the forum by people who work in this area.

Lilo is two commands and a done deal.

I will add as well I would rather a user had the MS bootloader, but lilo works every time, so it is the option here as far as I know, under these circumstances.

---

### Post by gokulsurendiran on 2012-06-11
ran the lilo command,


Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

restarted the system! it worked!

Thanks a ton!

Just out of curiosity, is the ubuntu removed or is hidden?
is it possible to load through ubuntu?

---

### Post by black veils on 2012-06-12
did you backup all your data, even in the windows system?  you might make a mistake when removing ubuntu, and lose the files.

you should boot the ubuntu live cd/usb, choose **Try** to load the desktop.

open **gparted**. from the list of partitions, check if there is a key symbol to the left of them, if there is, right-click, choose **unmount** (or **swap-off** for swap).

select and right-click a linux partition, choose **delete**, then **apply**. wait, repeat for the other linux partitions.

make sure you are not deleting anything for windows or another linux system you want to keep!

after that, run those lilo commands again.

---

### Post by gokulsurendiran on 2012-06-13
> **black veils said:**
> did you backup all your data, even in the windows system?  you might make a mistake when removing ubuntu, and lose the files.

you should boot the ubuntu live cd/usb, choose **Try** to load the desktop.

open **gparted**. from the list of partitions, check if there is a key symbol to the left of them, if there is, right-click, choose **unmount** (or **swap-off** for swap).

select and right-click a linux partition, choose **delete**, then **apply**. wait, repeat for the other linux partitions.

make sure you are not deleting anything for windows or another linux system you want to keep!

after that, run those lilo commands again.

Hi, thanks for the advice, but i hv already removed ubuntu atleast from the boot menu!

---

### Post by presence1960 on 2012-06-13
> **wilee-nilee said:**
> Not sure any of that is possible or easy.

If you have an exacting answer that would be great. ;)

Lilo is what is always suggested on the forum by people who work in this area.

Lilo is two commands and a done deal.

I will add as well I would rather a user had the MS bootloader, but lilo works every time, so it is the option here as far as I know, under these circumstances.

Lilo works perfectly for resetting MBR to windows. A couple commands from the terminal and then reboot and you are set. Definitely way better than booting a CD.

---

### Post by choganj on 2012-09-21
It has nothing to do with lost Win XP CD as you can simply uninstall Ubuntu from Add/Remove of XP, if you installed Ubuntu into XP.

If you installed it along with XP on another partition, then you can simply format that partition.

In the end you will have to modify your Boot.ini file to remove Ubuntu from boot menu as well.

You may also visit [http://www.techyv.com/questions/problem-after-deinstalling-ubuntu](http://www.techyv.com/questions/problem-after-deinstalling-ubuntu) for more information.

I hope it would be of some help.

---

