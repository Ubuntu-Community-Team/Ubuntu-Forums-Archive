---
title: "Hardy Install - GRUB Error 15"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by notwen on 2008-06-05
My folks who live out of state have been using Ubuntu for some time now, burned Hardy and went through w/ installing over their previous installation.  In doing so they have came up w/a GRUB Error 15. Is there any easy way for them to fix this w/o using command line?  They can point and click easy enough, but trying to talk them through command line over the phone is not something I look forward to.  I'm not all too familiar w/ setting up GRUB or GRUB errors.  I'm guessing GRUB is looking in the wrong place for it's /boot folder.  They're tried the supergrub disk, but it failed to repair GRUB.  I can't seem to find any simple solution for them.  Any recommendations?

---

### Post by dstew on 2008-06-05
Do they get the error before or after the grub menu appears?

---

### Post by Sef on 2008-06-05
This is grub error 15:  > 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

This is a [solved post]("http://sudan.ubuntuforums.com/showthread.php?t=644773"), but would be more difficult that you would like.

Only other option (I know of) would be to use [Super GRUB Disk]("http://www.supergrubdisk.org/").

---

### Post by notwen on 2008-06-05
> **dstew said:**
> Do they get the error before or after the grub menu appears?

According to what they tell me they get

Starting GRUB stage 1.5

Error 15 


-------

And that is all they get.

---

### Post by notwen on 2008-06-05
> **Sef said:**
> This is grub error 15:  

This is a [solved post]("http://sudan.ubuntuforums.com/showthread.php?t=644773"), but would be more difficult that you would like.

Only other option (I know of) would be to use [Super GRUB Disk]("http://www.supergrubdisk.org/").

Yes, I've came across this page w/ my numerous googling, but translating it into layman's terms for my folks over the phone would prove to be very difficult.  They've downloaded the GRUB SUPER DISK and tried the repair GRUB option, but it was not able to, they did not go into detail about the SUPER GRUB DISK other than it didn't work. =\

---

### Post by dstew on 2008-06-05
There are too many different possible things giving this error to figure it out without sitting down at the console and entering commands.

One possibility is that grub was mis-installed, such that the grub boot loader is looking in the wrong place for its stage2 file. This error might also occur if the old grub boot loader is being booted, but the new Ubuntu went into a new partition. Now grub can't find its stage2. Also, after the installation, was the CD removed? Some BIOSes count the CD as a hard disk in BIOS, so maybe grub is looking at the CD for its stage2, which isn't in the same place it is on a hard-disk installed system. Also, the BIOS boot order is sometimes changed in order to boot the CD, and if not changed back, the BIOS may enumerate the disks differently. That could lead grub astray.

I think you have to use the command line to figure it out. You could also just re-install the OS, and see if you have better luck the second time...

---

### Post by notwen on 2008-06-05
They've re-installed twice, they tried re-installing Gutsy and Hardy.  Both come up w/ this error 15.  They have 2 additional storage drives for family pics and music.  I'm wondering if the MBR was installed on separate drive than the one which they installed Hardy over.  Is there anyway to locate the system's current MBR and wipe it, then let my folks re-install Hardy using the new MBR/GRUB settings?  I believe I read that the SUPER GRUB DISK is capable of such a thing.

I'm wanting to keep it as simple as possible for them.  Thanks for your replies as well.  =]

---

### Post by dstew on 2008-06-05
If they really have 3 drives, then grub mis-installation is probably the cause. Clearly, the grub boot loader is in the MBR of the boot disk, because grub starts and gives you the error. The problem is not that grub is not in the MBR. The problem is that grub is mis-configured, so it goes looking for stage2 in the wrong disk partition. It will have to be re-installed.

To re-install grub, you need to boot a Live CD. Open a terminal window and enter grub. That will get you (or your parents!) a grub command line, with the grub> prompt. On the grub command line, enter```
find /boot/grub/stage2
```Whatever it returns, use as the argument in a **root** statement. If it returns (hd0,2), then the root statement should be:```
root (hd0,2)
```Then, setup a new grub boot loader in the boot disk:```
setup (hd0)
```Quit grub, shut down the Live CD, remove the CD from the drive, and reboot. Hopefully you will get a menu.

---

