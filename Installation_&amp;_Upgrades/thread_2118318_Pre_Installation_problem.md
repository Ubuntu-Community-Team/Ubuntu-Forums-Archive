---
title: "Pre Installation problem"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by ln633 on 2013-02-20
During the "Preparing to install Ubuntu" it says that I do not have 4.8gb on my hard drive but there is 160gb available. Is there something I'm supposed to do in Windows so that I can install ubuntu?

I also have reformatted my harddrive but I still experience the same problem. Here is a picture of what it looks like(picture from google) : 

[http://3.bp.blogspot.com/_A3pAfmaZt-Q/TNiI6C2XO5I/AAAAAAAAAfg/wfxw6uySc1s/s800/02-PreparingToInstallUbuntu.png](http://3.bp.blogspot.com/_A3pAfmaZt-Q/TNiI6C2XO5I/AAAAAAAAAfg/wfxw6uySc1s/s800/02-PreparingToInstallUbuntu.png)

I have a 'cross' on 'has at least 4.8 gb available drive space, which I think is not allowing me to continue.

---

### Post by MAFoElffen on 2013-02-20
Welcome to Ubuntu Forums.

Can you start up on a LiveCD > Use Try without installing. > Start a terminal session <cntrl><alt><T>...

Cut and paste this into the terminal prompt:
```

lsblk && fdisk -l

```
Press <Enter>. Then start a browser and cut and paste the results back here please.

---

### Post by ln633 on 2013-02-20
ubuntu@ubuntu:~$ lsblk && fdisk -1
NAME  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0    11:0    1 753.3M  0 rom  /cdrom
loop0   7:0    0 722.3M  1 loop /rofs
fdisk: invalid option -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sector

---

### Post by ln633 on 2013-02-20
and thank you :D
My computer science class requires me to use Linux to do stuff so I'll be creeping on the forums for a while. I tried using Oracle Virtual Box and VM player but they ran too choppy on my computer so I thought I would install it over windows 7

---

### Post by sudodus on 2013-02-20
```
lsblk && fdisk -l
```At the end of the command it should spell 'minus ell'.

Tip: if you cut and paste, you should get it right 'automatically'

*Edit*: I would suggest superuser privileges for the latter part of the command line

```
lsblk && sudo fdisk -l
```

---

### Post by ln633 on 2013-02-20
oh..

ubuntu@ubuntu:~$ lsblk && fdisk -l
NAME  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0    11:0    1 753.3M  0 rom  /cdrom
loop0   7:0    0 722.3M  1 loop /rofs

---

### Post by sudodus on 2013-02-20
> **ln633 said:**
> oh..

ubuntu@ubuntu:~$ lsblk && fdisk -l
NAME  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0    11:0    1 753.3M  0 rom  /cdrom
loop0   7:0    0 722.3M  1 loop /rofs
Sorry, you did not catch my edit with 
```
  lsblk && sudo fdisk -l 
```

---

### Post by ln633 on 2013-02-20
ubuntu@ubuntu:~$ lsblk && sudo fdisk -l
NAME  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0    11:0    1 753.3M  0 rom  /cdrom
loop0   7:0    0 722.3M  1 loop /rofs

Looks like I got the same thing!

---

### Post by sudodus on 2013-02-20
> **ln633 said:**
> ubuntu@ubuntu:~$ lsblk && sudo fdisk -l
NAME  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0    11:0    1 753.3M  0 rom  /cdrom
loop0   7:0    0 722.3M  1 loop /rofs

Looks like I got the same thing!
You get no output from fdisk.

Try gparted (it has a graphical user interface)
```
sudo gparted
```

---

### Post by sudodus on 2013-02-20
Check in Windows, what kind of partitions (volumes) that was created. Linux does not like dynamic partitions. Maybe this link will help you (if it is the same problem)

[http://ubuntuforums.org/showthread.php?t=1730617](http://ubuntuforums.org/showthread.php?t=1730617)

---

### Post by ln633 on 2013-02-20
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================
Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Can't have a partition outside the disk!

When GParted was open, the GUI came up but no devices were detected.

---

### Post by sudodus on 2013-02-20
No luck with gparted either. Ubuntu cannot see a hard disk drive. Are you sure that there is one connected? 

I hope you can still run Windows. Let us know what partitions you can see from Windows!

---

### Post by ln633 on 2013-02-20
Yeah I can still run Windows :/
Man, this is a wild goose chase!

---

### Post by sudodus on 2013-02-20
Also, have a second look at the link in post #10 (about dynamic partitions), but I'm not sure it's your problem.

Maybe it is time now, that you describe your computer: Brand name and model, cpu, ram, graphics chip/card and wifi chip/card. And what BIOS/UEFI version?

And which Ubuntu version are you trying to install? It makes it easier to help, when we know more details :-)

---

### Post by Sef on 2013-02-20
> ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================
Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0 has been opened read-only.
Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0 has been opened read-only.
Can't have a partition outside the disk!

When GParted was open, the GUI came up but no devices were detected.

If the disc is mounted, gparted will not be able to read it, so were using a Live CD or hard drive? If it is the latter, that is the problem.

---

### Post by sudodus on 2013-02-20
Maybe the install CD disk is bad? At the very beginning (after selecting language) you can test that the disk is good (one of the selections). Perform that test!

---

### Post by MAFoElffen on 2013-02-21
> **sudodus said:**
> You get no output from fdisk.

Try gparted (it has a graphical user interface)
```
sudo gparted
```
Gparted is not a default app... (although I always have it handy!)

So wouldn't it be 
```

sudo parted -l

```
to use the default partitioner on the LiveCD to "list" all partitions on all disks...

There's another way to get around where he is getting stopped, but I'm a little leery of mentioning it right off the bat without learning if it really has enough room or not. That would be to go through the LiveCD's Advanced Install Menu. Too easy to overwrite anything there going that way, but he said he re-formatted the hard disk?So it is empty NTFS or "other" now?   Or if he re-sized the Win partition... A little unclear on that.

Also unclear whether he is wanting to install as a full install in it's own multi-boot partition or if he is trying to go wubi...

---

### Post by sudodus on 2013-02-21
Gparted is (at least was) included in the Ubuntu boot CD (but it is not installed into the internal drive by default) ... and yes, many things are unclear at the moment. So, what are the best questions to ask?

---

### Post by sudodus on 2013-02-21
> **Sef said:**
> If the disc is mounted, gparted will not be able to read it, so were using a Live CD or hard drive? If it is the latter, that is the problem.
I checked it in my computer: gparted can see partitions that are mounted. It even tells that they are mounted (and does not want to edit them, unless they are unmounted).

---

### Post by MAFoElffen on 2013-02-21
Let's start over-

What is the computer make and model?
What is the CPU?
How much RAM?
What is the size of your hard disk?
How many partitions does Windows report?
How much space left over does Windows report for each partition?
What version of Windows is it?

While getting these answers for us, think on this-

There are 3 different basic kinds of Ubuntu installs for Windows users available through the main install menu's of the LiveCD if you follow the scripts:

1. Install full version in it's own partition. (Classic full install.) Needs unused space on hard-disk to create it's own partition and an additional Linux Swap partition. This is what I recommend to my customers. Secure. Independent. Can be used to recover Windows if needed.

2. Install as WUBI, meaining it installs as a Windows app, starting from within Windows from it's own file image within the windows partition.

3. Install over Windows... One of the options is to install using the whole disk. Careful with that. Your Win system and data will be lost and not be recoverable.


Next thing to think on is the boot loader. I recommend Grub2. It is adaptable and for the most part can be self-configured. Configuring the Windows boot loader is (to me) not as easy or adaptable. <-- I can do it, but I don't trust new users to be able to do it without having some basic Windows systems admin skills...

Back to partitions. This assumes you are installing a full version of Ubuntu in it's own partition, keeping Windows = multi-boot...

- Windows likes to run close to the root of the disk/ the beginning. So the Winodws system partitions hold be the first partitions on the disk. Linux doesn't care where it starts from or if it in a primary or logical partition. File image vulnerable to windows viruses. Performance not as good. If Win is down, well...

- Multi-boot systems need just a little bit of room to install a boot loader...

- Hard disks and partition tables- You have 4 primary partitions to play with or 3 primary and any number of logical partitions. So far a multi-boot install of windows and Linux, I usually go The original recovery partition (if exist), the original system partition, the original data (if exist) as primaries... The logical sda5 as linux root and logical sda6 as linux swap.
 
- Windows partitions move/re-size better from the Windows disk manager. The Linux utilities can do it, but if you move/re-size from them, then the first time you start windows, you'll have to repair the windows file indexes.

Taking the what is reasonable to take from each partition as free space/unallocated. You will need to move/re-size your partitions. Do not cut yourself to short on the Win System partition. It needs some free space to run and will give warnings about not having enough if too tight.

When you move/re-size the first partition, leave 1 MB of space free and unallocated before it. This is important! Some will say it is not... but it's a gamble if you don't. Sometimes if you don't leave this space on a multi-boot, when you load the boot loader, it may span over encroaching into the first partition, destroying the WIN boot record. (Better to plan ahead and be safe!) After it is moved, move/re-size the next against it, starting just after where that one left off.

Do you have enough space for Ubuntu? I've installed Linux in 4 GB's but it's tight. You are a student learning Linux and it's systems. You are going to have exercises, homework and tests, installing app's, etc. I would recommend at least 10GB's as a minimum. 40GB as a roomy start.

If you still don't have enough room- You're a student and are probably strapped for cash. You can still get creative on a budget. If you have a "computer recylcer" somewhere close, talk to the owner. Tell them you are a Computer Science student. I get 10-15GB PATA HD's for free. They feel anything under 20GB's as not being big enough for resale/reusing. I get them free to use as development test disks. Put in 3-4 of them and you can use software RAID5 or LVM to expand your space... Dependds if you have PATA support and room in your case. The again, you can pick up external USB PATA drive cases for about $20-$30.  

When you have enough room... Start up on a LiveCD and when it gets to the partitioner, select automatically use free space. If you have multiple drives or want to tune it to your own spec's, you'll have to do it manual/custom.

If you want to learn how to tweak the partitions for the best performance, just tell me before you start and I'll explain that... 

If not, good luck. At the last 98% of the install, it will probe for other operating systems, It should find your windows OS. It will ask you if you wish to install Grub2 as the bootloader. Select yes. If it asks you where, install to the root of the first drive ( the drive you left that 1MB unallocated) // NOT to any specific partition!!! If you select a partition you will may wipe out the MBR of your Windows OS...

Enough info to get started?

---

### Post by ln633 on 2013-02-21
Hey guys! Back from school.

-Amd Athlon II x2 5200+ 2.6ghz
-2gb ddr2 ram
-250gb harddrive 
-1 partition, made a second partition of 20gb to try to "fix" the problem but no good.
-I have about 250 gb harddrive space left over as well. I inserted my Window's 7 disc, deleted the recovery part of the partition and then clicked "format" for the partition that had all my other files such as program files, my documents, etc.
-Windows 7

I downloaded the latest version of Ubuntu on my laptop(12.10) and burned it to a DVD+ using Nero. I said the bios to my desktop to start the dvd drive first and rebooted with the disc inside. I'm not trying to dual boot, but what I want to do is replace windows 7 with Linux.

If you guys need other info, I'll be up for another 3 hours!

---

### Post by sudodus on 2013-02-22
Please add info about graphics and wifi chip/cards!

Otherwise, the general specs should allow you to choose any of the Ubuntu flavours of desktop environment

^ fancy
| Ubuntu with Unity
| Kubuntu with KDE
| Xubuntu with XFCE
| Lubuntu with LXDE 
v fast

---

### Post by ln633 on 2013-02-22
250gts
no wifi card 

:[ I wonder what the problem is

---

### Post by sudodus on 2013-02-23
Well, I wonder too.

1. Have you checked in Windows,*** if the file system is dynamic***? Such systems do not work with linux.

2. Have you used the ***md5sum*** to check if the download and burning were correct?
See this link

[COLOR=Red] [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[/COLOR]
3. The 250 gts card is from nVidia and it has been around at least a couple of years. You probably need a proprietary nvidia driver to get it running fast. You can use ***jockey-gtk*** for that purpose (after installation). It is possible that there is some error because of that card, but I don't think so. It is probably something else, that is hiding the hard disk drive for you.

I am editing this text in a live session booted from an Ubuntu 12.04.2 LTS iso file in a workstation with fairly old xeon cpus and an nvidia gt 430 card, and it works well with the free nouveau graphics driver, that comes with Ubuntu. And I can see the drives in the computer.
--
I suggest that you ***download Ubuntu 12.04.2 LTS*** and try that too. There might be a bug in the newer 12.10, that is tricking you. 12.04 LTS has been around for 6 more months and is quite stable by now.

---

