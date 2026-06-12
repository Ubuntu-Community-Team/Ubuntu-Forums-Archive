---
title: "Replacing Fedora with Ubuntu on dual boot"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by atac57 on 2012-03-14
I currently have Fedora 13 and Windows 7 set up as a dual boot. I want to replace the Fedora partition with Ubuntu, but keep Windows 7 as it is now. I have Ubuntu burnt to a CD, so would I install it in Windows? I would also need to backup my stuff in Fedora to maybe an external hard-drive, correct?

---

### Post by zvacet on 2012-03-17
First back up your files from Fedora to external dive ( as you mention ).After that you can run from Fedora 

```
fdisk -l
```

to be sure on witch partition Fedora is.Then boot Ubuntu CD and on partitioning stage **use something else** and you will be able to install Ubuntu on partition where Fedora was.

---

### Post by atac57 on 2012-03-19
Ok, so my plan is to boot from the Ubuntu CD. The first hard drive is from my old Dell, which had Windows XP. The second hard drive is where Fedora and Windows 7 are installed, would I need to install Ubuntu on sdb5 and sdb6 since those are the Linux partitions?

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8159    65537136    7  HPFS/NTFS
/dev/sda2            8160       19451    90702990    f  W95 Ext'd (LBA)
/dev/sda5            8160       16318    65537136    7  HPFS/NTFS
/dev/sda6           16319       19123    22531131    7  HPFS/NTFS
/dev/sda7           19124       19451     2634628+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00081b63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       12158    97552384    7  HPFS/NTFS
/dev/sdb3           12158      121602   879105025    5  Extended
/dev/sdb5           12158       13617    11717632   83  Linux
/dev/sdb6           13617      120604   859373568   83  Linux
/dev/sdb7          120604      121602     8011776   82  Linux swap / Solaris

---

### Post by atac57 on 2012-03-20
Can someone tell me what Error 17 is? I deleted the two Fedora partitions, to add the Ubuntu ones which I set the smaller one as "/" and the bigger one as "/home" and checked format for both of them. After installing Ubuntu, I rebooted and no operating system comes up, just Error 17. I tried it twice and the same thing happened. I can still get into the BIOS though.

---

### Post by coffeecat on 2012-03-20
Error 17 is an error message from legacy grub. There must still be residual legacy grub code from Fedora in the mbr of whichever hard drive you are booting from. Which means in turn that Ubuntu's grub2 was not installed to the mbr. Did you install it to a partition?

We need to get a complete overview of your system. Boot up the live Ubuntu CD, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Also - which of your hard-drives, sda/160GB or sdb/1000GB, is your BIOS set to boot from?

---

### Post by atac57 on 2012-03-20
Ok, in the terminal I put "sudo bash ~/Desktop/boot_info_script.sh" and it said "No such file or directory." I tried it a few times, nothing. As far as what hard drive the BIOS boots from, that would be the sdb/1000GB. 

Also I did some searching and could that error be from the partition table entries being out of order? When I do sudo fdisk -l, at the very end it says "Partition table entries are not in disk order."

---

### Post by oldfred on 2012-03-20
Partitions not in order is not an issue.

Two more ways to run boot info script. But you should have it in whatever folder you downloaded it to and can run it from there. Note that Linux is case sensitive and you do not have a Desktop but do have a desktop. Often downloads are now to downloads folder not desktop.

The git/testing version has some fixes and is still being updated. Works better for efi or grub 1.99 based systems:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by atac57 on 2012-03-20
> **oldfred said:**
> Partitions not in order is not an issue.

Two more ways to run boot info script. But you should have it in whatever folder you downloaded it to and can run it from there. Note that Linux is case sensitive and you do not have a Desktop but do have a desktop. Often downloads are now to downloads folder not desktop.

The git/testing version has some fixes and is still being updated. Works better for efi or grub 1.99 based systems:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.I'm not sure what you mean about whatever folder I downloaded it to, I wasn't aware I downloaded anything because I'm using the "Try Ubuntu" option off the Ubuntu CD I burned. If I try to boot from the hard drive I get the Error 17. The downloads folder is empty and the desktop only has an "Examples" folder and an "Install Ubuntu 11.10" icon. Am I not understanding something?

---

### Post by atac57 on 2012-03-21
Ok, I figured it out! On the "Device for boot loader installation" option, I put that to the sdb drive which is the drive I was installing Ubuntu on, I had put it on the sda drive previously. My friend told me that wouldn't matter with Linux, but he figured different BIOS implementations have different quirks. Thanks for your help guys!

---