### Post by notwen on 2008-06-05
Three commands over the phone shouldn't be too much trouble.  I'll give them a ring this evening and try it out.  Thanks again for your help and I'll post back our results.  =]

---

### Post by ejpyle on 2008-06-05
Hey guys I know why this happens....It happens to PC's mainly running a SATA as primary and an IDE as secondary......I have 3 PC's all with that type of drive set up and EVERY ONE of them gave that error on bootup. once I corrected the menu.lst to show which one had the MBR my problem was solved. 

Just to test the theory I pulled out the ide on one and connected a SATA...so 2 sata's running, did the install and did not get the error 15.

---

### Post by dstew on 2008-06-05
> once I corrected the menu.lst to show which one had the MBR my problem was solved.That is interesting. What exactly did you do to correct the problem? From the description here, the grub boot loader is not getting as far as loading stage2, or the menu.lst file. So I don't see how editing menu.lst would solve this particular problem. Maybe your problem gave the same error, but had a different cause....

---

### Post by notwen on 2008-06-05
> **dstew said:**
> If they really have 3 drives, then grub mis-installation is probably the cause. Clearly, the grub boot loader is in the MBR of the boot disk, because grub starts and gives you the error. The problem is not that grub is not in the MBR. The problem is that grub is mis-configured, so it goes looking for stage2 in the wrong disk partition. It will have to be re-installed.

To re-install grub, you need to boot a Live CD. Open a terminal window and enter grub. That will get you (or your parents!) a grub command line, with the grub> prompt. On the grub command line, enter```
find /boot/grub/stage2
```Whatever it returns, use as the argument in a **root** statement. If it returns (hd0,2), then the root statement should be:```
root (hd0,2)
```Then, setup a new grub boot loader in the boot disk:```
setup (hd0)
```Quit grub, shut down the Live CD, remove the CD from the drive, and reboot. Hopefully you will get a menu.

After entering your commands, it found the stage2 files on **(hd2,0)** .  My pops was able to get past the initial 1.5 stage and is immediately prompted by a 'Error 15: File not found' error.  He said he could hit any key to continue and it would bring him to the kernel select menu, but trying to open Hardy, Hardy(recovery mode) or memtest would all fall back to the 'Error 15: File not found' error. 

Also he said they've added an additional storage drive which worked fine w/ their previous installation.  I requested his sudo fdisk -l output and here it is.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01c3ba1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004657b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         996     8000338+  83  Linux
/dev/sdc2             997        9839    71031397+  83  Linux
/dev/sdc3            9840        9964     1004062+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e612c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux
ubuntu@ubuntu:~$ 

