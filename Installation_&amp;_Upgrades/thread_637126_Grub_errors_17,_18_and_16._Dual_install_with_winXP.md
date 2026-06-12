---
title: "Grub errors 17, 18 and 16. Dual install with winXP"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by init101 on 2007-12-10
Hi! First linux/ubuntu install...
Please forgive me if this has in any way been covered in a previous post. I'm completely new at linux, and from what I have read on the web the Ubuntu distribution should be the smoothest transition for an "old" windows enthusiast. Although the first installation was a breeze, leaving me quite impressed with Linux, it has now become really frustrating. Hope you guys have some pointers!
Setup:
HP pavilion zt3000 (made sure it would work with linux beforehand)
2gb ram
160gm hd (NTFS partition uses approx the first 130bg)

Install history:
installed with the help of an illustrated stepbystep guide (laugh all you want :) ) and set up partitions manually as per instructions.
On reboot Grub gave me a stage 1.5 Error 17.

Thankfully not the first one to have had that error, so there were lots of posts to help me. (Again - very impressed with this community!) I tried with all the commands I could find regarding how the grub might try and boot from a wrong partition and the like(this seemed to work lie a charm while in the terminal), but when I finally tried to boot with Supergrub, I was told I had an error 18. I ran the xp recoverydisk to "fixmbr", just to make sure windows was still working, and then I tried a fresh installation with the Ubuntu LiveCD. On reboot the Error 17 was replaced with an error 18. Whohoo!

Reluctant to fiddle around with the xp-partition, I tried updating the bios, and a new installation. Instead of the manual partition setup i used the "use free space" option. This landed me the Error 16, and now I am out of ideas.

Any help would be appreciated enormously!

I have seen on many of your posts a request for fdisk -l so just in case:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6f5d6f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16640   133653208+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *       16641       19334    21639555   83  Linux
/dev/sda3           19335       19457      987997+   5  Extended
/dev/sda5           19335       19457      987966   82  Linux swap / Solaris

any other information required I would be happy to supply it.

Oh, and it seems my BIOS settings are rather few and far between, and I have not been able to set hdmode to normal or lba or whatever... In case it makes a difference_

---

### Post by init101 on 2007-12-14
Well i guess its just an old machine, and its something like a cylinderthing. I'll try to move some partitions around :-)

thanks anyway.

---

