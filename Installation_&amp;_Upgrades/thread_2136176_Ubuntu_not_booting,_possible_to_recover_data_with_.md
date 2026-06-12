---
title: "Ubuntu not booting, possible to recover data with live cd?"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by Earl-Grey on 2013-04-16
Hi there,

[B]Ubuntu not booting, possible to recover data with live cd?
[/B]
My Ubuntu isn't booting, please can you tell me if I can view the data that I saved when I was unit Ubuntu by using a live cd? If so, what directory would it be in?

---

### Post by darkod on 2013-04-16
The directory depends on the directory where you saved the data. The folder structure is the same, regardless that you are opening the partition from live mode.

Don't you want to try and repair the boot? Maybe someone can help if you give us more details about the error and whether something happened before it stopped booting.

---

### Post by Earl-Grey on 2013-04-16
Thank you for the quick reply.

I have view the File System with the Bin, Boot, CDROM, dev etc folders in it, but dont know where my data would have been saved.

I have a faulty CD rom drive and cannot boot from usb, so I dont think I can recover thus ubuntu instalation.

Do you know what folder my saved data would be in?

---

### Post by Mark Phelps on 2013-04-16
From what I recall, unless you have modified the LiveCD/LiveUSB installer to be persistent, then its filesystem is created only in RAM -- memory -- and when you restart, the filesystem vanishes.  So, unless you had another drive mounted and wrote files to that, there is no way to recover them.

---

### Post by Earl-Grey on 2013-04-16
Thanks for the advice. So maybe it isnt possible to view my saved files as this is only created in RAM. Ubuntu along with the files that I would like to access were saved on the main hard drive.

Do you think there is a way of viewing these files? Maybe if I install a new version of Ubuntu on a different partition?

---

### Post by darkod on 2013-04-17
It is, but you are looking at the wrong place. In live mode, the Filesystem is the "live filesystem".

In Nautilus (the file browser) on the left you should see all partitions from the hdd listed in the Devices section. They will be specified with their size, and label if there was one. According to the size/label, click on your root partition from the hdd and it will open. From there on the structure is the same as if you are inside your installation. For example, once nautilus opens your partition, the home folder is your home folder from the installed ubuntu. All your data should be there. The home folder migth give you issues with ownership and permissions, so you might need to open nautilus as root. You can do that from terminal with:
```
gksu nautilus
```

Be careful, that will give it highest permissions including deleting files.

As mentioned before, if you want to copy something to another ext4 partition, make sure you copy it with ownership and permissions if you want to keep them. You can do that with cp -ax from terminal, for example:
```
sudo cp -ax /source /target
```

Again, are you sure your installation is not easily fixable?

---

### Post by Earl-Grey on 2013-04-17
Hi Darkod,

Thank you very much for the advice.

I am not 100% sure that my Ubuntu isnt easily fixable. I is so temperamental. For example if I wanted to add my wifi settings on the live cd, suddenly the icon for the internet would disappear. I have tried to install the boot-loader to fix grub, but it seems to time out or freeze.

Would you know another way fix grub?

---

### Post by Earl-Grey on 2013-04-17
I noticed a few strange things when I tried to view my files.

I have a 100 GB Hard disk (internal) but when I right click and go to properties it says Size 330866 items totalling 9.7 GB, Free Space 432.6 MB.

Do you know why this is? Sorry about all the quesions #-o

Just to add to that, I wanted to see what options I would get if I went to install Ubuntu again, and it says "This computer currently has no detected operating systems. What would you like to do?" and the "Erase disk and install Ubuntu" radio button is constantly pressed.

I can view the partitions and it shows;
 /dev/sda1 Size > 99091 MB Used > unknown
/dev/sda5 Type > swap, Size > 936 MB, Used > 0 MB

---

### Post by darkod on 2013-04-17
There seems to be an issue with the partition table. That would explain showing only a small part of the disk, and not seeing the OS. From live mode in terminal, can you post the output of:
```
sudo parted -l (small L)
```

Reinstalling grub2 is easy, but it doesn't look like it will solve all your problems. Not only grub2.

---