```


sdc1 is obviously his / dir, sdc2 is /home and sdc3 his swap.

---

### Post by dstew on 2008-06-05
So, the grub menu appears, but each item gives the Error 15, correct? So, now the problem becomes editing the grub menu.lst file to correct the errors. I am trying to think of an easy way to do this. I don't think there is an automatic way.

Here is an easy first step. At the grub menu, instead of pressing 'enter' press 'e' for edit. This should post a list of the grub statements for the first menu item. We might be able to get Ubuntu to boot by quickly fixing that. If your father cannot copy the whole menu item list for you, just tell me what the root argument is. I think it should be (hd2,0). If it is not, you can change it and see if it works. Highlight the root item using the up/down arrows, press 'e' again to edit, change the root argument to (hd2,0), press 'enter', then press 'b' to boot.

---

### Post by ejpyle on 2008-06-06
> **dstew said:**
> So, the grub menu appears, but each item gives the Error 15, correct? So, now the problem becomes editing the grub menu.lst file to correct the errors. I am trying to think of an easy way to do this. I don't think there is an automatic way.

Here is an easy first step. At the grub menu, instead of pressing 'enter' press 'e' for edit. This should post a list of the grub statements for the first menu item. We might be able to get Ubuntu to boot by quickly fixing that. If your father cannot copy the whole menu item list for you, just tell me what the root argument is. I think it should be (hd2,0). If it is not, you can change it and see if it works. Highlight the root item using the up/down arrows, press 'e' again to edit, change the root argument to (hd2,0), press 'enter', then press 'b' to boot.

if it is trying to boot to (hd1,0) then try changing to (hd0,0) <----this was mine. :)

---

### Post by notwen on 2008-06-06
After changing all (hd2,0) options in the GRUB menu.lst to (hd0,0)and booting into his Hardy installation a lot went wrong.  He was complaining about slow response times and eventually everything hard locked.  Upon rebooting, GRUB in itself failed to load.  He said he booted back into a LiveCD session to find his 80GB hdd missing from the partition editor.  So I'm guessing the drive died, which could explain all the earlier issues as well?  He's going to pick up a new drive sometime today.

I'll be sure to post back the final results after he gets the new drive and hopefully gets Hardy re-installed hopefully one last time.  Thank you both for your advice and recommendations on this situation.  =]

---

### Post by notwen on 2008-06-08
After adding a new drive, he was still getting Error 15 after another Hardy installation.  He even went to the extreme and purchased another hard drive just to try.  He and I both are getting pretty frustrated at this point.  I've Googled and browsed most every top link, but I can't make any sense of it.  I'm pretty much hoping someone can post simple commands for me to relay to my folks to get their system back up and running w/ all these new HDDs, lol.  It's been awhile since I've hit a problem I cannot resolve myself, but this whole having to play support tech and troubleshooting this problem w/ my dad via phone for the past week is really beginning to ruin my afternoons/evenings.  PLEASE HELP !! =]  

He's curently added two new drives and has installed Hardy again and is getting GRUB Error 22.  Here's all the info I can think might be useful.   

Here's their menu.lst, /etc/fstab, and sudo fdisk -l outputs:

sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74a674a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+  83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01c3ba1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401   83  Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040d20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1245    10000431   83  Linux
/dev/sdd2            1246        2490    10000462+  83  Linux
/dev/sdd3            2491        2744     2040255   82  Linux swap / Solaris
/dev/sdd4            2745       30401   222154852+  83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e612c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   83  Linux
ubuntu@ubuntu:~$ 

```

menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a4604b63-9bdf-4cd2-9337-f0fde7ac606f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a4604b63-9bdf-4cd2-9337-f0fde7ac606f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a4604b63-9bdf-4cd2-9337-f0fde7ac606f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

/etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=a4604b63-9bdf-4cd2-9337-f0fde7ac606f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd2
UUID=8f257011-f003-4696-83f6-1f6d72a2c42c /home           ext3    relatime        0       2
# /dev/sda1
UUID=a7c5627d-fa37-4523-bbda-89c7d53d6973 /media/sda1     ext3    relatime        0       2
# /dev/sdb1
UUID=d8e6b25d-fc55-4d1f-824a-653ac4e769f2 /media/sdb1     ext3    relatime        0       2
# /dev/sdc1
UUID=15e9bc19-632a-4733-aef5-af5daf69441f /media/sdc1     ext3    relatime        0       2
# /dev/sdd4
UUID=2fc77862-02bc-4942-ba1c-4421071f5bdd /media/sdd4     ext3    relatime        0       2
# /dev/sde1
UUID=ee95df85-a973-4390-87cd-cfac8d3e4d84 /media/sde1     ext3    relatime        0       2
# /dev/sdd3
UUID=685de034-5b02-4489-981f-45e3eaa7e88b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
```

Any recommendations/info you think may be useful please post.  I'm spent =|

---

### Post by dstew on 2008-06-09
Does he get the error 22 before the grub menu comes up, or after choosing a grub menu item?

Does his computer have a FakeRaid BIOS? Are the disks set up as a RAID? That might be one reason grub cannot see them. Grub can only see disks as the BIOS reports them, so if there is some cutting-edge BIOS setting, grub may be blind. You can also get into trouble if you put big disks (greater than 100 GB) into an old computer. The BIOS similarly chokes on this.

The Live CD kernel does not depend on grub to see disks, so the fdisk output is probably accurate.

---

### Post by notwen on 2008-06-09
> **dstew said:**
> Does he get the error 22 before the grub menu comes up, or after choosing a grub menu item?

Does his computer have a FakeRaid BIOS? Are the disks set up as a RAID? That might be one reason grub cannot see them. Grub can only see disks as the BIOS reports them, so if there is some cutting-edge BIOS setting, grub may be blind. You can also get into trouble if you put big disks (greater than 100 GB) into an old computer. The BIOS similarly chokes on this.

The Live CD kernel does not depend on grub to see disks, so the fdisk output is probably accurate.

I believe he gets Error 22 before the GRUB menu.  He said he doesn't even get to the kernel select/memtest screen.  

I doubt he has a FakeRaid BIOS and the HDDs are not setup w/ RAID.  Their PC is not very old, it's a AthlonXP I want to say.  I can verify w/ him this afternoon and post back more details on their BIOS and PC.  After adding these new HDDs, I think he has 2 IDE drives(250GB & 80GB) and 3 SATA drives(500GB, 320GB & 200GB).

He installed Hardy to /dev/sdd

sdd1 being /
sdd2 being /home
sdd3 being swap
sdd4 being /media/sdd4

the other drives are just storages devices being mounted to /dev sdX# matching their device name.  

Thanks again for replying, I'm completely out of ideas and am kinda desperate to get their machine back up because my dad knows enough to want to tinker, but not enough to really research and I just don't have the time to do it thoroughly.  I want to get their machine back up and running before he accidentally wipes one of the HDDs containign data, lol.

Is there any other info you can think of that I can post that may prove useful?

---

### Post by dstew on 2008-06-09
Tell him to re-install grub using the instructions in my post #8. He may get more that one disk in the **find** command output. Post what the find command returns on the forum.

To understand this problem we might need to do some unusual things. Let's take it slow, one step at a time, and try to understand where we are at each step. I see when he re-installed grub before, there was a strange behavior reported, that it gave "Error 15 - File not found" error, and apparently dropped to a command line (?). You say he "continued" (how?) and the menu appeared. This is strange. If something like that happens again, we need to carefully analyse it. It is a clue as to what the problem is.

---

### Post by notwen on 2008-06-09
> **dstew said:**
> Tell him to re-install grub using the instructions in my post #8. He may get more that one disk in the **find** command output. Post what the find command returns on the forum.

To understand this problem we might need to do some unusual things. Let's take it slow, one step at a time, and try to understand where we are at each step. I see when he re-installed grub before, there was a strange behavior reported, that it gave "Error 15 - File not found" error, and apparently dropped to a command line (?). You say he "continued" (how?) and the menu appeared. This is strange. If something like that happens again, we need to carefully analyse it. It is a clue as to what the problem is.

After the 'Error 15  - File not found' if I remember right, he was prompted to press any key to continue and doing this would bring him to the kernel select screen.  Again I'll verify w/ him after work.

---

### Post by notwen on 2008-06-20
> **dstew said:**
> Tell him to re-install grub using the instructions in my post #8. He may get more that one disk in the **find** command output. Post what the find command returns on the forum.

Sorry for the delay in my response, was out of town for a week.  Had my dad re-install GRUB as you wish and email me the output from each command in email.  Each command he entered is **bold**.  Here it is:

**find /boot/grub/stage2**
```
grub> find /boot/grub/stage2
 (hd3,0)

grub> 

```

**root (hd3,0)**
```
grub> find /boot/grub/stage2
 (hd3,0)

grub> root (hd3,0)

grub> 

```

**setup (hd3)**
```
grub> find /boot/grub/stage2
 (hd3,0)

grub> root (hd3,0)

