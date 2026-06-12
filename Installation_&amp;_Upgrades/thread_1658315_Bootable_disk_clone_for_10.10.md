---
title: "Bootable disk clone for 10.10"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by Clive McCarthy on 2011-01-02
I need to make identical Ubuntu machines (with the obvious exception of the hostname).

I have used **dd** to replicate the hard disk from my master machine. This _doesn't_ make the disk bootable :confused:

So next I follow the sundry instructions to get Grub to work. 
I boot from my Ubuntu ISO format installation CD (also *sometimes* known, confusingly, as a "LiveCD") open a terminal and type **sudo grub**.

Those instructions must be old because Grub isn't installed!

OK:
**sudo apt-get install grub** fine, but where did it get installed? Nevermind...
Next:
[B]sudo grub
find /boot/grub/stage1[/B]

No luck... not found. So forget the rest of those instructions.

Plan B[SIZE="1"]-1/2[/SIZE]:

I've read **The Grub 2 Guide** but, though it seems thorough, it isn't that helpful (too much information about the merits of Grub 2).
The instructions start with:
**sudo fdisk -l**
and
**sudo mount /dev/sda1 /mnt**
which wants to know the filesystem type. I guess ext3 -- maybe?
I stopped at this point.

I'd appreciate some help. This should be easy -- this is a single-boot installation and I just need to get the boot-loader installed on the duplicate drive.

---

### Post by dino99 on 2011-01-02
actual release(s) are loaded by grub2 (grub-pc package), not by the old grub1 (grub-legacy), so that cant work with "grub", use grub-pc (might need to remove grub, menu.lst first)

---

### Post by Clive McCarthy on 2011-01-02
Sorry, as they said in one Monty Python episode: "I don't understand your banter".

---

### Post by oldfred on 2011-01-02
I think what dino was saying is that you have made things worse by adding grub to grub2 and they do not get along. You should only have one or the other and should uninstall grub and keep grub2 (grub-pc is package name).

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Do you have both original drive & dd'd drive plugged in? You will have problems as UUIDs are unique (or supposed to be), but when you use dd to copy you have copied the drive's UUIDs so now grub sees two identical UUIDs and gets confused.

---

### Post by Clive McCarthy on 2011-01-02
No I don't have the master AND the dd'd drive installed. As soon as the copy completed and the machine was shutdown, I unplugged the master's SATA cable. So I am now simply trying to boot the clone.

Curiously, it was the Ubuntu 10.10 ISO CD that suggested I install grub -- it didn't suggest grub-pc.

---

### Post by oldfred on 2011-01-02
The last Ubuntu that installed grub legacy(0.97) was 9.04. But upgrades or manual installs still can use grub legacy.

Some of us still call grub2 grub, but mean grub2. I do not know where in the 10.10 ISO you would see a reference to grub legacy as the version is grub version 1.98.

fred@fred-LT-A105:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
fred@fred-LT-A105:~$ apt-cache policy grub-pc
grub-pc:
  Installed: 1.98+20100804-5ubuntu3
  Candidate: 1.98+20100804-5ubuntu3
  Version table:
 *** 1.98+20100804-5ubuntu3 0

---

### Post by Clive McCarthy on 2011-01-02
The way that drs305 writes instructions is quite convoluted:

[INDENT][I]From the Live CD:

If the Ubuntu OS cannot be accessed through the normal boot process (see above), boot a compatible installation CD/Live CD. The Grub 2 files are by default installed in the partition's /boot/grub folder and will be placed in this folder if the commands are run as instructed. 

Note 1: Running "update-grub" from the Live CD will not update the grub.cfg file of the normal installation. If the grub.cfg file is damaged or missing, the user should use the chroot procedure below to update the grub.cfg file.
Note 2: In the following commands, the Ubuntu partition (sda1, sda5, etc) is mounted in the first command, but only the drive (sda, sdb, etc) is designated in the 'grub-install' command.
Note 3: The middle commands are to be run only if the operating system has a separate partition specifically for /boot. This would normally not be the case.

If you have a separate /boot partition run these two commands first. Most users do not have a separate /boot partition. sdXZ is the boot partition.

Code:
### Run these two commands only if you have a separate /boot partition
sudo mkdir /mnt/boot
sudo mount /dev/sdXZ /mnt/boot  # Example: sudo mount /dev/sda6 /mnt/boot
Code:
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdX # Example: sudo grub-install --root-directory=/mnt /dev/sda[/I][/INDENT]

He/she writes 'notes' in the middle of his/her explanations which makes understanding MUCH more difficult. And he/she writes with conditional clauses with no explanation how one my determine if the clause applies. How would I know if I "have a separate /boot partition" for example.

**[COLOR="Red"]sudo mount /dev/sdXY /mnt [/COLOR]**
fails and asks for a filesystem type but rejects -t ext4 anyway.
However, fdisk identifies the cloned HDD as /dev/sda

---

### Post by Jahid65 on 2011-01-02
If you want a clone of your ubuntu installation. use Remastersys. Search for "remastersys" in the forum. You will get many post about this.

---

### Post by Clive McCarthy on 2011-01-02
I'm going to try **Rescatux** -- though it seems like there ought to be an easy way of slamming a boot record on a disk...

