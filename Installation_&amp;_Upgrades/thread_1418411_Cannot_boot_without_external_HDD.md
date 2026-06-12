---
title: "Cannot boot without external HDD"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by clydeseal on 2010-02-28
Hi everyone I just recently installed ubuntu. I had always used windows before, and I wanted to try something different. My laptop's internal HDD is pretty full so I decided to install ubuntu on my 500gb external HDD. It is connected via USB A to USB B.

So I run through the installation no problems at all. I partitioned 200gb of the external HDD for ubuntu. After install I could run ubuntu just fine and I really like it. 

However now it boots through GRUB. I am not really sure what GRUB is but it says GRUB loading every time I boot up and then lets me choose what os to boot, but if I do not have my external HDD plugged in then GRUB fails to start and I cannot boot at all from my laptop.

Is there a way that I can get it to boot windows from the internal HDD without having the external HDD?

---

### Post by darkod on 2010-02-28
Yes. There is an easy fix.
Connect the ext hdd, boot ubuntu and in terminal run:

sudo fdisk -l

and post the results here. That will show your disks and partitions. Also tell us which is your internal and which your external disk (although it would be easy to understand from the results, just in case).

---

### Post by oldfred on 2010-02-28
When you installed you had the internal set as boot in BIOS. After the suggested updates you need to set the external as first to boot in BIOS so it gives you grub and if not plugged in, the internal boots windows.

From Ubuntu reinstall grub to the external. Probably sdb but you need to check. Change boot order, sudo update-grub and check that you can boot both. Then install a windows boot load in the internal drive probably sda.

Threads with similar issues adn more instructions:

