---
title: "[SOLVED] various update,upgrade, CD boot problems"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by two4two on 2008-11-14
This is a long one!  We have 6 computers in our family.  They are all fairly old computers with Athlon/Athlon XP on some sort of VIA chipset from various mobo manufacturers and 750MB of PC133 memory.  They are all dual-boot Win98SE (primary master) and WinXP (primary slave) on two seperate HDDs on PCI add-in IDE controllers.  I'm installing Ubuntu (8.10) on all of them as a third OS.  I've completed two of these so far by putting Linux on a third HDD as secondary master.  The first one was trouble-free starting as 7.10, upgrading to 8.04 LTS; installing 8.04 from scratch and upgrading to 8.10beta; and finally installing 8.10 final release from scratch.  All of these operations went trouble-free.  The second one was a little more difficult.  I never used 7.10.  I started at 8.04 from live CD and installed.  The install failed a few times just at the point where it configures HAL, but finally it worked.  Then I installed all the latest 8.04 updates and they failed the same way when it configured HAL, but finally I got them to install.  Then I tried to upgrad to 8.10 using the alt CD but it failed with some broken package (a desktop theme of some sort), and so I installed 8.10 beta fresh from live CD and then got the latest updates online.  It is finally stable.  I think the main problem with that one was that ACPI was past the cut-off date and the install had to use ACPI force.  Great, two down and 4 to go!

So now I'm working on the third computer.  DFI mobo with VIA KT133A chipset, 750MB of PC133 memory, but only 2 HDDs on PCI add-in IDE controller.  Primary master is 80GB HDD with Win98SE on first primary FAT32 partition (sda1) and an extended partition with 4 logical FAT32 partitions (sda5,6,7,8 ).  The second 250GB HDD (primary slave on IDE controller) is as follows:  sdb1 is FAT32 and has WinXP; then there was undefined space; then there is an extended partition with 4 logical FAT32 partitions (sdb5,6,7,8 ).  In the unallocated space I created an ext3 primary partition which is called sdb3, and a 1GB swap partition.  So I don't know whatever happened to sdb2.  If anyone is curious I could run gparted to see.  So I've done like in both the other installs, I've installed grub into the boot sector and not in the MPR.  Then I used a piece of software called BOOTPART to copy the 512 byte record from the LINUX boot sector to the C drive and use the Win NTLDR as the primary boot loader.  Works just fine.  So here are my travails in setting up this 3rd computer!!!!

Just as in the 2nd computer, 8.04LTS live CD has a hard time booting and if it does the install often fails during HAL setup.  And getting the updates from online and installing them has a couple of failed packages and it also fails during HAL setup.  But I was able to boot the install and use dpkg -- configure -a (as superuser) to finish the interrupted package.  But!! The 8.10 alt cd doesn't work at all.  I use terminal sh /cdrom/cdromupgrade and it won't even start running.  And it doesn't even give the auto upgrade window.  So I tried upgrading online and it fails when configuring HAL.  So I try the 8.10 final release live CD and it won't even boot.  All I see is the orange progress line and it stops dead at about 10% of the way across.  So I'm stuck at 8.04 with all the current updates applied.  It's a lot of work to try to get this thing up to date and now that I've got it this far I'm afraid to do any more updates or upgrades.

Anyone have any ideas why it can be so hard?  Sometimes the CDs work and sometimes they don't.  I checked the CDs when I burnt them and they are OK.  I checked them from the Ubuntu menu when I'm booting from the CD and they are OK.  Also I checked the MD5SUM hash and it's good.  How do I keep a log of what's happenning so I can investigate and post it?  On alt CD I get an option to rescue failed installs, but I don't know how to use it.  Also I don't know how to use the recovery mode boot option.  Sometimes the old kernel will boot, but ff the install fails too badly I get a syn-up error and the panic message (and flashing num lock lights) and so all I know how to do is re-try the install.  Why so many problems?????

---

### Post by cdtech on 2008-11-14
WoW! more of a journal...:lolflag:

> All I see is the orange progress line and it stops dead at about 10% of the way across. So I'm stuck at 8.04 with all the current updates applied. It's a lot of work to try to get this thing up to date and now that I've got it this far I'm afraid to do any more updates or upgrades.