Well, Rescatux didn't do it.

---

### Post by oldfred on 2011-01-02
If when you installed you did not specify a separate /boot then you probably do not have one. It is unusual now for standard desktops.

[I]sudo mount /dev/sda5 /mnt

You typed the above but with the drive & partition that you have Ubuntu installed not the XY where X is drive & Y is partition??  You should not get the error on asking for type.
[/I]

---

### Post by Clive McCarthy on 2011-01-02
I'll give remastersys a try. It looks _very_ promising. I presume it keeps all the installed drivers etc. but I wonder how much user data it can transfer via a bootable CD.

It potentially can get me a cloned machine in a single step. I will report back.

---

### Post by Clive McCarthy on 2011-01-02
Thanks for the suggestion, however, it seems that **remastersys** doesn't handle proprietary video drivers :(

It will help me get basic clones of my master machine but I'll still have to run custom scripts to get the whizzy Nvidia drivers installed.

---

### Post by Clive McCarthy on 2011-01-02
Seems I'm not having much luck. Clearly I was originally hoping for a quick **dd** of a master HDD (with all the drivers) and simple edit of /etc/hostname.

I still don't see why:
[COLOR="Blue"][INDENT]sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt/boot[/INDENT][/COLOR]
doesn't work.

It would be very useful if there were a way to install the grub2 boot on a _second_ HDD.

I could then write a script to handle the **dd** from the master drive to the clone and script the installation of the grub2 boot to the new HDD. Wham bam, I could crank out half a dozen bootable systems in no time... :guitar:

So with a running system booted on /dev/sda with a second HDD /dev/sdb

I tried:
[COLOR="Blue"]**sudo grub-install /dev/sdb --no-floppy**[/COLOR]
and it reported no errors.

But when I unhook the boot drive and boot with just the clone it drops into **grub rescue>**

So next I have tried mounting the clone drive with the intention of copying the Grub2 files to the clone HDD.
[COLOR="Blue"][INDENT]sudo mkdir /media/clone
sudo mount /dev/sdb1 /media/clone[/INDENT][/COLOR]
and I get a message saying I must specify the filesystem type, so I do
[INDENT][COLOR="blue"]sudo mount -t ext4 /dev/sdb1 /media/clone[/COLOR][/INDENT]
and I'm told it's the wrong fs type or a bunch of other possible errors...

---

### Post by oldfred on 2011-01-02
When you did the dd command I would have expected it to have copied the MBR.

This is the dd commands for the MBR. You have to be extremely careful as the partition table is usually unique. But if you have cloned the drive, I would expect partition table to be exactly the same. If you did not copy MBR you may not even have a partition table and reinstalling grub will not work. Boot code is in the first 446 and the rest is primarily the partition table.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")
Backup the MBR e.g. Change sda if not correct.
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1
Erase - Make double sure you have correct drive & partition
Zero out MBR and partition table
dd if=/dev/zero of=/dev/sda bs=512 count=1

---

### Post by Clive McCarthy on 2011-01-02
Yes, I was hoping and expecting a real "image" copy using dd so I didn't expect I'd have to fiddle with the boot record at all.

I have just run:
[INDENT][COLOR="Blue"]dd if=/dev/sda of=/dev/sdb[/COLOR][/INDENT]because I may have done
[INDENT][COLOR="blue"]dd if=/dev/sda1 of=/dev/sdb1[/COLOR][/INDENT]previously.

Thanks for commenting on this. I will report back if the MBR is now in place.

---

### Post by Clive McCarthy on 2011-01-03
Good news! It took a long, long time for **dd** to clone the 250GB disk but when I boot it now, it thinks it's the other disk. Looks like the MBR is copied faithfully.

A quick edit of the /etc/hostname file and I'll have a cloned and renamed machine. This is a mini-production process: I'm making six copies of a fully configured machine with Nvidia proprietary drivers and a scripted boot sequence that runs immediately on power-up. The disks all run on the same hardware platform so the drivers etc. and configuration options are all the same.

Thanks for all the various suggestions. Using **dd** is a good way to make a cloned backup of a HDD. The 250GB drives only cost $50 so it's a cheap and certain way to go.

**[COLOR="Red"]*** Caution ***[/COLOR]** You can't trust that /dev/sda is your 'master' drive and that /dev/sdb is the target clone. It can be the other way around depending how the BIOS set things up so be sure they are the correct way around otherwise you might make a perfect clone of a blank disk!

---

### Post by ckilger12 on 2011-02-21
thanks for posting up Clive....i just bought a new HD for my notebook and I want to clone it so i dont have to recustomize my system. Glad to see the 

dd if=/dev/sda of=/dev/sdb

worked copying the MBR and all...good deal

---

### Post by Clive McCarthy on 2011-06-05
I'm glad you found the post useful. However, I did find some flakiness with HDDs cloned in this way. I finally broke down and bought an $80 HDD duplicator (Aluratek AHDDUB100) which has proven to be money well spent.

---

### Post by ArvidZHK on 2012-08-08
Bootable disc or Bootable disk?
If the post means the boot CD,
we need to build PE.
If not, why the disk would be not bootable?
It's always bootable while I restore 
my data from [disk clone]("http://www.pcdisktools.com/pcdiskclone.htm").

---