grub> setup (hd3)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd3)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd3) (hd3)1+16 p (hd3,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

```

Thanks again for offering your assistance w/ this.  I'm really surprised my folks haven't fallen back on installing XP Home.  Let me know if you need anything other info that may be of use.  =]

---

### Post by notwen on 2008-06-23
*bump*

---

### Post by VMC on 2008-06-23
It looks like Grub installed okay on your post #21. What happened after he rebooted?

Also, just curious. Why so many hard drives. And also did you find out if he has RAID on his computer.

---

### Post by notwen on 2008-07-01
ALl fo these drives are either storage drives or new drives he's purchased in attempt to get his Ubuntu install up & running again.

After he reboots, he gets the following:

> Error 15: file not found
Press Any key to continue

He hits any key and he is brought to the kernel select screen, where he can select:

Ubuntu
Ubuntu (recovery mode)
memtest

Sorry for the delay, my father is beginning to get tired of it not being an easy fix and tinkers w/ it when ever he feels like it.  Which is not so much lately. =[

---

### Post by notwen on 2008-07-03
*bump*

---

### Post by notwen on 2008-07-06
*bump* 

any one have any advice to offer ?

---

### Post by notwen on 2008-07-09
*bump*

---

### Post by Cap'n Skyler on 2008-07-09
> **notwen said:**
> They've re-installed twice, they tried re-installing Gutsy and Hardy.  Both come up w/ this error 15.  They have 2 additional storage drives for family pics and music.  I'm wondering if the MBR was installed on separate drive than the one which they installed Hardy over.  Is there anyway to locate the system's current MBR and wipe it, then let my folks re-install Hardy using the new MBR/GRUB settings?  I believe I read that the SUPER GRUB DISK is capable of such a thing.

I'm wanting to keep it as simple as possible for them.  Thanks for your replies as well.  =]

go to the super grub disk site and browse the wiki.LOTS of good info there,i think it is staying in my faves for that reason !!:guitar:

---

### Post by notwen on 2008-07-21
Well, I finally just told my dad to backup all of his data onto DVDs and format all drives and start from scratch.  There really needs to be a easier way for someone to identify which HDD has the boot settings on it and to remove it or move it to another HDD.  Thanks for all who tried to help.  =]

---

### Post by Scharpe on 2008-07-24
> **notwen said:**
> There really needs to be a easier way for someone to identify which HDD has the boot settings on it and to remove it or move it to another HDD.
The "boot settings" are in the BIOS - the boot order.  Every drive has an MBR - the BIOS decides *which* MBR to use to boot from.

As far as deciding which MBR has the GRUB loader - that's up to the person installing GRUB to remember.  It's the drive you did the setup to.  (I don't know whether GRUB - or anything else, other than a disk editor - can actually find the MBR that stage1 is installed on.  Assuming it was installed to an MBR, not the beginning sector of a partition [hdx,1 rather than hdx].)

---

### Post by mikesgregg on 2008-07-24
I don't know if you ever figured this one out, but I was having pretty much the same problem as your dad installing Hardy last week.  I checked out this thread and a bunch of others and no one seemed to figure it out.

I finally resolved the problem, but I don't know how much of it was a problem just unique to my hardware setup or if it's more general.  In case you never figured it out, maybe sharing my experience will help.

I'm a Linux novice, so I could be wrong, but I think this is a bug in Hardy. It may only be the 64 bit version though, I'm not sure.  Thats the version I have.  Let me tell you my hardware setup.  It's pretty similar  to your Dad's I think.

I have an Athelon 64 bit processor on an Nvidia chipset motherboard.  I have four SATA hard drives:

My BIOS assigns the drives these numbers:

SATA 1: Windows XP
SATA 2: Ubuntu
SATA 3: My Documents
SATA 4: Backup

Well, I want to use Grub to manage my booting, So I configured my BIOS to boot SATA 2 (Ubuntu) first. Then Windows XP (SATA 1) is the second drive in the boot list. 

Now, when I install Ubuntu, the partitioner lists my drives in a completely different order than my bios...which is weird.  It lists them like this:

sda: Backup
sdb: My Documents
sdc: Windows XP
sdd: Ext 3 (my drive formatted for Ubuntu)

So I install Ubuntu along with grub onto sdd, of course.  Reboot.  Error 15. What the heck?

So I check the menu.list and it appears to be in order (I'm simplifying whats written there as I am not at that computer at this time, so I can't paste in the text exactly):

Menu.list says:

Ubuntu: (3,0)
Windows XP (2,0)

This should be right, right?  Well. I get an Error 15 when I try to boot up Ubuntu, and I can't boot into Windows either.  It says "ntldr missing" or something like that.  So I think maybe, by some fluke, menu.list wants the order that my BIOS looks at the hard drives to boot.  So, since I have my BIOS set up to look for my Ubuntu drive fist, I change Menu.list to:

Ubuntu: (0,0)
Windows XP (1,0)

Now everything boots the way it's supposed to.  So, it's my hypothesis that the grub for Hardy wants the order that your BIOS boots the drive, NOT the order it's listed in "fdisk -l."  I don't know if this is a bug or an intentional change.  I don't even know if that hypothesis is correct.  All I know is that my system works now.  It wasn't a failing hard drive or a corrupted Grub install.....it was as simple as me telling Grub to look for the right disk.

Hope that helps you or anyone else that runs into this.

---