If you reboot and at the grub boot screen hit the esc key and select the kernel line that you want to boot from hit the  e key to edit the kernel boot line and remove the quiet and splash from the kernel bootup line. This will let you see visually what its hanging up on.

---

### Post by two4two on 2008-11-15
Thank you cdtech.  One more problem that I'm researching:  I've attached 2 screenshots -- one for each HDD.  As you can see, Ubuntu is on sdb3.  Here's my problem:  when I click on **Places --> removable media**, or **Places --> Computer**, it doesn't show sda.  I want to use those FAT32 partitions because there is data there I want to use.  This Ubunto partition is relatively small and I want to use the FAT32 partitions for storage.  But only sdb is accessible.  I need to access sda too.

Oh, BTW, sdb2 IS the extended partition.

---

### Post by caljohnsmith on 2008-11-15
How about opening a terminal (Applications > Accessories > Terminal), and post:
```
sudo fdisk -lu
```
Does that show your sda drive?

---

### Post by two4two on 2008-11-17
Thanks caljohnsmith.  Yes my sda drive was listed when I did fdisk -lu.  So why isn't it listed in Places --> removable media, or Places --> computer?  My sdb is listed in both places and I can mount it.  But I can't even find sda to do the mount.  What next?

---

### Post by caljohnsmith on 2008-11-17
I'm not sure why your sda drive doesn't show up under the Places menu. You could easily manually mount the partitions by first creating a directory in /media to mount it on:
```
sudo mkdir /media/[COLOR="Blue"]Data_1[/COLOR]
```
And of course you can name it anything you want. Then do:
```
sudo mount /dev/[COLOR="Blue"]sdb1[/COLOR] /media/Data_1
```
And change sdb1 to whichever sdb partition you want to mount on the new directory in /media. Then you will have access to it if you browse to the /media/Data_1 folder in the file browser. 

If you want, you could add an entry in your /etc/fstab so that the partition is automatically mounted on start up. If you would like help with that, then please post the output of the fdisk command I gave in my previous post, and also specify which partition you want to mount.

---

### Post by two4two on 2008-11-17
dad@kids1-linux:~$ sudo fdisk -lu
[sudo] password for dad: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30d030cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31262489    15631213+   c  W95 FAT32 (LBA)
/dev/sda2        31262490   156296384    62516947+   f  W95 Ext'd (LBA)
/dev/sda5        31262553    62524979    15631213+   b  W95 FAT32
/dev/sda6        62525043    93787469    15631213+   b  W95 FAT32
/dev/sda7        93787533   125049959    15631213+   b  W95 FAT32
/dev/sda8       125050023   156296384    15623181    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x51df4e9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    62910539    31455238+   c  W95 FAT32 (LBA)
/dev/sdb2        93996315   625137344   265570515    f  W95 Ext'd (LBA)
/dev/sdb3        62910540    93996314    15542887+  83  Linux
/dev/sdb5        93996378    96036569     1020096   82  Linux swap / Solaris
/dev/sdb6        96036633   229327874    66645621    b  W95 FAT32
/dev/sdb7       229327938   362683439    66677751    b  W95 FAT32
/dev/sdb8       362683503   495990809    66653653+   b  W95 FAT32
/dev/sdb9       495990873   625137344    64573236    b  W95 FAT32

Partition table entries are not in disk order
dad@kids1-linux:~$ 


It is sda that can't be found.  I did what you said (using sda1) and created the directory and issued the mount.  It says the mount point doesn't exist:

root@kids1-linux:/home/dad# mkdir /media/data_2
root@kids1-linux:/home/dad# mount /dev/sda1 /media/data_2
mount: mount point /media/data_2 does not exist

A mystery to me.  All the sda_ partitions are in /dev
Any more ideas?

---

### Post by caljohnsmith on 2008-11-17
How about:
```
ls -l /media
```
And see if the "Data_2" directory is there like it should be.

---