### Post by Earl-Grey on 2013-04-17
I cannot get sudo parted -l (small L) to work, but had got Sudo parted -l to work. THis is what it says;

Model: ATA Toshiba MK1031GA (scsi)
Disk /dev/sda: 100 GB
Sector sie (logical/physical): 512B/212B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags 
1, 1049KB, 99.1GB, 99.1GB, primary, , boot
2, 99.1GB, 100 GB, 936 MB, extended, 
5, 99.1GB, 100 GB, 936MB, logical, linux-swa(v1)

warning: unable to open /dev/sr0 read-write (read-only file system). /dev/sr0 has been opened read-only.
Error: Invalid parrtition table - recursive partition on /dev/sr0. 
Ignore/Cancel?

P.S. Sorry I should say thank you very much for trying to help me out!

---

### Post by darkod on 2013-04-17
Well, you have all 99GB there, it looks good.

So, if you click the sda1 partition and it opens, can you browse the folders and files? Forget about the right-click and whether it says you have only 9GB. Can you actually see your data or not? That's more important.

I just noticed, the parted -l output doesn't give the filesystem on sda1. Was it like that or you missed it retyping the output? If it doesn't see it as ext4, that could be an issue.

To try and reinstall grub2 to the MBR using the cd in live mode, do in terminal:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

See if that fixes the boot. But if the filesystem is not seen, reinstalling grub2 won't do much good.

---

### Post by Earl-Grey on 2013-04-18
Thanks again for trying to help.

I cannot actually view what is on the 99GB partition.

When I tried the code;

sudo mount /dev/sda1 /mnt

I get the message;

mount: you must specify the filesystem type.

---

### Post by darkod on 2013-04-18
The filesystem seems to be missing. You can try fsck from live mode:
```
sudo fsck /dev/sda1
```

If that also says it can't recognize the filesystem, it doesn't look good.

---

### Post by Earl-Grey on 2013-04-18
> **darkod said:**
> The filesystem seems to be missing. You can try fsck from live mode:
```
sudo fsck /dev/sda1
```

If that also says it can't recognize the filesystem, it doesn't look good.

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sda1: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 135441 has zero dtime.  Fix<y>? 


I get the above message.&#12288;Should I type Y for yes?

---

### Post by darkod on 2013-04-18
Not sure, but I would say yes. I hope the program knows what it's doing. :)

---

### Post by PhilWig on 2013-04-19
Things may be a bit late for this but:

> When I tried the code;
sudo mount /dev/sda1 /mnt
I get the message;
mount: you must specify the filesystem type.


That is a syntax error in the mount command.
I always create a directory as a mount point:
> 
cd /mnt
sudo mkdir mymount

Then you need to specify the partition type in the mount command eg for ext3 it is
> 
sudo mount -t ext3 /dev/sda1 /mnt/mymount
cd /mnt/mymount
ls
#etc


Phil

---

### Post by darkod on 2013-04-19
You can create a directory to use, but there is no syntax error in that command. Also, for ext3/ext4 you don't need to specify it, I guess it can mount those filesystems by default. The problem is that there is an issue with the filesystem, hence the mount fails, not because of syntax.

The parted output shows it too, there is no filesystem stated for sda1.

---

### Post by Earl-Grey on 2013-04-19
Hi there, thanks for helping once again.

Well I tried that 

sudo fsck /dev/sda1 command, and it did change a fiew things, but I still canoot get Ubuntu back.

This time it gave me a GNU GRUB menu. I have the below options

Ubutnu, with Linux 3.2.0-40-generic-pae
Ubutnu, with Linux 3.2.0-40-generic-pae (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

Sadly none of the menus seem to work. I get the below message

Target filesystem doesnt have requested /sbin/init.
No init found. Try passing init=bootarg.


BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) build-in shell (ash)
Enter 'help' for list of built-in commands.

(initramfs)



I am goint to try some of the other commands that you taught me and see what results I get :)

---

### Post by Earl-Grey on 2013-04-19
I tried Sudo parted -l and now get the following new info;

