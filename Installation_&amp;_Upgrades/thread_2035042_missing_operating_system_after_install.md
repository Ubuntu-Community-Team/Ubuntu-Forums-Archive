---
title: "missing operating system after install"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by aLarM on 2012-07-29
okay heres the problem, about 1 hour ago i began installing the latest ubuntu 64bit version. last night i partitoned my hd and everything for the fresh install when i wake up. so i installed it, restarted the computer as it requested after the install was completed, took the disc out and now every time i try to start the computer it says missing operating system. i currently have windows 7 ultimate 64bit installed on a different partition and ubuntu 12.04 64bit on an ext4 file system, i have already tried repairing windows 7 with the install disc and it fails. also, when i reboot the computer i cant do anything, it just immediately says "missing operating system", theres no grub menu os chooser or anything at all. i went to startup menu on boot, tried booting from both hard drives and they both get "missing operating system" i dont know whats wrong but im guessing its grub, so here is the output for some commands that i know of:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfab0a736

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400   82  Linux swap / Solaris
/dev/sda2          206848   310794239   155293696    7  HPFS/NTFS/exFAT
/dev/sda3       310794240  2825496575  1257351168    7  HPFS/NTFS/exFAT
/dev/sda4      2825496576  2930276351    52389888   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdedadeda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

```
```

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            3.9G   76M  3.8G   2% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  868K  1.6G   1% /run
/dev/sr0        699M  699M     0 100% /cdrom
/dev/loop0      664M  664M     0 100% /rofs
tmpfs           3.9G  8.0K  3.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   80K  3.9G   1% /run/shm

```

any help would be great, im currently on the live cd right now looking for help and will be watching this thread closely. if you need more info or more outputs from terminal please leave the command you need the output for and i will post up the output, also i installed from a burned dvd and i dont have a flash drive.

---

### Post by darkod on 2012-07-29
So, you get the missing operating system message without seeing any grub2 boot menu, right?

First thing to notice is that you seem to have installed ubuntu making /dev/sda1 the swap partition. However, it seems sda1 was the win7 system reserved partition containing the win7 boot files. So even if you can boot ubuntu, you will not be able to boot win7.

On top of that it seems grub2 didn't install properly if you can't see the boot menu. Where did you select to install the grub2 bootloader? Can it be on the other disk?

---

### Post by aLarM on 2012-07-29
well, during installation i chose to install ubuntu on the ext4 partition i made last night, and it asked for swap so yeah i chose sda1 on that, but i didnt get asked anything about grub but i did see it install grub2 during installation, and every start up it goes automatically to missing operating system screen so im guessing grub wasnt installed correctly. and yeah im pretty sure windows boot was removed because of the swap partition i decided to use, i tried doing the repair option on the installation disc but it failed both times i tried it, and it didn't detect the installed windows 7 os system, so i gave up on that for now.
my hard drive setup at the moment is 2 hard drives, one 1tb hd and one 1.5tb hd, the 1tb hd is purely backups, the 1.5tb has a windows 7 partition and ubuntu partition, the rest of the space will be for backups.

---

### Post by darkod on 2012-07-29
1. Boot with the ubuntu cd into live mode and open Gparted, select /dev/sda.
2. The swap partition will be mounted, it will have a keys symbol next to it. Unmount it with right-click, Swapoff. The keys symbol should be gone.
3. Format /dev/sda1 as ntfs and delete /dev/sda4. Click the green button in Gparted to execute the changes.

After that try the win7 repair process again few times. I think it doesn't work because the partition is not ntfs right now.

After win7 is fixed, install ubuntu again but this time don't create the root partition as primary, create two partition as logical. Root and swap, into the unallocated space left after you deleted sda4. When you create them as logical it will allow you to create 2,otherwise you can create only one primary because the maximum is 4 and you already have sda1-sda3.

For the bootloader (the drop down choice is under the partitions list when you are doing the manual partitioning), select only /dev/sda. That will put it on the MBR of the disk.
If you boot from sda you should get the grub2 boot menu at start.

---

### Post by aLarM on 2012-07-29
yeah i kinda figured the repair wouldnt work changing the windows boot partition to a swap area, im in the process of doing what you mention right now. the only problem is i dont get any options to choose between when ubuntu is installing grub2. also, with the unallocated space form the deleted ext4 system i tried creating a new partition from it, it would only let me choose primary or extended. (this is before repairing windows though, not sure if it makes a difference if i do it before repairing or after?) anyway, it just finished changing swap to ntfs and deleteing ext4 partition so i'm going to restart and try to repair windows 7.
also one off topic question, livecd h as this annoying new bar of programs on the left side of the screen and i like the only menu being on top being able to choose from everything installed, is there a way to get that back?

---

### Post by darkod on 2012-07-29
If you are doing the manual partitioning during install, the question about the bootloader will be right below the partitions list. Don't worry, it will be there.

Anyway, it can easily be added later if it fails for any reason.

---

### Post by aLarM on 2012-07-29
okay, i fixed windows partition and ubuntu install finished installing, will see if all is okay after this song.

---