### Post by Partyboi2 on 2007-12-14
sounds like you are moving through all the grub errors nicely :lolflag:
I don't know if you have looked through the grub page but it covers all the grub errors. Here is the link
[http://users.bigpond.net.au/hermanzone/p15.htm#splash](http://users.bigpond.net.au/hermanzone/p15.htm#splash)
for error 16 this is what it suggests:
> Quoted from the [GNU/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html")16 : Inconsistent filesystem structureThis error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.                                        Try a file system check.

If you have a [GParted -- LiveCD]("http://gparted.sourceforge.net/") you can boot that and right-click on the filesystem you need to check and select 'check' from the right-click menu. That will fix a lot of filesystem problems. A GParted LiveCD is free and only a small download (45 MB or so), and it is almost indispensable.

If that doesn't work or you would rather use your own commands for filesystem checking, see this website's [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm"). Type 'man fsck', 'man e2fsck', or 'man reiserfsck' into an terminal and make up a command with the right options to fix your specific filesystem problems.
                                       
hope this gets you some head way.

---

### Post by 2benglish on 2008-03-05
I am also getting error 16 when trying to boot.

From the live CD I have checked the partition by using GParted. This showed nothing to be fixed.

GRUB is trying to boot from hd(1,2). 

My partition is dev/sdb3.

I have tried other variations for the boot location - (1,0) up to (1,8) These give me Error 18.

What should I try next?

Thanks in advance.

---

### Post by dstew on 2008-03-05
2benglish, please post some information about your computer. Can you tell us how old it is, what processor you have, and your RAM size? What Ubuntu version are you trying to install? Then, open a terminal window in the live CD (Applications --> Terminal) and enter the command```
sudo fdisk -l
```That should display a list of your hard disk partitions. Post that list to the forum. Then we can try to debug your boot problems.

---

### Post by matey3 on 2008-03-05
you know you can hit the escape key at the boot up (grub) time and get into grub menu.

then you can hit the e key to edit each line . edit the first line and see what it says usually (hd0,1) or something like that and if u have scsi hdd then sd0,1 etc..

change the last number after the , comma if its 0 try 1 or 2 or vice versa then hit b key to boot.
keep trying different numbers and different files as well bcs it will point to some files and if those files are not there or the names are different then you get these errors.

sorry  but I am a very new bee myself and dont know much!
but that was one of the very first things i had to figure out when i started this new job... (xen or something changes this menu.lst file in the grub folder and that was what happened to me)...

the amount of knowledge and help in here is amazing. 
good luck.

---

### Post by Nibblyn on 2008-03-05
redundant

---

### Post by 2benglish on 2008-03-05
I have been happily using Ubuntu 7.10 since about a month after it was released. Last week the computer was on for 7-10 days. I turned it off one evening and in the morning, when turning it on, I first had the problem.

My initial reaction was to back up the data (photos) on the hard disk to a USB hard disk. This was partly successful but some of them do not allow me access as I am not logged in as me (using the live CD).

The computer was built in summer 2003 and I replaced the processor in Feb 2006.
The motherboard is an ASUS P4S800. The info in System Monitor tells me I have 503.7MB of memory and 

Processor 0: Intel Pentium 4 2.6
Processor 1: Intel Pentium 4 2.6


Here is the result of sudo fdisk -l


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe36fe36f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000009e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5227    41985846   83  Linux
/dev/sdb2           19460       20023     4530330    5  Extended
/dev/sdb3   *        5228       19459   114318540   83  Linux
/dev/sdb5           19836       20023     1510078+  82  Linux swap / Solaris
/dev/sdb6           19648       19835     1510047   82  Linux swap / Solaris
/dev/sdb7           19460       19647     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order


Thanks for helping!

---

### Post by dstew on 2008-03-06
OK, I see your fdisk output. I need to know a little more about the grub error. When you boot, do you get the grub menu, and then the error after you pick Ubuntu, or do you get the error before you get the grub menu? Is it just an error number with no explanation, or do you get an explanation too, like "Error 16, Inconsistent filesystem structure"?

Anyway, error 16 implies something might be wrong with the filesystem. From the Live CD, do **sudo fsck -a /dev/sdb3** to see if there are any errors on that device.

---

### Post by 2benglish on 2008-03-06
When booting, I get the grub menu and then the error message after I pick Ubuntu.
The message is as you put it:

"Error 16, Inconsistent filesystem structure"

This is the result of the check:

ubuntu@ubuntu:~$ sudo fsck -a /dev/sdb3
fsck 1.40.2 (12-Jul-2007)
/dev/sdb3: clean, 136261/14303232 files, 18846143/28579635 blocks

---

### Post by dstew on 2008-03-06
It seems that the error is with grub's configuration file. The disk does not seem to be corrupt. Perhaps grub is being mis-directed.

Let's have a look at the grub configuration file, which is /boot/grub/menu.lst. Since it is on your Ubuntu hard disk partiton, that partition needs to be mounted to the Live CD file system to access the file. To mount your Ubuntu partiton to your Live CD file system, we need to do two thinks. First, create a mount point using the mkdir command (a mount point is just a directory in the file system to attach the partiton to).```
sudo mkdir /mnt/sdb3
```Then, we mount the /dev/sdb3 partiton to that mount point:```
sudo mount -t ext3 /dev/sdb3 /mnt/sdb3
```If you get any error messages, please post them. Then, you can access the /boot/grub/menu.lst file on your sdb3 partition to read or edit. First, display the file```
cat /mnt/sdb3/boot/grub/menu.lst
```Post the result to the forum. Please post the whole file output, including the top part with the # statements.

---

### Post by 2benglish on 2008-03-06
Just to check...
Is what you asked me to do going to get the same result as if I use the live CD and then go to places/filesystem (select the hard disk in question and then navigate to the /boot/grub/menu.lst file?

I'll do as you ask in a moment, when I get on the computer running Ubuntu.

---

### Post by 2benglish on 2008-03-06
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=36f87e1f-d0a3-43d7-ab66-d5eb8a5bb114 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=36f87e1f-d0a3-43d7-ab66-d5eb8a5bb114 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=36f87e1f-d0a3-43d7-ab66-d5eb8a5bb114 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by dstew on 2008-03-06
> Just to check...
Is what you asked me to do going to get the same result as if I use the live CD and then go to places/filesystem (select the hard disk in question and then navigate to the /boot/grub/menu.lst file?Lol, yes, your way was easier.

From the fdisk, fsck and menu.lst outputs, it looks like grub is configured correctly. The only last thing to check is the /boot/grub/device.map file. Please post the contents.

I am now thinking there may be some hardware problem. Sometimes, a bad cable will give you a problem. That would go along with the grub error 18 when you tried booting other partitions. How old is your computer? If it is newer than 2000, it shouldn't give you a grub 18 error unless there is a hardware issue.

---

### Post by 2benglish on 2008-03-06
device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb

The computer was built in 2003 with all recent components. 

My main concern is backing up the data in /home. Is there any way of logging in as me from the live CD? Is there any way of moving some of the files that I don't have permission for?

---

### Post by dstew on 2008-03-06
> Is there any way of logging in as me from the live CD?I think you can do that. Go to System --> Administration --> Users and Groups. Create a new account for yourself (with administrative privileges.) Then, go to the shut down menu, and chose Logout. Then, log in as the new user. Mount the drive yourself as sudo, and maybe chown the drive to yourself (not sure if that is necessary).

---

### Post by 2benglish on 2008-03-07
You say my way was easier, it's just that I can't get my head around so many of the command line instructions!

It was a great relief to get in and back up my data.

Any more thoughts on what the problem with starting up may be?

---

### Post by dstew on 2008-03-07
The reason some of us use the command line a lot is that it never changes from distribution to distribution, and it always works. Ubuntu is a work in progress, and a lot of the work is making graphical "front ends" that will operate the old command line programs. Some of these new graphical front ends change from version to version, and it is hard to keep up with that. I am not one of these people who always upgrade to the next version as soon as it is available, because if my computer works, I don't like to mess with it unnecessarily. So, I think in "command line" a lot when it comes to configuring a Linux computer.

Glad you got your data. Let me look over the thread again and see if I have any more ideas on your start-up problem. It is an interesting and puzzling problem, so I would like to try to solve it.

---

### Post by dstew on 2008-03-07
[Here]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64928") is a bug report that sounds a little like your problem. It was reported as happening with The Reiser file system, not the ext3 file system, but I think it is worth trying the workarounds, they seem harmless enough (rebooting in recovery mode, or removing savedefault from menu.lst). It seems to be triggered by hibernation. Maybe if you left your system on a long time some power glitch or similar problem might have occurred that was similar. Also, if you have an older kernel, try booting that.

---

### Post by 2benglish on 2008-03-10
I cannot boot in recovery mode.

When using the live CD, again I set my account with the same username and password as is my regular login. Set myslf as an administrator and tried to remove the "savedefault=false" line from menu.lst.

I was unable to do this as I don't have permission.

So I can't get either of these avenues working for me.

It seems odd that the data within the HD is (all) there, yet the booting function is not working for me. I know that I can go ahead with a reload of the OS, but is that necessary at this stage?

If that is the way to proceed, knowing that me data is there, is there any way to make it harmless to configure the new system with all the software that I currectly have? I mean, can I copy these files to another hard disk and then quickly copy them back to the new system?

---

### Post by Jay80 on 2008-03-10
Re: Grub error 18 with dual-boot installs of Ubuntu 7.10 - possible bug:

I've seen a lot of posts saying that the Grub error 18 message is due to having a hard disk that is too
large for the PC's BIOS, but another reason may be that there's a bug in the version of Grub that is
currently supplied with Gutsy.

I only began having intermittent error 18's after installing Gutsy 7.10 on the same 80 GB hard drive
that previously had no problems first with Windows alone, then with a dual-boot of  Windows and
Ubuntu Dapper Drake.  Several removal and auto/manual reinstalls of Gutsy did not resolve this, but
removal of Gutsy followed by a new dual-boot install with Linux Mint did, so the problem in this case
seems to be definitely linked with Gutsy's version of Grub or the way it handles it during a dual-boot
install.

Possibly results will vary with different BIOS's, I don't know, but if it is a BIOS problem I don't see why
it would be intermittent, and why it only occurs with Gutsy 7.10.  I hope someone can shed more light
on the subject.

---

### Post by dstew on 2008-03-11
Jay80, thanks for your post. I think you might be right. My understanding was that grub is not really "versioned", but just an old program that is no longer being supported, but I might be wrong. There are new packages for each new Ubuntu distribution, but I had thought that the basic grub binary was not really changing. Maybe some grub guru out there knows about this. Certainly, if the grub binary is being compiled anew in the gutsy package, there is room for a bug to get in.

---

