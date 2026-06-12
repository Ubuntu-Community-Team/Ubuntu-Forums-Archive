---
title: "HowTo: Install Feisty on a bootable USB Flash drive"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by IntuitiveNipple on 2007-06-17
Having just installed a copy of the Feisty Live CD to a Flash drive and found it really easy to do I thought I'd let others know seeing as there seems so much confusion and bad or incomplete advice on how to do it. This procedure **also works for Gutsy LiveCD**.

If you follow all these instructions you'll need a Flash drive with a capacity of 1GB that will end up holding the contents of the Live CD and a separate partition for your persistent data.

Boot to your existing Feisty installation or run from the Live CD. Open an Xterm to type the commands ( Applications->Accessories->Terminal).

Before you get going, disable auto-mounting of hot-plug drives whilst we work to save it getting in the way:
[indent]**System -> Preferences -> Removable Drives and Media:** Storage tab 

disable (untick) the following:
Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted[/indent]
After you've completed these steps you can re-enable these options.
 
If you don't have it already, and aren't working from the Live CD now, download the Ubuntu Live CD (or any other bootable CD ISO image):
```
$ wget http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso
```

We need to install some software to help (some of these are only required when running from the LiveCD - if they're already installed apt-get should ignore them):
```
$ sudo apt-get install mtools lilo nasm libc6-dev netpbm
```
When lilo installs it will pop-up a window advising you to run it after installation - ignore that, it thinks you want lilo to be installed on your hard drive to start Feisty, but GRUB already does that.

We need to download and install the latest version of SYSLINUX. This package provides a boot-loader that will run from a vfat file-sytem:
```
$ wget http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.51.tar.gz
$ tar xzvf syslinux-3.51.tar.gz
$ cd syslinux-3.51
$ make
$ sudo make install
$ cd ..
```
Find out what the device-name of your USB drive is, and use it in these commands where-ever I refer to** /dev/sdX** or **/dev/sdX*y***.

To determine the USB drives in your system:
```
$ ls -l /dev/disk/by-id/ | awk '{ if( $0 ~ / usb-/ ) { split($10,drives,"/"); print(drives[3] "\t" $8); }  }'
sdb     usb-Sony_USB_HS-CARD_F000002619A9-0:0
sdb1    usb-Sony_USB_HS-CARD_F000002619A9-0:0-part1
```
So in my case the drive is /dev/sdb where-ever these instructions refer to /dev/sdX.

Now we can prepare the flash drive. This will wipe out the Master Boot Record (MBR) and Partition Table so make sure you've backed-up anything important.
```
$ sudo dd if=/dev/sdX bs=512 count=1 of=MBR-backup.bin
$ sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1
```
[indent]The first step backs up the MBR and Partition table in case you make a mistake. To put it back use:
```
$ echo "This step only required if you over-wrote the MBR by mistake"
$ sudo dd if=MBR-backup.bin of=/dev/sdX bs=512 count=1
```
[/indent]
Now we can use fdisk to prepare a new Partition Table:
```
$ sudo fdisk -u /dev/sdX
```
[list=1]
[*]Create the bootable partition (press n p 1 <Enter> +750M)
[*]Define it as FAT16 (press t 1 6)
[*]Make it active (bootable) (press a 1)
[*]Create a data partition (press n p 2 <Enter> <Enter>)
[*]Define it as FAT16 (press t 2 6)
[*]Print the Partition Table (press p)
[*]Write the Partition Table to the disk (press w)
[/list]
Unplug the USB drive and then reconnect it. This will allow the kernel to read the new partition table. Check it matches the configuration you just created:
```
$ fdisk -ul /dev/sdX
```
Now we need to write the Master Boot Record to the disk. This is what the BIOS loads when the PC boots. The MBR then reads the boot sector from the active partition, which in our case will be SYSLINUX code (We use lilo rather than grub-install because grub will sometimes write up to 16 sectors of stage-2 code into the 1st track when we only want it to add the MBR boot code in the 1st sector).
```
$ sudo lilo -M /dev/sdX
```
Now we need to create the VFAT file-systems:
```
$ mkfs.msdos -n Ubuntu /dev/sdX1
$ mkfs.msdos -n data /dev/sdX2
```
And let's make partition 1 bootable:
```
$ sudo syslinux -sf /dev/sdX1
```
It is time to mount the USB Flash drive boot partition (if it hasn't been automatically):
```
$ sudo mkdir /media/disk
$ sudo mount -t vfat /dev/sdX1 /media/disk
```
Now extract the files from the Live CD ISO image into partition 1. If you don't have the actual Live CD and have downloaded the ISO, mount it. If you do have the CD in the CD-drive you can skip this step:
```
$ sudo mkdir /media/iso
$ sudo mount -o loop -t iso9660 ubuntu-7.04-desktop-i386.iso /media/iso
```
Copy all the directories and files (including hidden) from the ISO (or CD) to the USB Flash drive.

If you're copying from the ISO:
```
$ sudo cp -r /media/iso/.[a-zA-Z0-9]* /media/disk
$ sudo cp -r /media/iso/[a-zA-Z0-9]* /media/disk
```
If you're copying from the CD (you may need to adjust the name of the cdrom device):
```
$ sudo cp -r /cdrom/.[a-zA-Z0-9_]* /media/disk
$ sudo cp -r /cdrom/[a-zA-Z0-9_]* /media/disk
```
[indent]**Note:** You may well see three errors reported by cp:
```
cp: cannot create symbolic link `/media/disk/dists/stable': Operation not permitted
cp: cannot create symbolic link `/media/disk/dists/unstable': Operation not permitted
cp: cannot create symbolic link `/media/disk/ubuntu': Operation not permitted
```
This is to be expected because the FAT file-system doesn't support symbolic links. However, somehow, when I first went through this process the symbolic links were created as empty files without any error being reported - I'm stumped as to how :)

If you want to see the three symbolic links appear as empty files after receiving the errors above, you can do this:
```
$ dd if=/dev/zero of=/media/disk/ubuntu bs=1 count=0 seek=0
$ dd if=/dev/zero of=/media/disk/dists/unstable bs=1 count=0 seek=0
$ dd if=/dev/zero of=/media/disk/dists/stable bs=1 count=0 seek=0
```
[/indent]

Now rename the boot image directory and files so that SYSLINUX will find them when it boots:
```
$ sudo mv /media/disk/isolinux /media/disk/syslinux
$ sudo rename 's/isolinux/syslinux/' /media/disk/syslinux/isolinux.*
```
and update references in the configuration file to syslinux:
```
$ cd /media/disk/syslinux
$ sudo sh -c "sed 's/isolinux/syslinux/' <syslinux.cfg  >syslinux.cfg2"
$ sudo rm syslinux.cfg
$ sudo mv syslinux.cfg2 syslinux.cfg

```
You should now be ready to try booting from the USB Flash drive.

[indent]** Note** that the menu you see on a CD boot will not show or be used although the entries are in the syslinux.cfg file because the version of isolinux used by Feisty (and Gutsy up to tribe-3) is specially created for Ubuntu to include the optional *[vesa]menu.c32* module that syslinux provides as an external option. I am looking at building an Ubuntu version of syslinux to fully recreate the isolinux experience.[/indent]

Don't forget to remove the iso mount when you're finished with it:
```
$ sudo umount /media/iso
$ sudo rmdir /media/iso
```

If you run the installer from the USB Flash drive it has problems when it expects to find the files it is installing on the cdrom device. There is a work-around for that which involves switching to another terminal (Alt+F2) when the Installer complains and issuing the command:
```
$ mount --bind /dev/sdX1 /media/cdrom0
```
and then switching back to the Installer (Alt+F7) and instructing it to continue. I need to test this thoroughly, so these instructions could change.

There are some changes you can make to the bootable image to allow using the 2nd partition as the home directory for saving documents and settings to. I'll cover those in another article once I've experimented with it fully.

Don't forget to re-enable the hot-plug preferences. 
Hopefully this is enough to get you started.

---

### Post by mwolfe on 2007-06-18
Great tutorial but I think you have a few errors.
First, i had to install nasm in order to compile
```
 sudo apt-get install nasm
```
you might want to include that in the programs needed to get everything working

Second
```

$ sudo cp -r /media/iso/.[a-zA-Z0-9]* /dev/sdb1
$ sudo cp -r /media/iso/[a-zA-Z0-9]* /dev/sdb1

```
I think you want the destination to be /media/disk
not /dev/sdb1 as that is a device.. 


Third
```
rename 's/isolinux/syslinux/' /media/disk/syslinux/isolinux.*
```

gave me an error about privileges. I ran with sudo in front and then it worked.


Last,
for some reason it didnt boot. I get an error on my laptop saying "no partition active"

I'll have to test it on my pc (which is where i formatted the usb disk and everything.. the whole point is to get an OS installed on my laptop which has no working cd/dvd rom) perhaps there are some additional steps to getting it to work on another computer. I'm sure the laptop supports usb boot drives and that the flash drive supports booting from.. but this didnt work yet. I'll have to try it out again tomorrow. 

Oh, and one other thing.
I'm not so sure its a good idea for you to use sdb[number] in your examples. Its real easy for a lazy person such as myself to copy and paste your command and forget to switch sdb with the correct drive for our situation. In my situation sdb is on my system but my usb disk is sdd. I once copied one of your instructions (the one for clearing the mbr) and forgot to change the letter. I think i formatted my mbr on that disk.. Oh well, i know how to fix it if i can't reboot, i'll just use the live cd and install grub again. 

A suggestion would be to use the format

sdx
this way a user won't accidently format the wrong drive unless they have the entire alphabet of drives installed (which is highly unlikely). This of course is not your fault but mine.. Its just that i probably won't b ethe only person to make that mistake. And for a  real newcomer to the linux world, that could be very bad. 

Thank you though for the tutorial, i'll probably be able to get it working tomorrow. I probably missed something

---

### Post by [h2o] on 2007-06-18
Do you really have to run LILO to create the MBR?

I'm having some difficulties installing from USB (not to, USB, but I guess it is related) since my computer refuse to boot my USB stick. I was thinking that this HOWTO might be helpful.

---

### Post by mwolfe on 2007-06-18
ahhhh shoot. when i ran
 sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
as the poster said, it will wipe out mbr and partition table.. i meant to use /dev/sdd

i was thinking that just wiped out the mbr.. this is not good. I had a ton of stuff on that drive. most of which i can live without.. no biggy.. but i did have my photographs, many of which havent been backed up for a couple months.. ouch
Anybody got a clue how i can get that back? Damn i wish i hadnt restarted..it seems everything was working fine until i restarted. The file should all still be in tact as i havent touched the drive and i won't if there is a possibility i can get the data back.
Any ideas?

---

### Post by bluknight on 2007-06-18
Also having installed and assume grub boots it wld it be possible to update it thru synaptic? Or do you have to update then reinstall? I did a regular install to a USB HD 20GB partition and ran everything from it.

---

### Post by IntuitiveNipple on 2007-06-18
Thanks for the feedback.
> **mwolfe said:**
> Great tutorial but I think you have a few errors.
First, i had to install nasm in order to compile
```
 sudo apt-get install nasm
```
 I knew I'd miss something especially with regard to building packages since I use the PC for compiling kernels and have previously had to install packages to support that. Remembering which packages aren't installed on standard systems always catches me out!

> ```

$ sudo cp -r /media/iso/.[a-zA-Z0-9]* /dev/sdb1
$ sudo cp -r /media/iso/[a-zA-Z0-9]* /dev/sdb1

```
I think you want the destination to be /media/disk
not /dev/sdb1 as that is a device.. 

This is strange. I remember actually editing that prior to posting to refer to the mount point not the device! I'll correct it :)
> 
```
rename 's/isolinux/syslinux/' /media/disk/syslinux/isolinux.*
```
gave me an error about privileges. I ran with sudo in front and then it worked.

The famous missing sudo! I work in super-user mode when I'm doing this kind of thing so it is easy to forget to add the odd sudo when translating the commands for user-mode :)
> Last,
for some reason it didnt boot. I get an error on my laptop saying "no partition active"

That would indicate the partition wasn't set to be active using fdisk (press a 1).

> Oh, and one other thing.
I'm not so sure its a good idea for you to use sdb[number] in your examples. Its real easy for a lazy person such as myself to copy and paste your command and forget to switch sdb with the correct drive for our situation.
I thought I should leave something for the user to do :p I take your point though, I'll edit the article and make it an x.

---

### Post by IntuitiveNipple on 2007-06-18
> **mwolfe said:**
> ahhhh shoot. when i ran
 sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
as the poster said, it will wipe out mbr and partition table.. i meant to use /dev/sdd

i was thinking that just wiped out the mbr.. this is not good. I had a ton of stuff on that drive. most of which i can live without.. no biggy.. but i did have my photographs, many of which havent been backed up for a couple months.. ouch
Anybody got a clue how i can get that back? 
Did the /dev/sdb drive have one or more partitions? Was it ext2,ext3, or some other file-system? If it had only one it is pretty easy to recover since in most cases fdisk will set-up the same partition start and end every time.

In the simple case of a drive with a single partition using the entire drive (assume it was not bootable to keep this simple for now) you simply do:
```
$ sudo fdisk -u /dev/sdX
```
[list=1]
[*]Create a new partition (press n p 1 <Enter> <Enter>)
[*]Set its file-system type to Linux ext2/ext3 (press t 1 83)
[*]Print the Partition Table (press p)
[*]Write the table to disk (press w)
[/list]
You may need to reboot to have the kernel recognise the new partition table if this is a fixed disk rather than a hot-pluggable device.

---

### Post by IntuitiveNipple on 2007-06-18
> **bluknight said:**
> Also having installed and assume grub boots it wld it be possible to update it thru synaptic? Or do you have to update then reinstall? I did a regular install to a USB HD 20GB partition and ran everything from...
Don't confuse the two distinct situations, it is a recipe for frustration!

The instructions I've given here are purely to have a copy of the Live CD on a USB drive that is bootable. The primary reason is to be able to carry Ubuntu around easily and run it on a variety of PCs without affecting their operating system installation or writing to their disks.

If you then install Ubuntu from the Live CD/USB drive you're dealing with a full Ubuntu install like everyone else has, and this tutorial no longer applies.

---

### Post by mwolfe on 2007-06-19
disregard post.. look below.. Basically, if you ever mess up your partition tables/mbr, look no further than :
[http://www.cgsecurity.org/wiki/Main_Page](http://www.cgsecurity.org/wiki/Main_Page)

Awesome programs over there.

---

### Post by mwolfe on 2007-06-19
DISREGARD my previous post. I just found an AWESOME utility for recovering a partition.
Now, i shouldnt jump the gun because i havent got the data back YET. but, given what i'm seeing now, this looks very promising
[http://www.cgsecurity.org/wiki/](http://www.cgsecurity.org/wiki/)

I ran the utility and it perfectly detects my partition tables. No ugly formatting or anything like the other program. Not only that it detected them in 2 seconds. I had left this other program, that was not FREE, (demo version) running for 2 hours and it was just crap.. nothing came up but some deleted files from the hard drive that i had lost.. it looked like all the images were from temporary internet files... i couldnt find a single jpeg that was from my hard drive that had thousands of important photos.. 
this other free, open source program, i am able to view all the files in the terminal after it detects the hard drives you can press P and it will list the folder structure and all the files on that partition.
They are all there! Now, i just am a bit scared because i'm so close to getting the data, i'd hate to hit a wrong button.. I'm going to work through it slow. 

But anyways, make sure to pass this program on to anyone who may have screwed up there partition tables or done something similar to me.. I'm not sure if this program can restore files that have been deleted but it may be able to do that as well. Anyways, given i spent hours looking for programs and tried all kinds of free demos, and none of them could detect what this one did in 2 seconds (and many of the others scanned for hours)
If i get my data back, a definite donation to them. Thanks cgsecurity. Oh, and awesome documentation too.. much better than anything else i found. who cares if it uses the terminal, it does so effectively and much better than this gui crap that all these other companies put out.

---

### Post by mwolfe on 2007-06-19
and 10 minutes or so later, here i am with my partitions 100% completely restored. The program detected the partitions perfectly and rewrote the the mbr and partition tables such that it basically was an exact undo of the mess i made. All i had to do was hit enter after it detected the partitions, and then it asks if you want to write the changes to disk.. I selected yes, restarted, and Everything is back working.. I now booted into linux and all my symlinks and everything work still since the partitions are in the same place and everything. 

This is a definite keeper program.. looks like i'm going to have to pay up ( as a donation, but i'll wait for my next paycheck)

---

### Post by mwolfe on 2007-06-19
running the steps you mentioned doesnt work

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.


It always says device or resource busy. I've tried unmounting the devices after i plug in the usb drive and it doesnt matter. It looks to me like they get remounted immediately or something no matter what i do. 
I started the tutorial over from scratch with no luck.. reformatted and copied over the files again and everything.. 
Everytime i seem to get stuck with it saying that re-reading the partition table failed with error 16. 
I also tried rebooting to see if i could use it then and that didnt work either.. Everything else seems to go just fine.

---

### Post by mwolfe on 2007-06-19
alright it looks like i got it.. i had to go into system->removable drives and media
and uncheck:
1.mount removable drives when hot-plugged, 
2.mount when inserted, 
3.browse when inserted
I dont know if you have to do all 3 but i did just in case.. You'll probably want to turn those back on later so that your usb disk will auto mount.

---

### Post by IntuitiveNipple on 2007-06-19
I'm glad you finally got your disk back to normal. What always gets me, that most people don't understand, is that the entire disk is reliant on just ***thirty-two bytes*** of data in the Partition table (the first sector of 512 bytes on a disk) and, *even in these advanced times* no utility think to write a back-up copy of the partition table to the end of the drive (the last sector would be a good choice) to aid in quick repairs!

Maybe I'll add this facility to the fdisk/parted/gparted source code :) 
> **mwolfe said:**
> alright it looks like i got it.. i had to go into system->removable drives and media
and uncheck:
1.mount removable drives when hot-plugged, 
2.mount when inserted, 
3.browse when inserted
I dont know if you have to do all 3 but i did just in case.. You'll probably want to turn those back on later so that your usb disk will auto mount.
I was about to reply to your earlier post telling you of this because it is one thing that constantly annoys me about the default configuration because it interferes with using GPartEd too - as soon as a program rescans the devices the auto-mount grabs them and stops the original program doing its thing!

Whenever I am in maintenance-mode I turn it off to avoid me shouting at the PC in frustration :D

I'll add this to the original article.

---

### Post by offchance on 2007-06-25
well done tutorial. the problem I've run into is that none of the folders created on my flash drive have any content. isolinux and syslinux are totally empty, so the last few steps don't give very good results.

---

### Post by echelon11 on 2007-06-25
Great tutorial, but I've come across a problem.
When I'm attempting to run the line:

```
cd syslinux-3.51
make
sudo make install
```

I'm presented with the following list of errors:
```
ubuntu@ubuntu:~$ cd syslinux-3.51/
ubuntu@ubuntu:~/syslinux-3.51$ make
set -e ; for i in mbr  ; do make DATE=0x466c807b HEXDATE=0x466c807b -C $i all ; done
make[1]: Entering directory `/home/ubuntu/syslinux-3.51/mbr'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ubuntu/syslinux-3.51/mbr'
make DATE=0x466c807b HEXDATE=0x466c807b all-local
make[1]: Entering directory `/home/ubuntu/syslinux-3.51'
gcc  -W -Wall -Os -fomit-frame-pointer -D_FILE_OFFSET_BITS=64 -c gethostip.c
gethostip.c:20:19: error: stdio.h: No such file or directory
gethostip.c:21:20: error: stdlib.h: No such file or directory
gethostip.c:22:19: error: netdb.h: No such file or directory
gethostip.c:23:24: error: sys/socket.h: No such file or directory
gethostip.c:24:20: error: unistd.h: No such file or directory
gethostip.c:25:22: error: sysexits.h: No such file or directory
gethostip.c:27:20: error: getopt.h: No such file or directory
gethostip.c:29: error: array type has incomplete element type
gethostip.c:31: error: ‘NULL’ undeclared here (not in a function)
gethostip.c: In function ‘usage’:
gethostip.c:44: warning: implicit declaration of function ‘fprintf’
gethostip.c:44: warning: incompatible implicit declaration of built-in function ‘fprintf’
gethostip.c:44: error: ‘stderr’ undeclared (first use in this function)
gethostip.c:44: error: (Each undeclared identifier is reported only once
gethostip.c:44: error: for each function it appears in.)
gethostip.c:45: warning: implicit declaration of function ‘exit’
gethostip.c:45: warning: incompatible implicit declaration of built-in function ‘exit’
gethostip.c: In function ‘main’:
gethostip.c:60: warning: implicit declaration of function ‘getopt_long’
gethostip.c:78: error: ‘EX_USAGE’ undeclared (first use in this function)
gethostip.c:83: error: ‘optind’ undeclared (first use in this function)
gethostip.c:91: warning: implicit declaration of function ‘gethostbyname’
gethostip.c:91: warning: assignment makes pointer from integer without a cast
gethostip.c:93: warning: implicit declaration of function ‘herror’
gethostip.c:98: error: dereferencing pointer to incomplete type
gethostip.c:98: error: ‘AF_INET’ undeclared (first use in this function)
gethostip.c:98: error: dereferencing pointer to incomplete type
gethostip.c:99: warning: incompatible implicit declaration of built-in function ‘fprintf’
gethostip.c:99: error: ‘stderr’ undeclared (first use in this function)
gethostip.c:105: warning: implicit declaration of function ‘printf’
gethostip.c:105: warning: incompatible implicit declaration of built-in function ‘printf’
gethostip.c:105: error: dereferencing pointer to incomplete type
gethostip.c:110: warning: incompatible implicit declaration of built-in function ‘printf’
gethostip.c:111: error: dereferencing pointer to incomplete type
gethostip.c:112: error: dereferencing pointer to incomplete type
gethostip.c:113: error: dereferencing pointer to incomplete type
gethostip.c:114: error: dereferencing pointer to incomplete type
gethostip.c:119: warning: incompatible implicit declaration of built-in function ‘printf’
gethostip.c:120: error: dereferencing pointer to incomplete type
gethostip.c:121: error: dereferencing pointer to incomplete type
gethostip.c:122: error: dereferencing pointer to incomplete type
gethostip.c:123: error: dereferencing pointer to incomplete type
gethostip.c:127: warning: implicit declaration of function ‘putchar’
make[1]: *** [gethostip.o] Error 1
make[1]: Leaving directory `/home/ubuntu/syslinux-3.51'
make: *** [all] Error 2
ubuntu@ubuntu:~/syslinux-3.51$ 
```

Any ideas?
Thanks in advance!

---

### Post by IntuitiveNipple on 2007-06-29
> **echelon11 said:**
> 
make[1]: Entering directory `/home/ubuntu/syslinux-3.51'
gcc  -W -Wall -Os -fomit-frame-pointer -D_FILE_OFFSET_BITS=64 -c gethostip.c
gethostip.c:20:19: error: stdio.h: No such file or directory
gethostip.c:21:20: error: stdlib.h: No such file or directory
gethostip.c:22:19: error: netdb.h: No such file or directory
[/CODE]

I ***think*** I know why - its the thing that always catches me out when I write these tutorials!

Because I'm always hacking software I have the GCC development package installed. I think this is your problem in that when trying to compile syslinux it can't find the standard system library header files.

If you don't have the missing files listed in your report  above in **/usr/include/** check if the development headers are installed:
```
$ sudo apt-get install libc6-dev
```
If this works let me know and I'll add it to the instructions. Thanks for the feedback.

---

### Post by jac1d on 2007-06-29
I wasn't the original posted but installing the lib6 stuff helped, but I hit another area.

I ran 
```

make clean
```

then I ran 

```
make
```

And here is the output:
```
make[1]: Entering directory `/home/ubuntu/syslinux-3.51/unix'
gcc -Wp,-MT,syslinux.o,-MMD,.syslinux.o.d -W -Wall -D_FILE_OFFSET_BITS=64 -g -Os -I. -I.. -c -o syslinux.o syslinux.c
gcc -Wp,-MT,syslxmod.o,-MMD,.syslxmod.o.d -W -Wall -D_FILE_OFFSET_BITS=64 -g -Os -I. -I.. -c -o syslxmod.o ../syslxmod.c
gcc -Wp,-MT,bootsect_bin.o,-MMD,.bootsect_bin.o.d -W -Wall -D_FILE_OFFSET_BITS=64 -g -Os -I. -I.. -c -o bootsect_bin.o ../bootsect_bin.c
gcc -Wp,-MT,ldlinux_bin.o,-MMD,.ldlinux_bin.o.d -W -Wall -D_FILE_OFFSET_BITS=64 -g -Os -I. -I.. -c -o ldlinux_bin.o ../ldlinux_bin.c
gcc -Wl,--hash-style=both -s -o syslinux syslinux.o syslxmod.o bootsect_bin.o ldlinux_bin.o
ln -f syslinux syslinux-nomtools
make[1]: Leaving directory `/home/ubuntu/syslinux-3.51/unix'
make[1]: Entering directory `/home/ubuntu/syslinux-3.51/extlinux'
gcc -Wp,-MT,extlinux.o,-MMD,.extlinux.o.d -W -Wall -Wno-sign-compare -D_FILE_OFFSET_BITS=64 -g -Os -I. -I.. -I../libfat -c -o extlinux.o extlinux.c
gcc -Wp,-MT,extlinux_bss_bin.o,-MMD,.extlinux_bss_bin.o.d -W -Wall -Wno-sign-compare -D_FILE_OFFSET_BITS=64 -g -Os -I. -I.. -I../libfat -c -o extlinux_bss_bin.o ../extlinux_bss_bin.c
gcc -Wp,-MT,extlinux_sys_bin.o,-MMD,.extlinux_sys_bin.o.d -W -Wall -Wno-sign-compare -D_FILE_OFFSET_BITS=64 -g -Os -I. -I.. -I../libfat -c -o extlinux_sys_bin.o ../extlinux_sys_bin.c
gcc -Wl,--hash-style=both -s -o extlinux extlinux.o extlinux_bss_bin.o extlinux_sys_bin.o
make[1]: Leaving directory `/home/ubuntu/syslinux-3.51/extlinux'
make[1]: Entering directory `/home/ubuntu/syslinux-3.51/sample'
pngtopnm syslogo.png | \
                ../ppmtolss16 \#000000=0 \#d0d0d0=7 \#f6f6f6=15 \
                > syslogo.lss
/bin/sh: pngtopnm: not found
../ppmtolss16: stdin is not a PNM file at ../ppmtolss16 line 214.
make[1]: *** [syslogo.lss] Error 9
make[1]: Leaving directory `/home/ubuntu/syslinux-3.51/sample'
make: *** [all] Error 2
ubuntu@ubuntu:~/syslinux-3.51$ 
```

---

### Post by jac1d on 2007-06-29
OK, I found the problem... you need the netbpm library if you're running from a naked livecd:

```
ubuntu@ubuntu:~/syslinux-3.51$ sudo apt-get install netpbm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libnetpbm10
The following NEW packages will be installed:
  libnetpbm10 netpbm
0 upgraded, 2 newly installed, 0 to remove and 38 not upgraded.
Need to get 1258kB of archives.
After unpacking 4395kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com feisty/main libnetpbm10 2:10.0-11 [64.8kB]
Get:2 http://archive.ubuntu.com feisty/main netpbm 2:10.0-11 [1194kB]
Fetched 1258kB in 10s (117kB/s)                                                
Selecting previously deselected package libnetpbm10.
(Reading database ... 92929 files and directories currently installed.)
Unpacking libnetpbm10 (from .../libnetpbm10_2%3a10.0-11_i386.deb) ...
Selecting previously deselected package netpbm.
Unpacking netpbm (from .../netpbm_2%3a10.0-11_i386.deb) ...
Setting up libnetpbm10 (10.0-11) ...

Setting up netpbm (10.0-11) ...
ubuntu@ubuntu:~/syslinux-3.51$
```

---

### Post by jac1d on 2007-06-29
BTW, syslinux crapped out building the win32 (windows) binaries, and I can't be bothered to find the error since the unix binaries were built.  However, it does require going in to the unix directory to run syslinux with

sudo ./syslinux REST OF COMMAND FROM TUTORIAL

Also, when running from the liveCD on a single optical drive machine, I did not find the CDROM contents in /media/cdrom, they were in /cdrom when it came time to copy them to the USB key:
```

$ sudo cp -r /media/cdrom0/.[a-zA-Z0-9_]* /media/disk
$ sudo cp -r /media/cdrom0/[a-zA-Z0-9_]* /media/disk
```

Became
```

$ sudo cp -r /cdrom/.[a-zA-Z0-9_]* /media/disk
$ sudo cp -r /cdrom/[a-zA-Z0-9_]* /media/disk
```

Just wanted to pass this bit along for the next guy...

I have to be honest, why the heck isn't there an Ubuntu wizard for USB Instlal on the LiveCD?  The whole purpose of the LiveCD is to help spread the word about ubuntu and let people see and try it without formatting their HD...  To be able to use it or demo it from a USB flash key, as many other distros do, is a fairly useful thing...  This and being able to install properly and easily to a USB HDD would be very welcome.

-Jeff

---

### Post by pavan_bitsgoa on 2007-07-02
first of all thank u verymuch for the guide

but i have a problem though
after following every step when i try booting frm usb hard disk
it gives an error message n starts windows xp normally 
ny comments

n also i think this methood just copies whatever is on cd to the usb drive so i was wonderin if i download ny packages r programs will they be saved on the hard disk or should i download them every time i boot up using this hard disk just as in the case of the live cd??

n ny solutions to my problem i will be glad coz i have been tryin really hard fr abt 3 days now to get feisty installed on my external hdd

btw mine is a 60 gb segate ata hdd if thats required

thanks again

---

### Post by IntuitiveNipple on 2007-07-03
> **pavan_bitsgoa said:**
> 
but i have a problem though
after following every step when i try booting frm usb hard disk
it gives an error message n starts windows xp normally 
ny comments
This isn't the method to use for an external hard-disk. You should install Ubuntu to an external disk drive using the standard Ubuntu installer but ensuring that the PC is set to boot from USB so the USB external drive is seen as the first hard drive, and therefore GRUB installs the boot loader on it rather than over-writing the boot-loader (Windows NTLOADER or whatever) on the internal hard drive.

Once you've installed Ubuntu to the external drive you simply change the BIOS boot-drive selection to USB when you want to use it to boot.

---

### Post by aseem on 2007-07-03
Thanks for a great write-up.

How ever, as with others, I'm not there yet.

I'm using syslinux this to install Ubuntu on a server without CD/DVD.  The server starts syslinux from  from the USB flashm but stops at the "boot:" prompt with the message:  "Could not find kernel image:  liniux"

I have read through another how-to as well, but can't find what I'm doing wrong:  [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

I would appreciate some hints.

---

### Post by IntuitiveNipple on 2007-07-03
> **aseem said:**
> I'm using syslinux this to install Ubuntu on a server without CD/DVD.  The server starts syslinux from  from the USB flashm but stops at the "boot:" prompt with the message:  "Could not find kernel image:  liniux"
Have you tried booting another PC from the USB flash device? If that works then you know the issue is related to the server configuration rather than how you've built the bootable image.

---

### Post by aseem on 2007-07-03
Thanks for the quick reply......

I went through the hole procedure one more time, and then it worked.  Must have missed something. Sorry.

Thanks again for an excellent write-up:D

---

### Post by LynxZ3r0 on 2007-07-06
Here's my query...

Is it possible to get the /home directories to load up on the data partition?  I've got a 4gb drive that I'd like to use to carry around all my user data as well as my files.  I've already got it booting just fine, runs along nice and quick (surprised me), and the data partition is functioning 100% too... I'm just not sure how to get it to mount /home on the data drive (since mtab/fstab are both loaded into the RAM, rather than hardwired).

Thanks for the great writeup, though - Helped a LOT.

---

### Post by IntuitiveNipple on 2007-07-06
I've been experimenting with the steps needed but I haven't got it working yet. I've published the steps I've taken so far here in case someone else wants to explore further. The issue right now is that when the live image starts it creates its own fstab and apparently ignores the one in the squashfs image. I won't have time to investigate this for a week or so.

The bootable file system on the Flash device is contained within the read-only squashfs file **/casper/filesystem.squashfs**. 

**Note:** This assumes you've already mounted the flash CD image at /media/disk.

You'll need at least 2GB of free space to perform these steps. Remember that by design squashfs is a *read only* file-system so you cannot make changes directly to the files as it is currently mounted. You can mount the squashfs using:
```
$ sudo su
$ apt-get install squashfs-tools
$ mkdir /media/flash
$ mount -t squashfs -o loop /media/disk/casper/filesystem.squashfs /media/flash
$ mkdir /tmp/flash
$ cp -r /media/flash/* /tmp/flash/
$ ls /tmp/flash
bin   dev  home    initrd.img  media  opt   root  srv  tmp  var
boot  etc  initrd  lib         mnt    proc  sbin  sys  usr  vmlinuz

```
Now you can edit the files and write changes.

Find the UUID of the data partition on the flash device:
```
$ ls -l /dev/disk/by-uuid/ | grep sdX2
lrwxrwxrwx 1 root root 10 2007-07-06 17:36 468E-6F80 -> ../../sdX2

```
So in this example the UUID is **468E-6F80**.

Now we need to add that to the **/etc/fstab** of the Live system:
```
$ echo "UUID=468E-6F80 /home vfat defaults 0 0" > /tmp/flash/etc/fstab

```
Just check it:
```
$  cat /tmp/flash/etc/fstab
UUID=468E-6F80 /home vfat defaults 0 0
```
Now build the new squashfs image (this will take a few minutes):
```
$  mksquashfs /tmp/flash /media/filesystem.squashfs
Parallel mksquashfs: Using 2 processors
Creating little endian 3.0 filesystem on /media/filesystem.squashfs, block size 65536.
. 
   0 MB .......... .......... .......... .......... .......... .......... 
  60 MB .......... .......... .......... .......... .......... .......... 

...

 600 MB .......... .......... .........
Little endian filesystem, data block size 65536, compressed data, compressed metadata, compressed fragments
Filesystem size 645809.78 Kbytes (630.67 Mbytes)
        36.29% of uncompressed filesystem size (1779628.54 Kbytes)
Inode table size 970700 bytes (947.95 Kbytes)
        27.67% of uncompressed inode table size (3507582 bytes)
Directory table size 984428 bytes (961.36 Kbytes)
        47.57% of uncompressed directory table size (2069428 bytes)
Number of duplicate files found 10856
Number of inodes 102900
Number of files 79698
Number of fragments 8305
Number of symbolic links  12369
Number of device nodes 159
Number of fifo nodes 2
Number of socket nodes 0
Number of directories 10672
Number of uids 1
        root (0)
Number of gids 0

```
[indent]If you don't have the original Live CD or ISO image to hand you might want to back-up the current squashfs on the Flash device:
```
$ cp /media/disk/casper/filesystem.squashfs /media/livecd.squashfs
```[/indent]
Now copy your new file-system onto the Flash device:
```
$ cp /media/filesystem.squashfs /media/disk/casper/

```
Now it is time to test it out by booting from the Flash device. Once it has started check that /home is mounted from the 2nd partition:
```
$ mount
/dev/disk/by-uuid/468E-6F80 on /home type vfat (rw)

```

---

### Post by LynxZ3r0 on 2007-07-06
You sir, are a scholar and a gentleman.  Thank you very much.  Rebooting to test it out right now :)  If it works, enjoy my silence as complete thanks.

---

### Post by MisterD on 2007-07-14
First, a bug...

> **IntuitiveNipple said:**
> 
[indent]```
$ sudo apt-get install mtools lilo nasm libc6-dev netbpm
```[/indent]


You list **netbpm**, but it should be **netpbm**.

Secondly, I can't get syslinux to compile and link, keeps giving me this error. I am using the AMD64 LiveCD, would that make a difference?

[indent]```

gcc -m32 -march=i386 -D__ASSEMBLY__ -c -o e820test.o e820test.s
gcc -m32 -g -o e820test e820func.o msetup.o e820test.o memdisk.o
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
make[1]: *** [e820test] Error 1
rm e820func.s msetup.s conio.s unzip.s e820test.s
make[1]: Leaving directory `/home/ubuntu/syslinux-3.51/memdisk'
make: *** [all] Error 2

```[/indent]

Any help on this appreciated, and thanks for the tutorial!

---

### Post by IntuitiveNipple on 2007-07-14
> **MisterD said:**
> 
You list **netbpm**, but it should be **netpbm**.

Well spotted, corrected, thanks.
> **MisterD said:**
> Secondly, I can't get syslinux to compile and link, keeps giving me this error. I am using the AMD64 LiveCD, would that make a difference?
Very likely. I originally wanted to use 64-bit since the PC is 64-bit but I hit so many problems with incompatible libraries and other miscellaneous bugs that I decided it was best to use 32-bit and actually be able to get work done!

---

### Post by MisterD on 2007-07-15
That was in fact the issue, so anyone contemplating trying this out using the 64 bit version, save yourself some time and get the i386 LiveCD. Although now that I have it working on my USB drive, I might try creating a bootable AMD64 USB drive :) Thanks again for the awesome tutorial!

---

### Post by hank1159 on 2007-07-21
Ok team. Ubuntu - I (a non-technical newb) followed the directions to the end anf they worked.  Good job (I do not think you know how big a complement this is, I have trouble with the beta vcr) However, I cannot get the system to boot from the usb drive to save my life (it is an old tecra laptop that I am attempting to reserct for my sister-inlaw to connect to the internet.

All I have on this pc is a 3&1/2 in floppy.  If I go through the frustration of finding one, is there a way to run enough linux off of the floppy to find the usb drive and install from there?

Any thoughts?

---

### Post by IntuitiveNipple on 2007-07-22
> **hank1159 said:**
> All I have on this pc is a 3&1/2 in floppy.  If I go through the frustration of finding one, is there a way to run enough linux off of the floppy to find the usb drive and install from there?

Booting from floppy is possible and from what I remember of the SYSLINUX web-site there is a variation to support it, but I'm not sure if it can be used to boot-strap a LiveUSB environment.

For a PC to be able to boot from a USB device the PC needs specific support in the BIOS software built into the PC. Almost all recent PCs (2-3 years) have this support but many older PCs don't.

Some PCs might have support built-in but need it enabling in the BIOS setup menus.

Your first step is to enter the BIOS Setup menus at boot-time. Different PCs have different key-combinations to do this. Just as the PC displays the first messages and counts memory  you press the [Del]ete key or (especially laptops) it is the F2 key - if in doubt check the user manual or consult the web.

Once in the BIOS menu you need to check and possibly change two settings. The first is usually on a menu called **Advanced** (although it could be anywhere!) and will say something like:

"**External Boot**" and will have the options [Enable/Disable]. This needs to be set to **Enabled**.

Somewhere else, usually the last-but-one menu, you'll find a way to configure the boot-device order. This controls how the BIOS looks for a boot-record on each device at start-up. BIOS searches the devices in the order given and boot-straps (starts) the PC from the first device in the list that has a valid boot-sector.

The list should be ordered something like this:

Floppy
USB
CD-ROM
Hard Disk
Network

The options you see will likely vary.

If your PC doesn't support USB as an option then I'm afraid that unless the PC manufacturer has released a BIOS upgrade that supports it, you're out of luck (check their web-site for BIOS updates and compare the version reported in the BIOS setup menu with what is on their web-site).

---

### Post by shakyone on 2007-07-23
Fellas, you are doing this the hard way.  Use the live CD.  

I spent this weekend smoothing out how to install Ubuntu 7.04 to a external USB 2.0 hard drive.  The procedure also works for a USB thumb drive, 8GB or larger.  I do not recommend running via a USB 1.1 connection.  You don’t have that kind of time.

Prep work:  
1.  Download the LiveCD iso and burn to CD.
2.  Prep your USB drive by deleting all partitions, no matter what kind they are.  
3.  Disconnect your internal hard drive(s).
4.  Change your system BIOS boot priority by whatever procedure required for your specific hardware, to:
	1.  CD 
	2.  USB
	3.  Hard drive.  

	If you cannot set the USB, because your motherboard is too old, this entire method will not work for you.

5.  Connect the USB drive 
6.  Insert the LiveCD and boot your system
7.  When the Gnome desktop is visible and the Boot is complete select the following pull-downs from the menu:

	System > Preferences > Removable drives & media.

8.  In the Removable drives & media window deselect:

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

9.  Close this window.
10.  Select the Install Ubuntu Icon and run through the install routine steps.  When you get to the step regarding the hard drive, the easiest method is to select Use Entire Disk.
	You can partition out any space you require later.
11.  Run the installation.  Even though the system says it will install GRUB to (hd0) the only drive connected is the USB drive, and it will place it in the right spot.  Choosing sda or anything of that nature is not required when using the new install cd.  It puts it on the right disk, when no other disks are connected.
12.  Restart the system when it is done.

Enjoy.

---

### Post by IntuitiveNipple on 2007-07-23
> **shakyone said:**
> Fellas, you are doing this the hard way.  Use the live CD.
The reason for doing this is to have the contents of the LiveCD on a LiveUSB so it can be used to install Ubuntu on other machines more conveniently.

The use-case expands as people see other uses for it such as the persistent home and so forth.

I agree if you want to a bootable installed system, install to the USB flash device. The problem with it is all the writing to the flash memory quickly reduce its life-span (requiring a block-erase followed by write) whereas a LiveUSB flash device does no writes unless users are saving data or using the persistent home option and therefore the life of the flash device isn't so severely reduced.

---

### Post by phonky on 2007-07-26
Hi all

I badly would like to install ubuntu on my 4 GB flash drive.
However, the tutorial doesn't work for me. 
The flash disk has 2048 sector size and not 512.
After I do all steps, when I mount the disk I get the error

"Can't read superblock"

When partitioning with fdisk, there's always the note below the
two partitions, that the partition does not end on cylinder boundary.

I also already heard that syslinux can't work with sector size 2048.

Does that mean there's no way to make my disk get two partitions
and make it bootable?

That would be quite sad...

Thank you

---

### Post by phonky on 2007-07-27
All information I've found on the internet seems to point to the fact that
only a device with sector size 512 is bootable...Only CD-ROMs have 2048 sector
size, but I assume that these boot in a different manner (isolinux). 

So instead of investing countless hours on this issue, I just invested
20$ in a 1GB mem stick which will do the job...:guitar:

As long as a 4GB drive has 512 sector size, I think it will work.

---

### Post by zenit123 on 2007-07-27
> **shakyone said:**
> Fellas, you are doing this the hard way.  Use the live CD.  

I spent this weekend smoothing out how to install Ubuntu 7.04 to a external USB 2.0 hard drive.  The procedure also works for a USB thumb drive, 8GB or larger.  I do not recommend running via a USB 1.1 connection.  You don’t have that kind of time.

Prep work:  
1.  Download the LiveCD iso and burn to CD.
2.  Prep your USB drive by deleting all partitions, no matter what kind they are.  
3.  Disconnect your internal hard drive(s).
4.  Change your system BIOS boot priority by whatever procedure required for your specific hardware, to:
	1.  CD 
	2.  USB
	3.  Hard drive.  

	If you cannot set the USB, because your motherboard is too old, this entire method will not work for you.

5.  Connect the USB drive 
6.  Insert the LiveCD and boot your system
7.  When the Gnome desktop is visible and the Boot is complete select the following pull-downs from the menu:

	System > Preferences > Removable drives & media.

8.  In the Removable drives & media window deselect:

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

9.  Close this window.
10.  Select the Install Ubuntu Icon and run through the install routine steps.  When you get to the step regarding the hard drive, the easiest method is to select Use Entire Disk.
	You can partition out any space you require later.
11.  Run the installation.  Even though the system says it will install GRUB to (hd0) the only drive connected is the USB drive, and it will place it in the right spot.  Choosing sda or anything of that nature is not required when using the new install cd.  It puts it on the right disk, when no other disks are connected.
12.  Restart the system when it is done.

Enjoy.

I have done all this and Ubuntu works well but I have a problem booting from Ubuntu when the windows internal hard drive is plugged back. Then despite the boot priority order, my computer just boots from the internal hard drive (win xp)

Any ideas?

thanks

---

### Post by Josdell on 2007-08-04
When I try to boot it, it says
Could Not Fine Kernel Image
Boot I've tried this twice, it didn't work. I need help! I'm using a AMD64 Disc to copy from, is this the problem?
Also, is it possible to use the whole thumb drive for a kind of complete computer kind of like a mac mini?

---

### Post by darren_07 on 2007-09-13
you said that you can partition it later... What do you use to do this??


> **shakyone said:**
> Fellas, you are doing this the hard way.  Use the live CD.  

10.  Select the Install Ubuntu Icon and run through the install routine steps.  When you get to the step regarding the hard drive, the easiest method is to select Use Entire Disk.
	You can partition out any space you require later.


Enjoy.

cheers
D

---

### Post by svu on 2007-09-22
Followed your instructions step-by-step. Getting the error trying to boot:

SYSLINUX
Could not find kernel image: linux

What could it be?

---

### Post by poof on 2007-09-28
Just a heads up on the topic:

I am currently writing this reply using Ubuntu 7.10 from a flash pendrive. I used the [_Pendrivelinux USB Ubuntu 7.10 tutorial_]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") which worked awesome.

I am able to add packages, change settings and save/restore everything on reboot. :)

---

### Post by Nooner on 2007-10-02
thanks poof

I'll try that 7.10 tut tomorrow. 

I was using the instructions from 
[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install)
for the 7.04 install all day long with no luck. trying different methods
thought I had it one time cause when I formated it with mkfs.vfat 16...  My XP 
system would not allow me to copy some files to the USB stick, but it would allow me
to copy all the files if I use mkfs.vfat 32... But I think that was a fluke caused by that
particular USB stick cause the others didn't do that 
 
It looks like the USB stick is booting, I get well past the boot menu but then it
stops. and I was getting
 /bin/sh: can't access tty; job control turned off (initramfs)

and when i went to the other terminal (ALT F1) I could see another error
"WARNING: Couldn't open /lib/modules/2.6.17-10generic/modules.dep" no such
file or directory" 

I take that to mean the file system was not uncompressing the 
File system, from the USB stick, into system RAM memory. 

I've tried 3 different sticks and 2 different laptops and always the same results. 
I can boot from the CD, using the same ISO (burned to the CD of course)
that I'm using in the tut, any ideas? 

Looking at the 7.10 tut I notice a "apt-get update"  before "apt-get install syslinux mtools" 
, maybe that it?

I know that it's some thing with the image and not the sticks cause before I was able to 
get both (2of the 3 sticks i have. Went and bought an new one just for this problem)
these sticks to boot the live CD version of knoppix. 

TIA 
Nooner

---

### Post by richiesgr on 2007-10-02
Thanks for this tuturial done without any problem !!!

Now I've the live CD on stick and it's running but only as live CD I would like to run it as real system I've not understand something ??

Thanks

---

### Post by Nooner on 2007-10-02
Hey richiesgr

check out the thread called 
 
"Installing Ubuntu onto a USB stick"

the post was started by davemar

towards the end it talks about live cd vs. an installed system, on a usb stick.
one of the suggestions was to disconnect the H/Ds and then boot from the live CD
then just do an install to the usb stick, looks like you do have to set up the 
stick and the live cd's setting for the stick before you do the install but it looks a lot
easier to set up that way then the way I'm doing it now (live usb stick) 

Me I'm still working on getting the live cd to usb stick to work. 
I like the idea of being able to just stick my stick into anyones system and boot away
if I do it with the install on to the stick then I'll be tied to that systems hardware.
And then there is the idea that the real install on a stick (vs. live CD on a stick)
will ware out the memory stick faster then the live cd on a stick, cause with 
the system on a stick it has to refresh the whole memory in the usb stick for
every change (not just read but write as well) and time you boot. instead of
just the memory on the systems (computer's) RAM. With the live CD on a stick 
you'll just be writing to stick's casper-rw partion and if that section goes bad you
most likely will still be able to boot and run, but some of your setting, specific apps, 
bookmarks, etc will be gone or damaged. But you should still have your basic 
OS there and get to the internet. 

I'm a newbie to this Linux stuff so for me to follow this thread's tut is way out of my league 
so I've been trying to use the tut at  pendrivelinux.com since it easier for me to understand.
I'm familiar with DOS, been with it, way back in the day,  since 2.1 version up to MS 6.22, 
but in DOS there is no case sensitivity and that gets me every time at the command line in 
*unix systems. So the less time I'm at the keyboard the fewer mistakes I make, the less 
frustration, cussing, physical breaking of stuff  

Thanks for sharing
Nooner

---

### Post by dxxvi on 2007-10-04
Hi Nooner,

I think you're right with a live USB stick which is better than a real system on a USB stick. Is there any way to get rid of some packages on the live USB stick and add some other packages to it? I'd like to get rid of all the packages like games, ppp, evolution ... and gnome java and add the sun java 6. If I can do that, that'll be great.

---

### Post by MQMike on 2007-12-07
The tutorial worked on my system.  I did it with Kubuntu 7.04 (from the Live Desktop install CD).

Comments/observations:

I played around a bit as I went through the steps.  I used GParted Live CD to partition the UFD (USB flash drive = sdc1 = (hd2,0)) as Fat16; and I copied the files from the Live Kubuntu CD to the UFD using, as root, Konqueror GUI:  Edit > Copy/Paste.  NOTE: In GUI, you must use View > Show Hidden Files to be sure you get them all!

I re-booted, and noticed what aseem said:

Post #23 by aseem:
"I'm using syslinux this to install Ubuntu on a server without CD/DVD. The server starts syslinux from from the USB flashm but stops at the "boot:" prompt with the message: 'Could not find kernel image: linux'"

I got the same error.  So, I re-booted again, and again once more, and it went OK (and every time after that it was OK).  So I conclude that the hardware/UFD/whatever might be a bit buggy at times.

I fired up the Live Kubuntu from the flash drive.
Kubuntu did not have GParted installed, and although I have GParted on Live CD and on UFD, I decided to use the Live Kubuntu Adept Manager to install GParted in the live ramdisk session.

I then used the newly "installed" GParted to make a new partition, sdb7 = (hd1,6) on my sdb internal hard drive (ext3, 10 GB).

Then I ran the Kubuntu installer.

GRUB:  I selected "Manual" partitioning method in Step 4.  In Step 6, click Advanced button at lower right, and entered (hd1,6) as the place to put GRUB.  That way, GRUB does not overwrite my existing GRUB setup I have for my two internal hard drives.

Installation took--yes--about 10 minutes!

Booting into the new Kubuntu on sdb7:
Upon re-booting, I had to get into the new Kubuntu as follows:
Interrupt my regular, working GRUB boot menu by pressing the "c" key to get a grub>.
grub> chainloader (hd1,6)+1
boot

and off we go into sdb7 Kubuntu.  No problems at all.

***   Thanks to IntuitiveNipple for his good work!   ***

- - - - -

BTW, I have also installed Kubuntu 7.10 to a flash drive as a full, regular install.  I did it exactly as you would install to any drive--no differences; did it both ways: by the Alternate installer and by the Live Desktop CD installer.  The only thing you have to do is the usual GRUB configuring:  I put GRUB in the MBR of the UFD; since I have 2 internal SATA drives, the Kubuntu installer sees the UFD as hd2, so the MBR is named (hd2).   Upon re-booting, you must edit the boot menu so you can boot into your new Kubuntu on the UFD.  It's the usual USB drive-shifting thing:  When used to boot the PC, BIOS names the UFD hd0.  So, on the menu.lst on the UFD, the Kubuntu root is at (hd0,y) (if you put it on GRUB partition y).  My Windows XP is on (hd0,0) which becomes (hd1,0) *as seen from the UFD GRUB*, so you use root (hd1,0), then map (hd1) (hd0) and map (hd0) (hd1), and chainloader +1 to boot into Windows from the UFD.  And so on, to edit the UFD menu.lst.

(BIOS:  Intel Desktop Board D915GAVL.)

---

### Post by MQMike on 2007-12-08
This is strange.  A new situation.

Today, I did a fresh install of Kubuntu 7.10 Gutsy Live CD to a 1 GB flash drive following the tutorial.
Upon re-booting, I get:

The SYSLINUX screen (version, copyright, etc.)
Could not find kernel image: linux
boot:

I tried re-booting a few times but got the same message.
So, I entered the only thing I knew:

boot: /casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz

(this comes straight from the syslinux.cfg2 file)

This worked:  It loads the kernel and the initrd (which takes awhile, several minutes) and boots into the Live CD session; and I tested this several times to be sure.


So, next, I then tried something else:

On the flash drive, in /syslinux folder, there's a syslinux.cfg2 file, as it was renamed in the tutorial here.
I copied that out, renamed it syslinux.cfg, and copied it back in, so now, on the flash drive, in the folder /syslinux, I have two config files:  .cfg2 and .cfg.

This worked:  Now, when I reboot, it all works perfectly, automatically; i.e., I do not have to manually type in any kernel image location.

So, it's fixed, but it doesn't quite fit the case of this tutorial.

---

### Post by MQMike on 2007-12-09
Oops . . .
I figured out I needed to add a command
sudo mv syslinux.cfg2  syslinux.cfg
and then I figured out that I-N already did that but my copy&paste-er didn't grab it!

Also, I posted my experience playing with I-N's tutorial here.  I posted it as a How-To at Kubuntu, positioning it as a re-packaging of I-N's work here and with full credit to I-N.  Hopefully, it will generate some enthusiasm over there and I am hoping to get some of the new users to give it a try and learn/use some Linux skills.

Two things I played with and did differently:
I used GRUB instead of LILO, and demonstrated using a separate, dedicated GRUB partition on the UFD; and I demonstrated some GUI methods to do some of the tasks, just for the heck of it.  I also tried to add a few details and extras for beginners.  This all ties in with some of the How-To's I've done for Kubuntu forums on GRUB and thumb drives.

Again, many thanks to I-N for this do-able and understandable method of putting K/Ubuntu Live on the flash drive!

--Mike

[http://kubuntuforums.net/forums/index.php?topic=3089474.msg104918#new](http://kubuntuforums.net/forums/index.php?topic=3089474.msg104918#new)
Build a LIVE Kubuntu Flash Drive, How-To

---

### Post by MQMike on 2007-12-20
I did the obvious and put both Kubuntu 7.10 Live and Ubuntu 7.10 Live on a 2 GB flash drive, using GRUB to boot both by chainloading to the SYSLINUX boot sector of each OS partition.

The GRUB files in sdc1 got 32 MB (FAT32); I think FAT16 would work, using just 16 MB, but didn't try it.  Each OS would go tight into 700 MB, but 700-750 MB would be safer.  So a total of 1432 MB to 1532 MB is required, leaving space leftover for something else.  If made persistent somehow, there's room for some data/settings on the 2 GB flash drive.
(See same link as in Post #49 above, Reply #1.)

About the only thing that you might be aware of is the need to be patient!
On my system, it took 1-2 minutes for the kernel to load; then another 4-5 minutes for initrd (& ?) to load.  So, about 5-7 minutes before show time. But that's not a big deal. The Live CD also takes some time, so the differential (UFD minus CD) is not the entire 5-7 minutes. Once loaded, both OSs run fine and without issues.

Again, of course, thanks goes to IntuitiveNipple.

(I do have a small, embarrassing Q:  what is the -f option for on the command syslinux -sf /dev/sdxn)?  I can't find anything on it!)

---

### Post by aonegodman on 2007-12-28
"When lilo installs it will pop-up a window advising you to run it after installation - ignore that, it thinks you want lilo to be installed on your hard drive to start Feisty, but GRUB already does that."

This comment should have preceeded the command line entry example.

Now I have installed lilo on my hard drive and need to get it off. How do I reverse this??

](*,)

---

### Post by aonegodman on 2007-12-28
"We need to download and install the latest version of SYSLINUX. This package provides a boot-loader that will run from a vfat file-sytem:"

Why is this necessary? If you are installing from a new distro LiveCD and that's what you want to put on your USB Flash Drive, can't you just copy the existing syslinux off the CD?

I don't understand all the need for added downloading and installing. I guess I just don't want screw up my existing installation on my hard drive anymore in order to get it onto a flash drive.   Just a little frustrated here this morning . . . my lack of understanding. Please excuse me.  :(

---