### Post by two4two on 2008-11-17
dad@kids1-linux:~$ ls -l /media
total 28
lrwxrwxrwx 1 root root     6 2008-11-13 11:41 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2008-11-13 11:41 cdrom0
drwxr-xr-x 9 root root 16384 1969-12-31 19:00 Data_1
drwxr-xr-x 2 root root  4096 2008-11-17 16:44 data_2
lrwxrwxrwx 1 root root     7 2008-11-13 11:41 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2008-11-13 11:41 floppy0
dad@kids1-linux:~$

---

### Post by two4two on 2008-11-17
As you can see, sda extended partition is there with its logical partitions, but I just have no way of accessing it.  It is not in Places --> removable media, or Places --> computer, or any way I know how to get to the files on those partitions.  Is it possibly a permissions thing?  Or is there a place where partitons are marked to be hidden?  In review, sda has Win98SE on sda1 and I use the ntldr from that drive, and there are some logical partitions on the HDD.  It is the drive Ubuntu can't see.  sdb has WinXP on sdb1, sdb2 is an extended partition with 4 logical partitions, while sdb3 is the second primary partition on the hdd and it is my Linux partition.  I believe my swap partition is in the extended partition.  Since I don't know much about the way linux does things I am stumped.

---

### Post by caljohnsmith on 2008-11-17
I'm thinking that your problem may be more fundamental than just not being able to mount those partitions; the mount command claimed that "/media/data_2" does not exist, when clearly that directory exists according to "ls -l /media". How did you invoke that root shell? How about doing it with sudo instead:
```
sudo mount /dev/sda1 /media/data_2
```
If that doesn't work, try:
```
sudo mkdir /tmp/data_2
sudo mount /dev/sda1 /tmp/data_2
```
Please post the output of all the above commands.

---

### Post by two4two on 2008-11-17
In Accessories --> terminal I simply entered "su" and it asked me for my password and then it gave me the new command prompt with root as the user.  Here was when I created the directory and issued the mount and got the error:

root@kids1-linux:/home/dad# mkdir /media/data_2
root@kids1-linux:/home/dad# mount /dev/sda1 /media/data_2
mount: mount point /media/data_2 does not exist


But later when I did the  ls -l /media  I didn't do it from root.  I'll do the new things you asked and post them.  Stay tuned.  Thanks for all your help.  I really need to access those partitions.

---

### Post by two4two on 2008-11-18
OK caljohnsmith, here it is.  I entered the commands exactly as you specified.  It tells me I need to specify filesystem type.  These are FAT32 partitions.  Not being expert in Linux I didn't want to try it further and take the chance of killing my FAT32 partition.  Obviously there is something wrong that it doesn't know about the partition because isn't mount supposed to find out the filesystem type and the other options for itself without me having to specify?  Here's the results of the commands:


[B][COLOR="Blue"]dad@kids1-linux:~$ sudo mount /dev/sda1 /media/data_2
mount: you must specify the filesystem type
dad@kids1-linux:~$ sudo mkdir /tmp/data_2
dad@kids1-linux:~$ sudo mount /dev/sda1 /tmp/data_2
mount: you must specify the filesystem type
dad@kids1-linux:~$ [/COLOR][/B]

---

### Post by caljohnsmith on 2008-11-18
> **two4two said:**
> Obviously there is something wrong that it doesn't know about the partition because isn't mount supposed to find out the filesystem type and the other options for itself without me having to specify?
Yes, something must be wrong, because "mount" will normally figure out the partition file system on its own and mount it accordingly. I'm beginning to suspect there is something wrong with your Ubuntu rather than your data partitions though; how about booting your Live CD and run the same commands, and post the output so I can see what happens.

---

### Post by two4two on 2008-11-18
Same results from live CD.  Maybe there IS something wrong with the partitions since Ubuntu can't see them either from the installed OS or from the live CD.  Let me say though that Windows can see these partitions.  Here is the results from the commands from live CD:

[B][COLOR="RoyalBlue"]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /tmp/data_2
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /tmp/data_2
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30d030cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31262489    15631213+   c  W95 FAT32 (LBA)
/dev/sda2        31262490   156296384    62516947+   f  W95 Ext'd (LBA)
/dev/sda5        31262553    62524979    15631213+   b  W95 FAT32
/dev/sda6        62525043    93787469    15631213+   b  W95 FAT32
/dev/sda7        93787533   125049959    15631213+   b  W95 FAT32
/dev/sda8       125050023   156296384    15623181    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x51df4e9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    62910539    31455238+   c  W95 FAT32 (LBA)
/dev/sdb2        93996315   625137344   265570515    f  W95 Ext'd (LBA)
/dev/sdb3        62910540    93996314    15542887+  83  Linux
/dev/sdb5        93996378    96036569     1020096   82  Linux swap / Solaris
/dev/sdb6        96036633   229327874    66645621    b  W95 FAT32
/dev/sdb7       229327938   362683439    66677751    b  W95 FAT32
/dev/sdb8       362683503   495990809    66653653+   b  W95 FAT32
/dev/sdb9       495990873   625137344    64573236    b  W95 FAT32

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

[/COLOR][/B]

---

### Post by caljohnsmith on 2008-11-18
When you say that Windows sees the partitions, can you read and write to them just fine from Windows? And you can still boot into Win98SE on sda1 OK?

How about trying to mount a couple of your logical partitions and see if that gives the same result:
```
sudo mkdir /mnt/sda5 /mnt/sda6
sudo mount /dev/sda5 /mnt/sda5
sudo mount /dev/sda6 /mnt/sda6

```
If that doesn't work, try:
```
sudo mount -t vfat -o force /dev/sda5 /mnt/sda5
```
And if that doesn't work, then I would boot into Windows, open a terminal ("cmd") and do:
```
map
```
That should give the drive letters of your data partitions, and for each one, how about running:
```
chkdsk /r D:
```
Replace "D" with the drive letters of the data partitions, and also run chkdsk on each partition as many times as it takes until it reports no errors. Let me know how that goes.

---

### Post by two4two on 2008-11-19
I'm running from the live CD -- this time 8.10 release.  Here are the results:

To[B][COLOR="Blue"] run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda5 /mnt/sda6
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/sda5
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/sda6
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount -t vfat -o force /dev/sda5 /mnt/sda5
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/COLOR][/B]

I'll boot into windows and try that chkdsk thing.

Oh, and BTW, I found out my webcam hangs up this 8.10 live CD.  It thinks its a different manufacturer and maybe it's trying to connect with it and can't.  When I unplugged it I was able to boot Live.  The webcam is OK in 8.04

---

