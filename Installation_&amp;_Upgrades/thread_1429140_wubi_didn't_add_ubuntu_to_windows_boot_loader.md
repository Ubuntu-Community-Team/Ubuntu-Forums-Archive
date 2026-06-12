---
title: "wubi didn't add ubuntu to windows boot loader"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by beast099 on 2010-03-13
i used wubi 9.10 to install ubuntu 9.10 on one of my hard drive partitions but when i boot up, ubuntu does not appear in the windows boot loader.  

im running windows 7 on a dell pc.  i tried using easyBCD 2.0 to try to put ubuntu into the MBR but i can't get it to work.  

i've also tried formatting the partition and reinstalling ubuntu with wubi but encountered the same problem.

---

### Post by drs305 on 2010-03-13
beast099, 

Welcome to Ubuntu and the Ubuntu forums.

Putting aside wubi for the time being, if you didn't see Ubuntu *before* you tried using Easy BCD normally following an Ubuntu installation it is the *Windows* entry that is placed in the *Ubuntu* bootloader (GRUB) menu. 

If they are on different drives, it's possible that the BIOS is booting directly to the Windows drive and reading the Windows bootloader without ever seeing Ubuntu. If they are on the same drive, it's possible that Ubuntu or Grub didn't get fully installed.

I'm not familiar with the workings of EasyBCD so I can't comment on the results after you used that app. Don't worry though, others on this forum are familiar with it. 

In any case, there are several items of information we need to make recommendations, so if you will run meierfra.'s [boot info script]("http://bootinfoscript.sourceforge.net/") and then post the results we can take a look. When you are ready to copy the results, please click the # icon in the post's menu area and paste the results between the resulting code tags.

---

### Post by beast099 on 2010-03-13
im sorry but i don't know how to run that boot file in windows and i cannot boot up ubuntu because i don't know how to boot it if it doesn't show up on the windows boot loader

---

### Post by garvinrick4 on 2010-03-13
wubi is not installed in a partition it is installed in a folder in Windows C: drive right next
to Users. To install you just put CD in tray and when it comes up click on wubi and it then asks you how big to make folder up to 30 gig I believe and asks for password and then you say go and that is it.
 To do a install you have to partition by booting off of CD and choosing install then it will go to gparted and partition for you or if you choose manual can partition exactly how you want. 
 Installing is not a tough process, Ubuntu makes it do just about everything for you except kiss you good night. 
 If you need to know something, Google it, Google it, Google it.

---

### Post by lomah on 2010-03-14
Hello,
I'm brand new to Ubuntu and this forum, so please bear with me.
I, too, have the same isue after installing Wubi in a Windows 7 environment.
My Windows OS is installed on my first drive (Disk 0), as I use my second drive (Disk 1)as a backup drive.  This is because I have recently installed a new drive, on which I installed Windows 7.
My first drive (Disk 0) contains 3 partitions:
F: Windows 7
G: Windows Vista
H: Ubuntu (not necessary, I know, but I wanted Ubuntu in it's own partition)

My second drive (Disk 1) contains 2 partitions:
D: Recovery
C: Backup

I installed Wubi to drive H:, but it doesn't appear as a boot option.
I notice that both drive C: and drive F: contain:
wubildr
wubildr.mbr

and drive G: contains:
bootmgr

---

### Post by garvinrick4 on 2010-03-14
Do this code and post to thread Code:
                                           sudo fdisk -l   (that is small L)

---

### Post by beast099 on 2010-03-14
sudo fdisk -l results

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9b60b42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        7338    58846095    7  HPFS/NTFS
/dev/sda3            7339       13886    52589844    7  HPFS/NTFS
/dev/sda4           13887       14593     5678977+   5  Extended

i ran this from the ubuntu an 10.9 instillation disk so i dont know if that will make a difference.

---

### Post by beast099 on 2010-03-14
i think i figured out what the proplem was.  i fell a little stupid for not noticing it before but wubi keep install the 64 bit version of ubuntu and i have a 32 bit machine.  

so the question now is how do i get wubi to install the 32 bit version of ubuntu instead of the 64 bit version

---

### Post by Mark Phelps on 2010-03-14
> **beast099 said:**
> ... i tried using easyBCD 2.0 to try to put ubuntu into the MBR but i can't get it to work...

EasyBCD does not mess with the MBR -- unless you go into a Advanced screen and specifically tell it to do so.

What it does is add an entry to the Vista/WIN7 BCD for the new OS, and install GRUB4DOS in an MS Windows partition.

Don't know what version of EasyBCD you're using, but the latest is V2 Beta build 82.

If you want to use the Win7 Bootloader to boot both Win7 and Ubuntu, you need to go to the NeoSmart Technology forums.  They have tutorials and how-to's dealing with doing that.

If you want to use GRUB to select either Win7 or Ubuntu, quit messing around with EasyBCD -- you'll just hose up your Win7 boot loader.

---

