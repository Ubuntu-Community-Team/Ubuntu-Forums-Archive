---
title: "After installing 12.04 laptop says &quot;Operating System Missing&quot;!"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by lonestranger on 2013-06-05
Hi there.  I tried to install 12.04 to my usb drive.  Tried to be very careful not to do any damage to my hard drive (since I bricked a computer already!), and all seemed to be going well during the install, except that the ubuntu install screen stayed frozen for way too long.  I forced it to quit, and when I tried to turn my machine on again it simply says "Operating System Missing".  Wow.  Operating system was vista.

I respectfully would request help from anyone on this forum.  I'm sure you need more information, but that's the basic story.

Lonestranger

---

### Post by vadimkolchev on 2013-06-05
Well, the only thing I can think off is that you accidentally confuseddribes during the installation. Could it be that you installed ubuntu on your usb drive and your bootloader to your main drive?  Check the contents of your usb drive to see if ubuntu is there. try to boot from it by connecting it and coosing it in your bios or quick load menu.

---

### Post by lonestranger on 2013-06-05
I was careful to install the bootloader onto the usb.  The part where I got unsure is the funky message at the end that says "you didn't assign any swap space.  nothing may work right if you don't assign swap space."  So, I assigned one of the sda partitions to swap.  The usb is completely blank.

---

### Post by fantab on 2013-06-06
> **lonestranger said:**
> I was careful to install the bootloader onto the usb.  The part where I got unsure is the funky message at the end that says "you didn't assign any swap space.  nothing may work right if you don't assign swap space."  So, I assigned one of the sda partitions to swap.  The usb is completely blank.

Ideally SWAP should be where Ubuntu / is, in your case USB.

Boot with the live Ubuntu DVD/USB and post the output of:

```
sudo fdisk -l
```

---

### Post by vadimkolchev on 2013-06-06
> **lonestranger said:**
> I was careful to install the bootloader onto the usb.  The part where I got unsure is the funky message at the end that says "you didn't assign any swap space.  nothing may work right if you don't assign swap space."  So, I assigned one of the sda partitions to swap.  The usb is completely blank.

One of the sda partitions? Are you sure this was not a partition with vista? If you installed on usb, it should have been sdb, sdc, sdd or anything else, but no sda. Sda here represents your internal hard drive. And if usb is completely blank, it is not a good sign.

---

### Post by lonestranger on 2013-06-06
Oh bother!  Sounds like I swapped all over my hard drive!  In a few minutes I'll post about the fdisk command...

---

### Post by lonestranger on 2013-06-06
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x332acbfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    44046335    22022144   27  Hidden NTFS WinRE
/dev/sda2   *    44046336   625140399   290547032   82  Linux swap / Solaris

Disk /dev/mmcblk0: 3904 MB, 3904897024 bytes
100 heads, 35 sectors/track, 2179 cylinders, total 7626752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1            8192     7626751     3809280    b  W95 FAT32

---

### Post by vadimkolchev on 2013-06-06
Sorry to say it, pal, but you seem to have substituted your vista partition with swap.

> Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    44046335    22022144   27  Hidden NTFS WinRE
/dev/sda2   *    44046336   625140399   290547032   82  Linux swap / Solaris

---

### Post by lonestranger on 2013-06-06
Boy I can think of better ways to design the install than ubuntu is now using, but what to do?  All I want to do is get as much data off the computer as possible.  How can I recover windows files from ubuntu live DVD?

---

### Post by Mark Phelps on 2013-06-06
> **lonestranger said:**
> Boy I can think of better ways to design the install than ubuntu is now using, but what to do?  All I want to do is get as much data off the computer as possible.  How can I recover windows files from ubuntu live DVD?

Probably not well, if at all.  Some folks have had success using TestDisk -- but my own personal experience has been otherwise.

If you can connect the hard drive to an existing Windows PC, and you're willing to spend some money, then read through the details below:

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

