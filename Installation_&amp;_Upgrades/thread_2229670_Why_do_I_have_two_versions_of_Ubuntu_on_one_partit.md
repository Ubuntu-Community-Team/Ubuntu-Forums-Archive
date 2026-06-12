---
title: "Why do I have two versions of Ubuntu on one partition?"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by justin53 on 2014-06-14
tl;dr: I currently have 12.10 and 14.04 on the same partition, but I only want 14.04

I originally just had Windows 7 on my computer, but a while back I created a new partition and installed Ubuntu 12.10. At some point, I tried repeatedly to install Matlab, but something got screwed up and Ubuntu was always kind of weird after that. I never did get Matlab working on Ubuntu, but it wasn't a big deal since I had it on Windows. 
Fast-forward to today. I burned a disc of Ubuntu 14.04 and during the installation I formatted the old Ubuntu partition and turned it into swap space. Then I created a new partition from the Windows partition and installed 14.04. When it finally booted up, I saw my old Ubuntu background and 12.10 at the bottom of the screen. After restarting, I have found that at startup I have the choice of loading either 12.10 or 14.04. When I look at my hard drive, I only have four partitions: Windows recovery, Windows 7, swap space, and Ubuntu. So both versions must be on the same partition, right?
What did I do wrong and how do I remove 12.10 and replace it with 14.04? I thought I had axed 12.10 when I turned that partition into swap space.

---

### Post by ajgreeny on 2014-06-14
Let's check what you really have on the disk rather than what you think you have, as you can't have more than one version of ubuntu on a single partition.

Can you show the output in terminal of command ```
sudo fdisk -l
```I suspect that after attempting to use the old partition as swap without deleting it or its contents first, you may still have everything on that partition that was there previously, but I am a bit baffled about where your new 14.04 has gone.

Can you boot into your ubuntu (I assume you only have one in the grub menu)and again show the outputy of command ```
lsb_release -dc && echo "Desktop:    $DESKTOP_SESSION" && uname -mrn
```If you have more than one ubuntu version in grub please boot to both and run that last command in both OSs.

Let's also see the output of ```
free
```to see if you actually have a working swap partition in both OSs

---

### Post by justin53 on 2014-06-14
OK, I'm in 14.04 right now. The output of fdisk is:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b92b11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2459647     1228800    7  HPFS/NTFS/exFAT
/dev/sda2         2459648   874069022   435804687+   7  HPFS/NTFS/exFAT
/dev/sda3       952195072   976771071    12288000   82  Linux swap / Solaris
/dev/sda4       874070014   952195071    39062529    5  Extended
/dev/sda5       874070016   952195071    39062528   83  Linux

Partition table entries are not in disk order
```

The output of lsb_release is:
```
Description:    Ubuntu 14.04 LTS
Codename:    trusty
Desktop:    ubuntu
justin-ThinkPad-E520 3.13.0-24-generic x86_64

```

And the output of free is:
```
             total       used       free     shared    buffers     cached
Mem:       3956612    1835924    2120688     183052      36396     905816
-/+ buffers/cache:     893712    3062900
Swap:     12287996          0   12287996

```

---

### Post by justin53 on 2014-06-14
OK, I'm in [s]12.10[/s] 13.10 (I guess I was wrong on that one). Here is the output of lsb_release:
```
Description:    Ubuntu 13.10
Codename:    saucy
Desktop:    ubuntu
ubuntu 3.11.0-23-generic x86_64


```

and the output of free is:
```
             total       used       free     shared    buffers     cached
Mem:       3956940    2812796    1144144          0     980868    1170620
-/+ buffers/cache:     661308    3295632
Swap:       262140          0     262140


```

---

### Post by grahammechanical on 2014-06-14
Could you also run from both Ubuntus

```
df -h
```

This is what I see when I run that command from one of my Ubuntu installations

> Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb8        35G  8.7G   24G  27% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            486M  4.0K  486M   1% /dev
tmpfs           100M  1.3M   98M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            497M   13M  484M   3% /run/shm
none            100M   60K  100M   1% /run/user

It shows that the Ubuntu I am running that command from is on sdb8 - partition 8 on the second sata hard drive. I have a question. How did you install Ubuntu 13.10? did you use Wubi.exe and install it inside Windows 7? I am just making wild guesses.

---

### Post by justin53 on 2014-06-16
From 14.04, I'm getting:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        37G  5.2G   30G  15% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G   12K  1.9G   1% /dev
tmpfs           387M  1.1M  386M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  268K  1.9G   1% /run/shm
none            100M   60K  100M   1% /run/user


```

---

### Post by justin53 on 2014-06-16
and in 13.10, I'm getting:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   14G  3.3G  81% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           387M  1.1M  386M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  152K  1.9G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda2       416G  247G  169G  60% /host
/dev/sda1       1.2G  331M  870M  28% /media/justin/SYSTEM_DRV


```

---

### Post by steeldriver on 2014-06-16
So I would guess your original 13.10 system is a wubi install inside the Windows system

---

### Post by justin53 on 2014-06-16
> **steeldriver said:**
> So I would guess your original 13.10 system is a wubi install inside the Windows system

I'm not sure. When I installed it, I booted from the cd and inserted a separate partition for the install. That 13.10 partition is now formatted and being used for swap space.

If I can't delete the 13.10 install, can I at least remove it from the grub screen? When I select Ubuntu at startup, I'd like it to go straight to 14.04.

---

### Post by coffeecat on 2014-06-16
> **justin53 said:**
> I'm not sure. When I installed it, I booted from the cd and inserted a separate partition for the install. That 13.10 partition is now formatted and being used for swap space.

No, you did not and do not have a separate 13.10 partition. The output you posted in post #7 is unequivocal. Your 13.10 is a wubi system inside your Windows partition, sda2.

---

### Post by justin53 on 2014-06-16
> **coffeecat said:**
> No, you did not and do not have a separate 13.10 partition. The output you posted in post #7 is unequivocal. Your 13.10 is a wubi system inside your Windows partition, sda2.

Well, it was on sda3 when I installed 14.04. It looked like a separate partition to me, but I'm just a novice. 


At any rate, how do I remove 13.10?

---

### Post by oldfred on 2014-06-16
Back up or copy any data in wubi that you may want in your partitioned install.

It should be just like any Windows software that you uninstall. 
If you have to manually uninstall, you can just delete root.disk and edit BCD to remove the wubi entry.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by justin53 on 2014-06-17
> **oldfred said:**
> Back up or copy any data in wubi that you may want in your partitioned install.

It should be just like any Windows software that you uninstall. 
If you have to manually uninstall, you can just delete root.disk and edit BCD to remove the wubi entry.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I uninstalled "Ubuntu" from the control panel in Windows and now I can't access any of my Ubuntu installations. What happened? At startup, I used to have the option of Windows 7 and Ubuntu, but now it just goes straight into Windows. 
The program uninstalled so quickly that I don't think it deleted anything from my installations. Is there a way to get it back? I tried the system restore tool in Windows, but that was useless.

---

### Post by oldfred on 2014-06-17
With wubi you boot with the Windows boot loader in the MBR. And the BCD or boot.ini shows both Windows and Ubuntu.
With a full partitioned install, you install grub to the MBR and grub's menu has both Windows and Ubuntu as boot options.
It sounds like you have the Windows boot loader in the MBR and need to install the Ubuntu/grub boot loader.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

