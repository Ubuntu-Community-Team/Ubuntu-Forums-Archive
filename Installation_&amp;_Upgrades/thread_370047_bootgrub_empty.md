---
title: "/boot/grub empty"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by bracc0 on 2007-02-25
Hi, guru's,
I installed ubuntu on my desktop PC. I need to keep my Window$ XP home partition (my wife's job application runs under windows only). I woul like to setup a dual boot.

I have two disks, partitioned as follows:
[LIST]
[*]disk 1 (160 GB)
[/LIST]
[INDENT][LIST]
[*]a single NTFS partition
[/LIST][/INDENT]
[LIST]
[*]disk2 (80 GB)
[/LIST]
[INDENT][LIST]
[*]NTFS partition (50GB)
[*]linux swap partition (2GB)
[*]ext3 partition - ubuntu (23 GB)
[/LIST][/INDENT]

The installation went up smoothly, but unexpectly ended with a grub error message like this: "Failed to load grub".
I rerun the live CD, I mounted my ext filesystem in a temporary mount point named /mnt, I had a look into the /mnt/boot/grub directory: it was empty!
I've just been able to create the device.map file using the "grub" CLI.

How can I populate my /boot/grub dir and boot-up my PC, with the option to choose among ubuntu and Window$?

Thank in advance to those who will answer
Claudio

---

### Post by m.musashi on 2007-02-25
I'm no guru but I'll see if I can help. I've had similar problems with two physical disks. It might load grub on disk 1 and then look on disk 1 for the files even though they are on disk 2. However, it's odd that there is nothing in /boot/grub. Are you sure you are mounting the right partition? Do other folders have files but just not grub?

There is a tool you can download called super grub disk. It can fix a lot of problems. I'll try and find a link.

Here is the SGD home page [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Here is a nice tutorial [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by bracc0 on 2007-02-25
Almost sure I was mounting the right partition, because is the only /ext3 in my PC :-)

The command I used was sudo mount /dev/hdd2 /mnt.

I've read in othe posts about the super grub CD, but I understand is a tool for booting. Am I missing something? Can Super grub CD correct grub/boot errors?

I would like to boot from my PC, instead of using a CD to boot...
I enthusiastically installed ubuntu in three different machines in the last three days, two of them being PC's of friends of mine, and I have problems with my own PC :-(

Thanks
Claudio

---

### Post by m.musashi on 2007-02-25
Yes, SGD can be used to repair grub. I've only used it once or twice so I can't remember the details but there is an option to reinstall grub. It fixed mine when I managed to mess it up.

Just to check. what does```
sudo fdisk -l
``` print out?

Also, the /boot folder should have some files with names like vmlinuz-2.6.17-10-generic. Do you see those? Their absence wouldn't cause grub not to load but I'm just checking to make sure that the parts you need to fix grub are there.

---

### Post by confused57 on 2007-02-25
Here's an excellent tutorial for mounting different partition types, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

You can also reinstall grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

As m.musashi suggested, please post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Super Grub Disk is indeed a handy utility to have, useful for booting Windows or Linux & can repair the mbr of either.

---

### Post by bracc0 on 2007-02-25
> **confused57 said:**
> 
As m.musashi suggested, please post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Super Grub Disk is indeed a handy utility to have, useful for booting Windows or Linux & can repair the mbr of either.

Here-s the output:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1019     8185086   1b  Hidden W95 FAT32
/dev/hda2   *        1020       19456   148095202+   7  HPFS/NTFS

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        6686    53705263+   7  HPFS/NTFS
/dev/hdd2            6942        9964    24282247+  83  Linux
/dev/hdd3            6687        6941     2048287+  82  Linux swap / Solaris

Partition table entries are not in disk order

Answering to confused:
I've already tried with no success to reinstall grub from the live CD. The file /boot/grub/stage1 ia absent. That's why I started this thread;

Answering to musashi:
files in /boot folder seems OK. Here's the output: 

ubuntu@ubuntu:/mnt/boot$ ls -la
total 8376
drwxr-xr-x  3 root root    4096 2007-02-25 11:53 .
drwxr-xr-x 21 root root    4096 2007-02-25 11:53 ..
-rw-r--r--  1 root root  285604 2006-10-13 19:09 abi-2.6.17-10-generic
-rw-r--r--  1 root root   74645 2006-10-13 16:13 config-2.6.17-10-generic
drwxr-xr-x  2 root root    4096 2007-02-25 16:22 grub
-rw-r--r--  1 root root 5697541 2007-02-25 11:53 initrd.img-2.6.17-10-generic
-rw-r--r--  1 root root   94600 2006-10-20 11:44 memtest86+.bin
-rw-r--r--  1 root root  728690 2006-10-13 19:09 System.map-2.6.17-10-generic
-rw-r--r--  1 root root 1636681 2006-10-13 19:09 vmlinuz-2.6.17-10-generic

Thanks for your patience, guys!

Claudio

---

### Post by m.musashi on 2007-02-25
It looks like you are doing things right but it sure seems odd that there is nothing in the /boot/grub directory. I would have thought even if it wasn't working there would still be something there. It is part of the install.

I would give super grub disk a try. If grub isn't loading then something may be corrupted on the MBR. SGD can rewrite the info to the MBR. It should also repopulate the /boot/grub directory with the needed files - although I've never tried to confirm that.

I am assuming that you were never able to boot Ubuntu and that the grub error appeard the very first time you tried to start. Is that correct? If so, it's also possible that the install was not successful or that the CD you installed from is corrupted. This is a somewhat common problem. Make sure the downloaded file is good (i.e. check md5) and maybe try reburning. There is also an option when you boot the live CD to check for errors. Give that a whirl too. If you do burn a new CD choose the slowest possible speed. People have reported problems from burning too fast.

---

### Post by bracc0 on 2007-02-25
> **m.musashi said:**
> It looks like you are doing things right but it sure seems odd that there is nothing in the /boot/grub directory. I would have thought even if it wasn't working there would still be something there. It is part of the install.

Looks very strange to me too.

> **m.musashi said:**
> 
I would give super grub disk a try. If grub isn't loading then something may be corrupted on the MBR. SGD can rewrite the info to the MBR. It should also repopulate the /boot/grub directory with the needed files - although I've never tried to confirm that.

I'm afraid I will have to

> **m.musashi said:**
> 
I am assuming that you were never able to boot Ubuntu and that the grub error appeard the very first time you tried to start. Is that correct? 
Your assumption is correct. I tried to install ubuntu three times: first time I specified (hd0) as a disk where to install grub, second time I specified (hdd), third time I specified (hd1)

> **m.musashi said:**
> 
If so, it's also possible that the install was not successful or that the CD you installed from is corrupted. This is a somewhat common problem. Make sure the downloaded file is good (i.e. check md5) and maybe try reburning. There is also an option when you boot the live CD to check for errors. Give that a whirl too. If you do burn a new CD choose the slowest possible speed. People have reported problems from burning too fast.

I used the very same CD for two other installations, and they went a piece of cake. I usually burn CD's at the lowest speed.

I'll try SGD.

Thanks, guys.
Claudio

---

### Post by m.musashi on 2007-02-25
> **bracc0 said:**
> Your assumption is correct. I tried to install ubuntu three times: first time I specified (hd0) as a disk where to install grub, second time I specified (hdd), third time I specified (hd1)

If I understand correctly, only hd0 will be read at boot (unless there is a way to change that). If you change the boot order in your bios to point to hd1 first it will become hd0. I installed edgy to my hd1 and had it install grub to hd1. The computer boots from hd0 so that grub was not seen. If I changed the bios to point to hd1 first it also didn't work becuase grub was set up to look on /dev/sdb for the kernel and if I changed the hd in the bios it became /dev/sda and wouldn't work (although it would if I edited grub to look in /dev/sda).

I suspect this could have something to do with your problems. I would install grub to hd0 and not make any changes to which disk is hd0 or hd1 and see what happens. Of course, the lack of any files in /boot/grub is still an issue.

---

### Post by randiroo76073 on 2007-02-26
Hi, my /boot & /grub are populated thusly[multi-booted], AFAIK, unless you have at least these in /boot & at least - device.map, menu.lst, stage1, in /grub it won't boot Ubuntu.  I do think it's a good idea to install grub to hd0 though, too.  In order to dual boot you have to use a bootloader other than window's, it doesn't want anything to do with any other OS.

/BOOT..............
abi-#
config-#
intrid.img-#
memtest86+.bin
System.map-#
vmlinuz-#
/GRUB..............
default
device.map
e2fs_stage1_5
fat_stage1_5
jfs_stage1_5
menu.lst
minix_stage1_5
reiserfs_stage1_5
stage1
stage2
xfs_stage1_5

---

### Post by bracc0 on 2007-02-26
> **randiroo76073 said:**
> Hi, my /boot & /grub are populated thusly[multi-booted], AFAIK, unless you have at least these in /boot & at least - device.map, menu.lst, stage1, in /grub it won't boot Ubuntu.

My /boot dir is populated with the right files, I believe. My /boot/grub isn't.
Is the stage1 file common to any ubuntu 6.10 installation? Should be the case, I can get this file from another working machine, and try to re-run the grub CLI.

> **randiroo76073 said:**
> 
I do think it's a good idea to install grub to hd0 though, too.  In order to dual boot you have to use a bootloader other than window's, it doesn't want anything to do with any other OS.


 Thank you for the suggestion. I'll try it for sure, using SGD.
Claudio

---

### Post by bracc0 on 2007-03-05
I finally got my ubuntu partition bootable.

I have just copied the content of the directory /boot/grub from a working Edgy machine (my laptotp) to my Home PC, the one with the /boot/grub empty after ubuntu 6.10 installation.

Then I edited menu.lst and device.map in order to reflect my partitioning and disk names, and with
Super Grub Disk I have been able to boot ubuntu in my home PC! Cool!

What SGD failed was to install GRUB in MBR, either in disk 0 or disk 1. At the moment I can boot into ubuntu with my home PC only if I boot using SGD, choosing manually the partition to boot.
I'll open a new thread about it.

Thanks everybody
CLaudio

---

### Post by m.musashi on 2007-03-05
Hmm. Odd that SGD would not rewrite grub to the MBR. However, I know from personal experience that grub doesn't work well if not on HD0. Others with more experience may know how to get it to work. If I install it to HD1, the only way to boot it is to go into the bios and change the second disk to be first. However, that messes up all the paths since /dev/sdb becomes /dev/sda and then grub can't find what it's looking for. My recommendation...keep grub on HD0.

---

