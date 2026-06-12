---
title: "Installing Ubuntu onto a USB stick"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by davemar on 2007-09-04
I've seen a few threads about installing Ubuntu FROM a USB stick, but I'm interested in installing TO a USB stick. I've played around with the likes of Pendrivelinux and Slax which run off a USB stick, but they appear to aim to squeeze as much as possible into as small as space as possible and unzip everything. I'm thinking something a bit more conventional can be done where the USB stick is simply treated like a normal hard drive and everything is installed as normal rather than all compressed up. I know there are issues with USB sticks and multiple writing to them, but we'll cross that bridge later.

I've decided to have a go at doing with Ubuntu Server as it's a bit more compact (fewer toys) and it more fits some of the applications I've got in mind. So far I've done this:
1) Got a 1GB USB stick.
2) Added 512 bytes of mbr.bin from extlinux (that's the boot system I aim to use) to the beginning of the stick (using dd).
3) Made a partition with the rest of it and formatted it as ext2.
4) Run extlinux on it.
5) Tried to write an extlinux.conf file (this is where I'm very unsure about, and there's very little good documentation about it).
6) Installed Ubuntu server from CD onto the partition on the USB stick (we'll call sda1 for now), with "/" set to sda1, and no swap space used for now. This seemed to go fine.

With this setup so far, the thing starts to boot up with initrd spitting out it's line of full-stops and vmlinuz doing the same; but then it falls over and restarts the machine. It's clearly getting somewhere before falling over in a heap, so the MBR and extlinux stuff seems to be doing roughly the right thing.

Now I know there are things needed to change to make it boot from a USB stick, but I'm rather stuck at this stage. I'm assuming there are things to change in initrd.img, and I've cpio'ed it and loop mounted it to have a look, but not really sure what to tackle to make this work. There's an init file in the top level of initrd, so I assume there needs to be some jiggling around in there, but don't know where to start.

Does anyone know what I need to tweak to get it too boot? I'm guessing there needs to some sort of USB device mounting and time delays involved somewhere.

Cheers, Dave.

---

### Post by startherepodcast on 2007-09-06
Im trying the same thing at the moment, grub didnt boot for me, but on every other pc i tried... Just try installing grub to your usb hdd in the ubuntu installer (normally /dev/sda). Grub didnt work for my comp at all, so im currently trying your extlinux solution...

---

### Post by Digitbig on 2007-09-06
Is it even possible to boot Ubuntu from a USB drive?:confused:

---

### Post by markp1989 on 2007-09-06
it is possible to put Ubuntu on a usb disk, i tried it before i installed it properly, i just unplugged my internal hard drives and then used the live cd to install Ubuntu to the usb drive.


there is also pen drive Linux, which is based on t he live cd [http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)

---

### Post by davemar on 2007-09-07
As I mentioned, I've played with pendrivelinux, and that worked fine; but I'm really after installing Ubuntu (or a variation on it) instead. There seems to be some differences in installing to a USB memory stick and a USB HD, though not sure what they could be.

I wonder whether the initrd from pendrivelinux can replace the one in ubuntu to make it work on a USB stick?

---

### Post by OliverN on 2007-09-10
let me get this straight: Are you talking about installing Ubuntu to a usb stick drive and booting to that drive, theoretically allowing for a boot to your personal Ubuntu from any pc with a usb port? Is that what you are hoping to do?

If so, then this has got to be made working! God, I want that...

I want it like...

A lot.

---

### Post by davemar on 2007-09-16
Yes, that's exactly what I'm aiming to do.

---

### Post by oomar on 2007-09-16
im just guessing and i am pretty new with linux but have intsallled a host of OSes on stuff. if it is installed properly, it is a BIOS issue. Boot up your computer and press F12, F2, F8, and F1. OR whichever one goes to your BIOS. depends what you got. then go to the boot sequence. from there it will probably have options like Floppy Disks and Internal Hard Drives, and CDs and then if it is a decently new one(within 3 years i would guess) it will say USB device. Set this above everything you want it to boot before and ::POOF:: it should work. OR: try instead of editing your BIOS just go to the one time boot menu and CHOOSE what to boot from ONLY FOR THAT TIME.... though the USB option may not show up then. 

hope it works... i have thought about doin this on my External HDD but never had time.

PM me if this does not work.


SERIOUSLY!!! PM me if it doesnt work. this should be made a sticky if it works cause this is so useful... lol...

EDIT: I am going to try to do what you are on my Ext HDD.

---

### Post by davemar on 2007-09-18
It appears to be more difficult than that. On my machine the BIOS is clearing doing the right thing as the thing does start to boot up, the vmlinuz completes it's installation, and the initrd.img gets going, but bombs out part way through. So it's unlikely to be a BIOS issue.

I'm assuming that something needs to be done in the initrd files, maybe getting the USB stick starting up correctly - though it is clearly being read. I did try replacing the ubuntu initrd.img file with the pendrivelinux version, but that wasn't any more succesful. If I could find out where and why it bombs out when installing initrd.img then it would be helpful.

I also suspect dealing with a usb flash stick might have subtle differences from using a usb HDD.

---

### Post by pxwpxw on 2007-09-18
> **davemar said:**
> It appears to be more difficult than that. On my machine the BIOS is clearing doing the right thing as the thing does start to boot up, the vmlinuz completes it's installation, and the initrd.img gets going, but bombs out part way through. So it's unlikely to be a BIOS issue.

I'm assuming that something needs to be done in the initrd files, maybe getting the USB stick starting up correctly - though it is clearly being read. I did try replacing the ubuntu initrd.img file with the pendrivelinux version, but that wasn't any more succesful. If I could find out where and why it bombs out when installing initrd.img then it would be helpful.

I also suspect dealing with a usb flash stick might have subtle differences from using a usb HDD.
usb sticks and usb hdd enclosures are 2 different animals, the usb hdd has a more complex controller intertface of some sort, whereas the usb flash stick looks more like a giant floppy but can be partitioned to look like a hard disk.
Whether one or both are bootable depends on the hdd enclosure and the pc bios (or apple mac equivalent). If not directly bootable, then almost anything can be indirectly booted using bootloader and kernel images on the internal hard drive, which then mount the external linux file system.
 
Anyway, if your BIOS can boot the bootloader directly from the usb stick as you are doing you are 1/2 way there, and it is probably only the bootloader installation or configuratin on the usb stick that needs work.
Pendrive linux has different configuration to ubuntu so it used extlinux, from my reading (not used here).

 In your case, a straight installation using grub bootloader to the MBR (or equivalent) of the usb stick (i.e. install everything to the usb stick, just like a hard disk install) should work, may need some editing of grub menu.lst, and it is always a good idea to have another grub floppy or cd to sort out any install bugs.

---

### Post by oomar on 2007-09-18
true. if your BIOS seems to be doing it right then it is either software or that ur USB stick is not complex enough to do this. Now while it would be cool to boot off of a USB STICK, i think you should just get the smallest EXT HDD you can find and install it. so much easier and has MUCH more memory. 


But if your heart is set, then i wish all the luck to you. myEXT HDD is bootalbe now so i have your quest completed on easy. your quest just seems to be set on hard.

---

### Post by davemar on 2007-09-19
I decided to have another go at installing it on the USB stick last night, but this time not trying to set up extlinux on it and just let it do it with grub. Everything seemed to install OK, and when I tried booting it up it went into grub, but straight to the grub command line. It completely ignored the menu.lst file. Why would it do this? Is there something I need to set up with grub to get it working here? 

The reason why I want to use a USB flash drive rather than a HDD is no moving parts and complete silence.

---

### Post by dcstar on 2007-09-19
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by pxwpxw on 2007-09-19
> **davemar said:**
> I decided to have another go at installing it on the USB stick last night, but this time not trying to set up extlinux on it and just let it do it with grub. Everything seemed to install OK, and when I tried booting it up it went into grub, but straight to the grub command line. It completely ignored the menu.lst file. Why would it do this? Is there something I need to set up with grub to get it working here? 

The reason why I want to use a USB flash drive rather than a HDD is no moving parts and complete silence.

If you got to a grub command line,  you could use it to manually boot the kernel and initrd from there, or do some checks, and then sort out the problem to boot from the menu.lst.

If you could post a copy of the menu.lst from the usb /boot/grub/menu.lst
that might provide a clue to the problem.

You could get this using the install cd in rescue mode, or a live cd.

---

### Post by davemar on 2007-09-19
Here's the non-commented out parts of menu.lst:

----------------------
default 0
timeout	 30

title		Ubuntu, kernel 2.6.20-15-server
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-server root=UUID=736ae4e0-cf90-4d1b-8c98-7a334e357533 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-server
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-server (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-server root=UUID=736ae4e0-cf90-4d1b-8c98-7a334e357533 ro single
initrd		/boot/initrd.img-2.6.20-15-server

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
--------------------

The USB stick has been partitioned with sda4 containing the installation, to make it USB-ZIP bootable compatible. Maybe this is a problem?

On the grub command line I typed this:
> root (hd0,3)
 ... worked fine
> setup (hd0)
 ... gave this error (can't remember the exact text):
  can't find /boot/grub/stage1.

But /boot/grub/stage1 does exist! What's that all about?

---

### Post by pxwpxw on 2007-09-20
**davemar**

That can be fixed, probably needs menu.lst edited (not yet) and setup grub again using corrected drive/partiton numbers. What have you got on the main drive?

Do not run setup again until you know where everything is, it may zap the wrong thing.

The installer drive numbers can be wrong for the new system when booted i.e. installer says (hd0) but the installed system is (hd1).

These are example results for an external linux root at /dev/sdb2 = (hd1,1)

<TAB> means press the tab key to get a tab completion or a list of possibles
## is my comment

Your numbers and results will be different. Change it for your numbers and then follow this to boot from the grub command line. 

```

grub> root (hd<TAB>
 Possible disks are:  hd0 hd1

grub> root (hd1,<TAB>
 Possible partitions are:
   Partition num: 0,  Filesystem type is fat, partition type 0xc
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> find /boot/grub/stage1
 (hd1,1)

grub> root (hd1,1)

##just note this result for the map, it may need fixing later to reinstall grub.

grub> cat /boot/grub/device.map 
(hd0)	/dev/sda
(hd1)	/dev/sdb

##check the files in the /boot directory using <TAB>

grub> find /boot/<TAB>
 Possible files are: vmlinuz-2.6.20-15-server config-2.6.20-15-server System.ma
p-2.6.20-15-server abi-2.6.20-15-server initrd.img-2.6.20-15-server grub memtes
t86+.bin

## should be able to boot like this, later will fix the grub installation
## use <TAB> completion here to save typing the whole thing. 
## Change the kernel root=/dev/sdb2 to your root partition as found above.

grub> kernel /boot/vmlinuz-2.6.20-15-server root=/dev/sdb2

grub> initrd /boot/initrd.img-2.6.20-15-server 

grub> boot


```

That should tell what needs to be done to fix the setup, if you can post the story.

You should also run from ubuntu ```
 sudo fdisk -l 
```  to see the partition info for the main drive and the usb together.

If it doesn't work, then trash the "USB-ZIP bootable" compatible stick, if that is what I think it is, it has garbage on the drive, for this application.

---

### Post by schambers on 2007-09-20
I followed the directions a couple of days ago here: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), which works fine, albeit a little buggy.

My question is now, I have an 8gb usb stick and the instructions above are basically using a LiveCD from the USB stick which is very slow because of the fact that anytime you access anything it needs to be ungzipped and then accessed.

I want to try now to do a COMPLETE install to a usb drive. So this way, it is basically a complete operating system and not just a modified livecd. I think a complete ubuntu install is around 3gb isnt it? If this is the case then I have more than enough space on my usb stick to do this, i'm just not sure how to go about it.

Has anyone tried this? I don't mean installing a LiveCD to a usb drive, but a complete install to a usb drive.

To respond to other messages on this thread. It is possible to boot off the USB drive, it just depends if your BIOS supports it. You configure the usb drive in such a way that it has a MBR and then bios sees it and boots off it.

---

### Post by pxwpxw on 2007-09-20
> **schambers said:**
> 

1. Has anyone tried this? I don't mean installing a LiveCD to a usb drive, but a complete install to a usb drive.

2. To respond to other messages on this thread. It is possible to boot off the USB drive, it just depends if your BIOS supports it. You configure the usb drive in such a way that it has a MBR and then bios sees it and boots off it.

1. That is what this thread and my post above is about. I have no interest in live cds on sticks.

2. You have answered your own question. The problem addressed in my post above is simply getting the bootloader (grub) configuration fixed up to correcct wrong drive names that happen due to variations between the install and the restart.

---

### Post by schambers on 2007-09-20
ahh hah.

I guess I shouldnt have quickly skimmed through and taken a look.

I'm going to wipe by stick and try this tonight. I will let you know how it goes. I also am going to do a blog post on how to do this. I'm sure theres lots of other people that wouldnt mind doing a full usb install.

What is the complete size of a full ubuntu install? I figured I would partition 3gb for the boot partition and that would be enough.

cheers!!

sean

---

### Post by davemar on 2007-09-23
I decided to have another go at installing on the usb stick. This time I partitioned the stick, so that it had the one partition which is sda1, and formatted to ext2. So pretty conventional.
The installation went smoothly, which was good.

When I booted it up, grub got started and required me to hit 'esc' to get to the menu, which appeared as I would hope. I selected the default kernel to boot into, but things went wrong from here. It sat doing nothing for a couple of minutes (just a flashing cursor) before giving this error:
"Error 18: Selected cylinder exceeds maximum supported by BIOS".

So does this suggest the MBR has been placed not at the beginning of sda?

---

### Post by pxwpxw on 2007-09-24
> **davemar said:**
> I decided to have another go at installing on the usb stick. This time I partitioned the stick, so that it had the one partition which is sda1, and formatted to ext2. So pretty conventional.
The installation went smoothly, which was good.

When I booted it up, grub got started and required me to hit 'esc' to get to the menu, which appeared as I would hope. I selected the default kernel to boot into, but things went wrong from here. It sat doing nothing for a couple of minutes (just a flashing cursor) before giving this error:
"Error 18: Selected cylinder exceeds maximum supported by BIOS".

So does this suggest the MBR has been placed not at the beginning of sda?

( Forget the errors, irrelevant, just due to wrong menu.lst. MBR is by defintion at the start of the disk )
.
Thats good - another giant step forward. The fact you are now seeing the grub menu means it has got past its second stage and found /boot/grub/menu.lst which is on your usb linux root partition. (I am assuming you dont have any other linux/grub on the ijnternal drive). Probably only needs a correction to grub menu.lst -

When it restarts and you escape to the menu, read the help bit, hit "c" for a grub command line, then TAB for help. 
 Now you will beable to  start from the grub command line when you find vmlinuz and initrd. See my post #16  above for details.

For example here on 2 internal drives to see the overall picture:
```

grub> 
grub> root (hd <TAB>
 Possible disks are:  hd0 hd1

grub> root (hd1, <TAB>
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x82
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type is fat, partition type 0xb
grub> geometry (hd1)
drive 0x81: C/H/S = 2434/255/63, The number of sectors = 39102336, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x82
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type is fat, partition type 0xb

```
See post above for more details, you need to understand what you are doing.

When you have done that, you can boot into the usb ubuntu / command line console and edit <sudo nano /boot/grub/menu.lst> (AFTER you save a backup copy) to correct whatever is wrong - this will probably only be the drive (hd1 or hd0), but you can report  what you find and post the relevant menu.lst entry for comment before changing it.
Also, when you get into ubuntu, run < sudo fdisk -l > to see what drives/partitions exist.

Do NOT run setup or any destructive commands from grub.

---

### Post by davemar on 2007-09-24
OK, I followed your instructions and this is what I got:

grub> root (hd0,0)              ..... this is what I expect, there's only the usb stick attached.

grub> geometry (hd0,0)

drive 0x80: C/H/S=999/32/63, The number of sectors=196608, LBA
    Partition num: 0, Filesystem type is ext2fs, partition type 0x83

....and following on with the instruction from your earlier post it went fine up to and including this line: 

grub> kernel /boot/vmlinuz-2.6.20-15-server root=/dev/sda1    ... which completed fine.

...then...
grub> initrd /boot/initrd.img-2.6.20-15-server   ... which then gave the error I had before:
Error 18: Selected cylinder exceeds maximum supported by BIOS

So this is where it's falling over. Is there something in the initrd run-through that's getting lost or stuck? Does this mean I'm going to have to delve into the initrd.img file and fiddle around with scripts within it?

---

### Post by pxwpxw on 2007-09-24
**davemar**


Its a grub/bios/format problem, the message says its having problems loading initrd, its not an initrd run problem. 
But if the initrd i file corrupted or not found that could lead to grub searching beyond the partition limit.
You can check that grub actually finds the initrd
```

grub> root (hd0,0)
grub> find /boot/<TAB>

```
Should list files in boot, but does not show sizes.

It might be a problem with that breed of usb stick, some do have problems and just wont work. Hwever you have established it is bootable and can run grub menu.
All a bit mysterious.

There seems to be some problem with the partitioning on the usb stick, grub error 18, the old bios cylinder limit is 1023 but there are only 999 - its a 1GB stick isnt it? Very old bios have problems there. 

I need more info on your system there and how you are installing in particular how you are setting the usb partition types and sizes, and the partitioning system (lba mbr ? ). Also grub should be able to see the partitions on the internal drive as (hd1) if you have one.

If you have another linux box, or a live cd, you could look at the usb stick partitioning with fdisk  or gparted to see what is going on, and check the boot files in file manager.

> 
grub> geometry (hd0,0)
drive 0x80: C/H/S=999/32/63, The number of sectors=196608, LBA 

I assume the "sectors=196608" is a typo should 10 times that for 1GB=200,000 sectors of 512 bytes.

Also dont know why it is LBA for that size, and with only one partition.

Sorry I cant spot the problem right now, I will try to do another usb stick install here to see what might be wrong and post as soon as I can.

---

### Post by pxwpxw on 2007-09-25
**davemar**

Continued from my last post above.

I have grub booting a kernel and initrd from usb stick in a skeleton test config.
The obvious difference from your result is in the usb drive geometry reported by grub,
I suspect this  is significant, but don't know why you get that result with your installation.

in your case: (the cylinder 999 and head 32 numbers are unusual)
grub> geometry (hd0,0)
drive 0x80: C/H/S=999/32/63, The number of sectors=196608, LBA
Partition num: 0, Filesystem type is ext2fs, partition type 0x83

in my test (using grub and other packages from ubuntu 704, current kernel)

grub> geometry (hd1)
drive 0x81: C/H/S = 125/255/63, The number of sectors = 2015231, LBA
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83


That is the only difference I can see, kernel version is irrelevant here.

However I had to test this on an Apple intel MacBook (i386) as 
I don't have anything that will boot direct from grub on external usb. I don't thnk that matters for this problem.

This is how I set up the usb stick - this was just a test to debug the initrd.img problem, not a full system install.

I have a 1Gb usb flash stick DSE N19XH8306 no garbage, cheap.

it appears as /dev/sdb here, the internal sata is /dev/sda

1. partitioned and format the usb stick with one / root partition.

using gparted (from xubuntu on internal /dev/sda3)

 set disk label = MSDOS, new partition max size 981Mb, primary (default), ext3, round to cylinders.

 Creates Primary Partition #1, ext3 981 Mb on /dev/sdb.
 View Hard Disk info for /dev/sdb
  Disk label type= msdos
	heads 255, sectors/track 63, cylinders 125
	total sectors 2008125  (255 x 63 x 125); 512 byte sectors)
  partition 1 info
	First sector 63 last sector 2008124, totla sectors 2008062.

Check with fdisk.
```

# sudo fdisk -l /dev/sdb

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         125     1004031   83  Linux

```
grub view
```

# sudo grub
grub> geometry (hd1)
drive 0x81: C/H/S = 125/255/63, The number of sectors = 2015231, LBA
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83

```

============
usb1gb flash stick test /boot files
```

root@ubuntu:/home/admax# mkdir aaa
root@ubuntu:/home/admax# mount /dev/sdb1 aaa
root@ubuntu:/home/admax# ls -la aaa
total 32
drwxr-xr-x  5 root  root   4096 2007-09-25 21:47 .
drwxr-xr-x 33 admax admax  4096 2007-09-25 22:39 ..
drwxr-xr-x  3 root  root   4096 2007-09-25 21:42 boot
drwx------  2 root  root  16384 2007-09-25 21:00 lost+found
drwx------  4 root  root   4096 2007-09-25 21:47 .Trash-0
root@ubuntu:/home/admax# ls -la aaa/boot
total 33928
drwxr-xr-x 3 root root    4096 2007-09-25 21:42 .
drwxr-xr-x 5 root root    4096 2007-09-25 21:47 ..
drwxr-xr-x 2 root root    4096 2007-09-25 21:48 grub
-rw-r--r-- 1 root root 6934381 2007-08-13 11:14 initrd.img-2.6.20-15-generic
-rw-r--r-- 1 root root 6804262 2007-08-07 01:07 initrd.img-2.6.20-15-server
-rw-r--r-- 1 root root 6934670 2007-08-13 21:29 initrd.img-2.6.20-16-generic
-rw-r--r-- 1 root root 6952957 2007-08-13 13:34 initrd.img-2.6.20-16-server
-rw-r--r-- 1 root root 1745100 2007-04-15 18:07 vmlinuz-2.6.20-15-generic
-rw-r--r-- 1 root root 1763308 2007-04-15 18:19 vmlinuz-2.6.20-15-server
-rw-r--r-- 1 root root 1746636 2007-06-08 06:58 vmlinuz-2.6.20-16-generic
-rw-r--r-- 1 root root 1764812 2007-06-08 07:10 vmlinuz-2.6.20-16-server
root@ubuntu:/home/admax# ls -la aaa/boot/grub
total 204
drwxr-xr-x 2 root root   4096 2007-09-25 21:48 .
drwxr-xr-x 3 root root   4096 2007-09-25 21:42 ..
-rw-r--r-- 1 root root    197 2007-08-07 01:07 default
-rw-r--r-- 1 root root     15 2007-08-07 01:07 device.map
-rw-r--r-- 1 root root   8660 2007-08-07 01:07 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-08-07 01:07 fat_stage1_5
-rw-r--r-- 1 root root     15 2007-08-07 01:07 installed-version
-rw-r--r-- 1 root root   9152 2007-08-07 01:07 jfs_stage1_5
-rw-r--r-- 1 root root    259 2007-09-25 22:16 menu.lst
-rw-r--r-- 1 root root   4029 2007-08-13 21:29 menu.lst~
-rw-r--r-- 1 root root  10132 2007-08-07 01:07 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-08-07 01:07 stage1
-rw-r--r-- 1 root root 110132 2007-08-07 01:07 stage2
-rw-r--r-- 1 root root   9980 2007-08-07 01:07 xfs_stage1_5

```

You may be able to  try another usb stick variety, or any other suggestion to find what  affects or explains that drive geometry discrepancy. I cant say much more than that with the information I have.

---

### Post by davemar on 2007-09-25
OK, my hardware I'm installing this on is a EPIA ME6000 mini-itx board, and there's no hard-drive, just the USB stick and a CD-ROM for installing Ubuntu from. 

I decided to try it all again on another breed of USB stick, this time a 2GB one. This time on booting, it bombed out before even displaying the menu with Error 18, and no chance of hitting 'c' and trying out some commands. So worse than the other, which at least got as far as the menu. So different usb stick do act differently.

Going back to the original 1GB usb stick, the initrd.img file was detected when using the find command in grub. The number of sectors really was 196608, that wasn't a typo. It does all look a bit weird having 999 cylinders and not sure where 196608 came from, although it is close to what you would expect (i.e in the 200,000 region).

The output of disk -l /dev/sda on this 1GB stick gives:

Disk /dev/sda: 1031 MB, 1031798784 bytes
64 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         984     1007600   83  Linux

... so it shows 984 cylinders, not the 999 that grub reports.

I'm wondering whether it's worth trying two partitions on the usb stick, a small one of say 20MB for a /boot partition and the rest for / . Hopefully this will focus the booting routine on the small partition and get round these Error 18 issues?

There's got to be a way that's robust against different type of usb stick.

---

### Post by pxwpxw on 2007-09-26
**davemar**

Ah, no internal drive, beginning to understand what you have there.

Then I would suspect the BIOS, since grub depends on the bios for its navigation after the usb MBR is booted. However you know a lot more about the EPIA ME6000 mini-itx board than I do.

It could be a very good idea to try the usb stick in another computer, to resolve that issue.

If you used a live cd on the same computer for the "fdisk -l" result it might also be using the same bios info, but different interpretation and a lot of system software to do it - you can also run a grub command line from the live cd ( sudo grub ) dont try booting it though.

The small discrepancies in the various sizes are not a problem, one is for the partiton, one is for the disk and so on.

=========

But I dont understand the 196608 sector figure, this makes the usb stick size 196608 * 512 bytes = 100663296 bytes  i.e. 100Mb not 1Gb
A 10* discrepancy. If grub thinks the disk is 100Mb it will be in trouble.

And from the grub CHS figures this should give the total sectors -
64*32*999 = 2045952 sectors = 1047527424 bytes = correct.

I take this as a symptom that grub is using wrong information about the disk size. Since it is finding the initrd, the problem is in preparing to load it. I assume you never got as far as the 
 grub> boot command. 

========
 
As you suggest, you could try a small boot partition #1 to bring it to the beginning of the drive, yes see if that helps it. You can make a test disk with just the /boot/vmlinuz, initrd.img and /boot/grub files, like the one listed in my last post, but needs another linux to set it up. (it just runs the initrd.img then stops when there is no root system) 

As for the variation between stick breeds, I dont understand it, just accept it. Someone started compiling a list once.

That is all interesting, but as I said -

It could be a very good idea to try the usb stick in another computer, to resolve the bios issue.

---

### Post by davemar on 2007-09-28
I had a go a making a small partition for the /boot directory, with a second large partition with everthing else. I dived into the grub command line to step through the commands, and it successfully got past the kernel install, and also the initrd install (an improvement over previously where it bombed out with the Error 18). Unfortunately when I issued the 'boot' command it just restarted the machine. A rather annoying place to go wrong, with very little diagnostics to draw on.

Unfortuately my main PC (this one I'm typing from now) is pretty old school and doesn't support booting from USB, so I can't try it on this machine. I may attempt it on my work laptop when I get a chance soon. 

I have been partioning and formatting the USB stick using fdisk and mkfs on this machine. However the Ubuntu server installation routine wants to format the partitions again anyway, which I've been allowing it to do.

---

### Post by pxwpxw on 2007-09-29
Progress.

Try boot right after kernel, without loading initrd. Should get a few lines.

Is that ME6000 some weird cpu or otherwise eccentric machine?

---

### Post by davemar on 2007-10-02
I tried boot right after the kernel, and it flashes up "starting up...." (or something similar) for a blink of an eye before rebooting the machine. Not a lot to go on.

The ME6000 is a mini-itx board:
[http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=81](http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=81)

---

### Post by nabeelfa on 2007-10-02
interesting post, I liked the idea of getting Ubuntu from the pocket.....
but is it going to be a very reliable with other PC and its Display card?? or should I use Xbuntu???

---

### Post by pxwpxw on 2007-10-02
> **davemar said:**
> I tried boot right after the kernel, and it flashes up "starting up...." (or something similar) for a blink of an eye before rebooting the machine. Not a lot to go on.

The ME6000 is a mini-itx board:
[http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=81](http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=81)

Ah, I get about 1 screen full, doing same boot after kernel on macintel. I'm reading about mini-itx now.

---

### Post by pxwpxw on 2007-10-02
> **davemar said:**
> I tried boot right after the kernel, and it flashes up "starting up...." (or something similar) for a blink of an eye before rebooting the machine. Not a lot to go on.

The ME6000 is a mini-itx board:
[http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=81](http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=81)

VIA EPIA M-Series Mini-ITX Mainboard

Had a read. Seems to be x86, linux and xp support, award bios, usb booting, all the usual, but I have no experience with minitx boxes, not qualified to comment further.
Dont know what ram size yours has, if it can support XP or Ubuntu Live CD
it should be enough.

We know it works for the install CD, and I think you ran a Desktop Live CD?

At the start with pendrive linux, you were reporting some output from initrd - line of dots, but no text to indicate real progress. You know the ubuntu alt install cd runs and I think the live cd also?

To establish whether grub can run anything  from the usb stick, why not just copy the install kernel and/or the live cd kernel to the usb disk /boot/ and boot them from grub to see if they do any better.

Serverinstall CD   /install/vmlinuz, initrd.gz
Live CD   /casper/vmlinuz, initrd.gz

---