[http://ubuntuforums.org/showthread.php?t=1416000](http://ubuntuforums.org/showthread.php?t=1416000)
[http://ubuntuforums.org/showthread.php?t=1416899](http://ubuntuforums.org/showthread.php?t=1416899)

---

### Post by clydeseal on 2010-02-28
Okay I do not really know what all this is, I am still really new with ubuntu. Here is the terminal entry you asked for.
```
andrew@Andrew-Ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a95f8f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       14594   115683328    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6a6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       27377   219905721   83  Linux
/dev/sdb2           60054       60801     6008310    5  Extended
/dev/sdb5           60054       60801     6008278+  82  Linux swap / Solaris
andrew@Andrew-Ubuntu:~$ ^C
andrew@Andrew-Ubuntu:~$ 
```
I hope this helps, cuz I do not have a clue :confused: 
The first disk listed (the 120gb) is my internal HDD
The second disk listed (the 500gb) is my external HDD

---

### Post by darkod on 2010-02-28
OK. Connect the ext disk, boot into ubuntu and run:

sudo grub-install /dev/sdb

to put grub2 (the bootloader) on the ext hdd. Right now it's on the internal while its config files are in the ubuntu partition on the ext and that's why you can't boot without it.

To put generic mbr on /dev/sda so you can boot windows directly from it, run:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be some warnings but ignore them.

After that try booting ubuntu and windows from grub2, and also try to boot with the external disconnected to see if it worked.

---

### Post by clydeseal on 2010-02-28
I ran into a problem "sudo grub-install /dev/sbd" failed it gave me this back
```
grub-probe: error: Cannot stat `/dev/sbd'
Invalid device `/dev/sbd'.
Try ``grub-setup --help'' for more information.
```
I was able to complete the second part though. here is the code it gave me back
```
andrew@Andrew-Ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/main mbr 1.1.10-2 [23.0kB]
Get:2 http://us.archive.ubuntu.com karmic/main lilo 1:22.8-8ubuntu1 [390kB]
Fetched 413kB in 2s (205kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 146504 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

```
and then I completed the last part 
```
andrew@Andrew-Ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.
andrew@Andrew-Ubuntu:~$ ^C
andrew@Andrew-Ubuntu:~$ 

```
so what do I do now?

---

### Post by darkod on 2010-02-28
You miss spelled the first command:

sudo grub-install /dev/sdb

not /dev/sbd

---

### Post by clydeseal on 2010-02-28
Thank you thank you thank you soooo much. I can boot windows now without the external HDD and I can boot ubuntu with it. Thanks again! 

here is a smiley star for all your help! :KS

---

### Post by clydeseal on 2010-02-28
I have another question...
Since I installed ubuntu on my external HDD when I plug it in my external HDD it does not show up. I only partitioned 200gb for ubuntu, so shouldn't I be able to use the other 300gb for miscellaneous stuff?

---

### Post by darkod on 2010-02-28
Unallocated space (not belonging to any partition) is not showed like that.

Boot your ubuntu and install Gparted (it's on the live desktop but not by default in the install) because it's great tool.

sudo apt-get install gparted

Then open it in System-Administration. In the top right select the /dev/sdb disk. You will see your unallocated space there and can create a partition from it if you want.

If you want to use it for both windows and ubuntu the partition has to be ntfs. Otherwise, for only ubuntu I believe ext4 is more efficient.

Also, even when created, that partition will not mount automatically in ubuntu. It will be in Places and you can mount it when you click on it, for occasional use. For constant use, you need to modify /etc/fstab to mount it on every ubuntu boot. BE VERY CAREFUL WHEN MODIFYING FSTAB!!!!!

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you mess up fstab your ubuntu won't boot up correctly too. :) Just a note.

---

### Post by sgosnell on 2010-02-28
Windows may not recognize the second partition even if it's ntfs.  It seems to only look at the first partition of a drive.  The usual workaround is to install Ubuntu to the second partition, leaving the first partition for data storage with Windows.  Ubuntu will see the second partition, along with any others that exist.

---

### Post by darkod on 2010-02-28
> **sgosnell said:**
> Windows may not recognize the second partition even if it's ntfs.  It seems to only look at the first partition of a drive.  The usual workaround is to install Ubuntu to the second partition, leaving the first partition for data storage with Windows.  Ubuntu will see the second partition, along with any others that exist.

That is a limitation for usb sticks only. Windows uses different drivers for usb sticks and hdds. So for a stick it will only look at the first partition, true. But on usb hdd you can have more partitions and windows will find them.

You can even change the driver to make it recognize more partitions on usb stick too but it's rarely worth the effort.

---

### Post by clydeseal on 2010-02-28
For some reason it will not allow me to select the ntfs format. I have ext 2, 3, and 4 then there is fat16 and fat32 (I do not want to use fat because it is limited to 4gb transfers) and last there is linux-swap. Now there are a lot of other formats including ntfs listed, but they are grey and I cannot select them. :(

Any ideas on how to unlock those formats? 

P.S. Do I have to 50 kills on Veteran level? lol

---

### Post by darkod on 2010-03-01
> **clydeseal said:**
> For some reason it will not allow me to select the ntfs format. I have ext 2, 3, and 4 then there is fat16 and fat32 (I do not want to use fat because it is limited to 4gb transfers) and last there is linux-swap. Now there are a lot of other formats including ntfs listed, but they are grey and I cannot select them. :(

Any ideas on how to unlock those formats? 

P.S. Do I have to 50 kills on Veteran level? lol

Sorry, I forgot to mentioned. The live cd gparted supports ntfs by default, but on the hdd ubuntu you also need to install:

sudo apt-get install ntfs-progs

(I think it had the hyphen in middle). After that your Gparted will support ntfs.

---

### Post by clydeseal on 2010-03-01
I booted from the live cd and was able to get it to format ntfs.

---

### Post by clydeseal on 2010-03-09
Okay since you were so helpful last time, maybe you can help me again.

As you know I have Windows Vista on my laptop internal drive, and Ubuntu on my external drive. Well I decided that I was going to install Windows XP on the external hard drive as well. So I set the external hard drive to the following partitions: 100GB for Ubuntu, 100GB to install XP onto, and 300GB of general storage. I install XP on the external hard drive just fine. However now when I try to boot my computer normally, it boots XP instead of Vista, similar to before when it kept trying to boot Ubuntu instead of Vista. I think it may be like the problem I had before when I had to move the boot loader to the external drive. Can I do something similar with XP?

---

### Post by sgosnell on 2010-03-10
Sorry, I don't do Windows.  I know just enough to know that Windows installations can be problematic, and the Windows does not like being installed on external drives.  Maybe someone will be along with help, but you may need to start a new thread.

---

### Post by clydeseal on 2010-04-01
Okay first install of Ubuntu on the external drive is working great.  However I need to install a second Ubuntu on the external drive also. I have it installed, but I have the same issue as last time. It keeps trying to boot GRUB even when the device is not plugged in. I tried to do the same thing as before with this new install, but it did not work :( so can you help with this please.

Additional Info:
I ran sudo fdisk -l so I could find the partition that the second install of Ubuntu was on. It gave me this back
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6776bb9c
  Device Boot                     Start                    End                 Blocks          ID          System
/dev/sda1                         1                          192                 1536000     27         Unknown
Partition 1 does not end on cylinder boundry.
/dev/sda2                         192                      14594        115683328    7            HPFS/NTFS

Disk /dev/sdb: 500.1 GB 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6a6c

 Device Boot                     Start                       End                Blocks          ID          System
/dev/sdb1   *                   1                        13055       104864256         83          Linux
/dev/sdb2                        52297               60801         68316412+        5          Extended
/dev/sdb3                        13056               52296       315203332+        7          HPFS/NTFS
/dev/sdb5                        60054               60801            6008278+     82          Linux swap / Solaris
/dev/sdb6                        52297               59731          59721574+     83          Linux
```
[SIZE="1"]Sorry I had to manual type this from another computer so it may not look right, but the information should be all correct I triple checked it.[/SIZE]

I thought that if I followed the same formula as before I could do it but it didn't work. I tried "sudo grub-install /dev/sdb" and "sudo grub-install /dev/sdb6" but neither of them worked both came back with errors. So then I tried to install lilo but that didn't work either it came back with an error as well.

Any help would be appreciated. :)

---

### Post by clydeseal on 2010-04-02
Nevermind, after updating the second install of linux I was able to move the boot loader the same way as before. :D

---