### Post by two4two on 2008-11-19
It was successful.  I did the chkdsk as you said and it fixed several errors on the "C" drive.  The others were OK.  Then I cam back here to my 8.04 install and sda was still not visible, but I did the mount command as you wrote (but it didn't like the "force" option, so I just did it without it) and woila!  It works.  Now I need to get them to be visible in Places -- Computer when I boot up.  I'll re-read your posts and see if I can get it done for all those partitions on sda.  Thanks a bunch! :)  (Oh, and I'll figure out how to do an official Thanks on this forum for ya!

---

### Post by cdtech on 2008-11-20
> **two4two said:**
> Now I need to get them to be visible in Places -- Computer when I boot up.  I'll re-read your posts and see if I can get it done for all those partitions on sda.  Thanks a bunch! :)  (Oh, and I'll figure out how to do an official Thanks on this forum for ya!

Any time you mount a device using "/media/device" it will show up under places. Using the "/mnt" directory wont show.

Good luck.
And don't thank me, I had nothing to do with your success. :guitar:

---

### Post by caljohnsmith on 2008-11-20
> **two4two said:**
> It was successful.  I did the chkdsk as you said and it fixed several errors on the "C" drive.  The others were OK.  Then I cam back here to my 8.04 install and sda was still not visible, but I did the mount command as you wrote (but it didn't like the "force" option, so I just did it without it) and woila!  It works.  Now I need to get them to be visible in Places -- Computer when I boot up.  I'll re-read your posts and see if I can get it done for all those partitions on sda.  Thanks a bunch! :)  (Oh, and I'll figure out how to do an official Thanks on this forum for ya!
Glad to hear it finally works after doing the chkdsk on your partitions. Cheers and have fun with your OSes. :)

---

### Post by two4two on 2008-11-20
I installed pysdm (storage device manager) and when I look at sda1 general configuration and use the assistant it has checked to mount at boot time.  But it said the name was sdb8.  I changed it to sda1 and clicked APPLY.  I go to dynamic configuration rules and the attributes say the name is still sdb8 and on the bottom left of the sdm window it says it's /dev/sdb8.  Now that's a problem.  The mount as you helped me to do worked and I was able to read/write the partition, but when I went to do the things to make it mount at startup I found this little twist.  I'm a little afraid to re-boot now because maybe It will kill one or the other or both of the partitions sda1/sdb8.  I attached a screenshot of it.  What do you make of it?

Oh, I'm going to re-boot anyway, so I'll let you know if anything bad happens.

---

### Post by two4two on 2008-11-20
So, I rebooted and it's up.  Still the system has confusion over devices and mount points.  Some device such as sdb8 or sdb3 etc gets mounted on sda1, while sda1 gets mounted nowhere.  So I did the mount command you suggested earlier and it works and I can get to the real sda1, but when I get more time I'd like to sort through the strange device mapping that occurs when this thing boots up.  If you'd like me to put together an accurate picture of what gets mounted and where (such as with gparted, sdm, and file browser to go through contents of certain files) let me know what would be useful for you to get a picture of what's happenning, OK?  I'd really appreciate it.  For now I can get to sda1 and all the others but I'd like to get it straight the way it should be.  Thanks.

---

### Post by caljohnsmith on 2008-11-20
I'm not familiar with using pysdm because I normally just edit my /etc/fstab manually; how about posting:
```
cat /etc/fstab
```
And I'll try to help you sort out the mounting issues.

---

### Post by two4two on 2008-11-20
OK, I edited fstab and made sure all the devices were mounted at the correct place and I rebooted and now they are all there and I can access them all.  Thanks so much fo helping.  One quick question:  how do I keep a log of the entire boot process from the text phase thru the gui phase?  I'd like to see what all happens.  I'd like to install updates but until I can know what might hang this thing up I'm afraid to do it.  How to back up before I go?  Maybe just burn this partition to DVD or back it up to a different ext3 partition on a flash drive?

---

### Post by caljohnsmith on 2008-11-20
> **two4two said:**
> OK, I edited fstab and made sure all the devices were mounted at the correct place and I rebooted and now they are all there and I can access them all.  Thanks so much fo helping.  One quick question:  how do I keep a log of the entire boot process from the text phase thru the gui phase?  I'd like to see what all happens.  I'd like to install updates but until I can know what might hang this thing up I'm afraid to do it.  How to back up before I go?  Maybe just burn this partition to DVD or back it up to a different ext3 partition on a flash drive?
I read there's been some changes in the way Intrepid logs the boot process vs. previous Ubuntu versions; problem is I can't remember the details. But most of the boot process messages you can see with:
```
dmesg | less
```
Also, if you want to backup your partition, there is "[Clonezilla]("http://www.clonezilla.org/")", and "partimage" is available in the repositories. Or if you want to be a little geeky about it and use the command line, you can use: 
```
sudo dd if=/dev/[COLOR="Blue"]sdb3[/COLOR] bs=10M conv=notrunc,noerror | bzip2 -c > ~/Desktop/[COLOR="Blue"]sdb3[/COLOR].bz2
```
That will make a clone of the sdb3 partition and save it to your desktop in compressed form so you won't end up with a full ~15 GB file (the size of the sdb3 partition). And then to restore the sdb3 image:
```
bzcat ~/Desktop/[COLOR="Blue"]sdb3[/COLOR].bz2 | dd of=/dev/[COLOR="Blue"]sdb3[/COLOR] bs=10M conv=notrunc,noerror
```
And of course you would want to put that "sdb3.bz2" partition image somewhere other than in your sdb3 partition. Anyway, good luck with it. :)

---

### Post by two4two on 2008-11-20
Thanks so much.  You've fixed every one of my problems for me.  I'll mark this thread resolved.  Thanks again! :)

---

### Post by two4two on 2008-11-20
Thank you for your part in helping me get this straightened.  You helped me find out where the install or live CD process stopped, both in this 8.04 and in the 8.10 versions.

---