Model: ATA Toshiba MK1031GA (scsi)
Disk /dev/sda: 100 GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags 
1, 1049KB, 99.1GB, 99.1GB, primary,[COLOR=#ff0000]ext4[/COLOR] , boot
2, 99.1GB, 100 GB, 936 MB, extended, 
5, 99.1GB, 100 GB, 936MB, logical, linux-swa(v1)

warning: unable to open /dev/sr0 read-write (read-only file system). /dev/sr0 has been opened read-only.
Error: Invalid parrtition table - recursive partition on /dev/sr0. 
Ignore/Cancel?

---

### Post by darkod on 2013-04-19
Looks good. If you try to open sda1 now from live mode, can you read the data on it?

You still might need to reinstall grub2 on the MBR (I think I posted the command earlier), or even to reinstall a kernel. It all depends if some system files were damaged when the filesystem got damaged, and which ones.

---

### Post by Earl-Grey on 2013-04-19
> **darkod said:**
> Looks good. If you try to open sda1 now from live mode, can you read the data on it?

You still might need to reinstall grub2 on the MBR (I think I posted the command earlier), or even to reinstall a kernel. It all depends if some system files were damaged when the filesystem got damaged, and which ones.

I can actaully see my saved files now! Thank you so much! I didnt think that this was possible.

I would like to try and fix Grub now. Did you mean this command;


sudo fsck /dev/sda1

---

### Post by darkod on 2013-04-19
No.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note that the issue might not be only grub, so that might not make it boot. But it's the first thing to try.

Also, you need to run these commands in a new live session, sda1 should not be mounted before you start. If you did mount it to view files, either unmount it or restart into live mode again.

---

### Post by Earl-Grey on 2013-04-19
sudo mount /dev/sda1 /mnt sudo grub-install --root-directory=/mnt /dev/sda

is the above exactly how I shoud write it, or do I need to change anything?


Please could you tell me the command to un mount sda1 so I can run the command :) 

P.S. I tried Sudo unmount just in case, but it didnt work.

---

### Post by darkod on 2013-04-19
The commands are exactly as I wrote them. They are two commands, execute them one then the other.

If you are using the Nautilus file browser in the live mode, you can unmount a mounted partition by clicking the eject symbol next to it on the left side.

Or simply retart and go into live mode again, sda1 does not get mounted automatically when you boot into live mode.

---

### Post by Earl-Grey on 2013-04-20
> **darkod said:**
> The commands are exactly as I wrote them. They are two commands, execute them one then the other.

If you are using the Nautilus file browser in the live mode, you can unmount a mounted partition by clicking the eject symbol next to it on the left side.

Or simply retart and go into live mode again, sda1 does not get mounted automatically when you boot into live mode.

Thanks again for the advice.

I have tried the commands again and get the below message about the BusyBox;

Target filesystem doesnt have requested /sbin/init.
No init found. Try passing init=bootarg.


BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) build-in shell (ash)
Enter 'help' for list of built-in commands.

(initramfs)

Is there a command that I can try in this mode to load Ubuntu. Do you think I need to install the Kernal? I think that Grub 2 is working now thanks to you :) I get to see the menu to choose linux, but when I select it I get the above message.

---

### Post by darkod on 2013-04-20
At this point I think it's best to make a backup of your personal data, since you can access it now, and then make a new clean installation. It will take much longer to sort out the problem, if you ever manage to sort it out. There can always be some problems left over which will show up in future.

Just copy the data to external hdd and make a new clean install. Then put your data back.

---

### Post by Earl-Grey on 2013-04-20
> **darkod said:**
> At this point I think it's best to make a backup of your personal data, since you can access it now, and then make a new clean installation. It will take much longer to sort out the problem, if you ever manage to sort it out. There can always be some problems left over which will show up in future.

Just copy the data to external hdd and make a new clean install. Then put your data back.

I think that is the best idea. I will make a back up to my USB HDD and then make a clean installation.

Thank you so much for your help and advice!!!

If I could give you some of my coffee beans as points I would do so :popcorn:

---

### Post by girish-ecologikol on 2014-01-13
hi, just ran through this thread,
ubuntu 11.10 on my system is not loading
after trying the live cd to extract the files, it says i dont have the permision to view or copy them
how do i retrieve the data?
please help

---

