---
title: "Lost Windows 2000"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by SoUS on 2008-04-27
Hello from the south.

Sorry for being so ignorant in this matter, but while trying to install ubuntu on a separate drive from my Windows 2000 drive, I seem to have lost my C: drive, which is (was?) Windows 2000. That 200 mb drive had 2 partitions (C: and D) and the spare drive I had was drive E:. When installing umbuntu, it said I could run it on that separate drive (or partition) along side Win 2000. During the install, I made sure the small spare drive was selected, but I suppose I missed something around that point. When the PC rebooted, all I had was the umbuntu loading and no choice for Win 2000. 

Now I'm desparate and feeling pretty foolish. I popped my Win 200 hard drive out of that box and stuck it in a Win XP machine here and the drive shows up but says it's not formatted. (No, I did not tell it to format.) I have a demo for a fairly expensive undelete, unformat utility and it sees my whole Win 2000 C: drive. I recon I can use a utility like that to recover somethings like my check book, photos and emails.

I've read around on here and see posting(s) on using mbrfix to recover or repair master boot record. I ran "mbrfix /drive 1 listpartitions" and it looks like it sees both partitions on that 200 mb drive. 

I really don't want to do more than one dumb thing in one day, so I'm going to stop here for the night. Any suggestions or assistance in this matter would be very, very much appreciated.

I'm sure I can put both these drives back in that box and load back into umbuntu, if that's nesessisary to troubleshoot or back out of this problem. 

Thank you very very much, in advance, 
SoUS

P.S., If anyone knows what I may have done wrong, I may still try this again. I like the looks of this Linux install, so I really do want to explore some more with unbuntu. 

Thanks again.

---

### Post by bobnutfield on 2008-04-27
Hello,

I'm very sorry you are having such difficulty on your first attempt with Ubuntu.  But, before we completely decide that the Win2000 partition has been written over, there are some things you can check.

If you are able to boot into Ubuntu, you can open a terminal (this can be found under Applications>Accessories>Terminal).  Once there, type in the command:

```
fdisk -l
```

This will list all of the disks and partition that are recognized in Ubuntu and list what file system their partitions are. You Win2000 should show up as an NTFS filesystem.  If you followed the install instructions, it is difficult to lose a partition with an operating system on it unless Ubuntu is specifically instruction to use that partition OR instructed to used the ENTIRE disk.  That is the most common error that I have seen is when Auto partitioning is chosen instead of Manual to select the partition you want to install Ubuntu to.

Are you getting the Grub boot menu when you start the computer allowing you to select between operating systems?

The people on this forum will help you any way they can and hopefully help you recover what you need.

Bob

---

### Post by felker2 on 2008-04-27
When in Ubuntu, can you see any Windows partitions? For example, my Windows partition is on /dev/sda, which I can check with:

```
sander@fujitsu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee3cee3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8454    67906723+   7  HPFS/NTFS
/dev/sda2            8455        9548     8787555   83  Linux
/dev/sda3            9549        9729     1453882+  82  Linux swap / Solaris
sander@fujitsu:~$
```

As my Windows is on /dev/sda1, I checked to see it's mounted:

```

sander@fujitsu:~$ mount | grep sda1
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
sander@fujitsu:~$

```

Yes, it is. 
And contents are viewable with "ls -al /media/sda1".

---

### Post by sandysandy on 2008-04-27
yours could be simply an issue of adding an entry of windows to the UBuntu's menu.lst file so that the GRUB gives u both options to boot.

post out put of 

[COLOR="Blue"]sudo fdisk -lu [/COLOR]  and

[COLOR="Blue"]gksudo gedit   /boot/grub/menu.lst[/COLOR]

regards

---

### Post by SoUS on 2008-04-27
Thank you both for these tips. 

Yes, I get the GRUB boot menu, but Win 2000 is not there. I will put the drives back in that PC in the morning and try the fdisk -1 in the terminal window. 

I did select that specific drive/partition when installing umbuntu. 

You people are all great. Thanks very much. I have to sleep now before I cause more trouble. I'll check back in here in the morning before proceding further. 

I am new to Linux, so this is going to take me a bit to get through this. I can not beleive I did not remove my Win 2000 drive when I did this. Perhaps you can or can not imagine what I've lost. Even though I'm very tired, this is going to be a sleepless night.

Thanks again in advance for all thoughts/suggestions. 
SoUS

---

### Post by SoUS on 2008-04-27
As stated, I'm new to Linux. I'm assuming I enter these commands in the terminal window?

post out put of 

sudo fdisk -lu and

gksudo gedit /boot/grub/menu.lst

Thanks Sandy.
SoUS

---

### Post by sandysandy on 2008-04-27
> **SoUS said:**
> As stated, I'm new to Linux. I'm assuming I enter these commands in the terminal window?

post out put of 

sudo fdisk -lu and

gksudo gedit /boot/grub/menu.lst

Thanks Sandy.
SoUS

thats right

regards

---

### Post by SoUS on 2008-04-27
Looks to me that umbuntu is only seeing 32mb of my 200mb drive. Also only showing one partition? I'm not exactly positive, but believe my C: drive was NTFS and the D: partition FAT32. Not positive with that, but I used mbrfix to list the partitions on that drive last night and I think that's what it was showing. 

I currently have the 200mb drive (was C: & D: of my Win 2000 machine) and the 8.5gb drive back in my machine. I'm currently on the net in umbuntu. (I figured out how to install my netgear wireless adapter.)

```

SoUS@SoUS-desktop:~$ sudo fdisk -lu 

Disk /dev/sda: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders, total 66055244 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           9    16434494     8217243   54  OnTrackDM6

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3488226

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    15711569     7855753+  83  Linux
/dev/sdb2        15711570    16498754      393592+   5  Extended
/dev/sdb5        15711633    16498754      393561   82  Linux swap / Solaris

```

I'll try and post the outputs from these other commands suggested here in a few minutes. I desperately need to get my Windows 2000 back and running.

Just can't believe I was so foolish last night. Trying to not cause any more damage.

Thanks,
SoUS

---

### Post by SoUS on 2008-04-27
Hope this works. Here's the output of the gksudo gedit /boot/grub/menu.lst command. (How do you people get these outputs in those nice "code" boxes?)

```

 menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=089e547e-3eb3-44eb-9233-097eb3fcb769 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=089e547e-3eb3-44eb-9233-097eb3fcb769 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=089e547e-3eb3-44eb-9233-097eb3fcb769 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by SoUS on 2008-04-27
Any suggestions at all would be much appreciated. If I can do anything to reverse or uninstall ubuntu and restore my windows 2000 install, that's exactly what I think I should be doing. I can come back and do the ubuntu dual boot install after more research and back ups of the the Windows 2000 disk. 

Getting back into W2000 is a must. Even if the info on my D; drive were lost not as big a deal, but I need to restart W2000 for some very important stuff.

Please help. Severe depression is setting in. 

Thank you,
SoUS

How could I have been so stupid? I played with the live CD and liked what I saw. I set up this spare hard drive in my PC to do the ubuntu install and one of the first install screens made it sound as if there was no problem setting up ubuntu along side my current Windows installation and would be able to use either one. What ever I could have done wrong, it would have been nice if this installer asked if I was sure. 

I hope I'm not doing further harm, running in ubuntu and browsing the web.....

---

### Post by ayampanggang on 2008-04-27
if you don't see NTFS filesystem as you entered sudo fdisk -l, this one's example from my HDD layout:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   83  Linux
/dev/sda2              16          66      409657+  82  Linux swap / Solaris
/dev/sda3              67       15971   127756912+  83  Linux
/dev/sda4   *       15972       19457    28001295    7  HPFS/NTFS --> a NTFS filesystem, your windows partition

```
then i'm afraid you might have overwritten it with your ubuntu installation.

i really really hope i'm wrong with this one since i know how stressful it can be.

best of luck for you.

---

### Post by SoUS on 2008-04-27
I'm not sure what I'd have done to overwrite my ntfs drive/system. From the code below, doesn't it look like I installed to the 8.5gb drive? 

The only other thing I see, is that "Disk /dev/sda" line ends with Ontrack. That utility loads when my PC boots, right after the BIOS stuff finishes. Westerndigital and Seagate use that for some reason so Windows(?) or certain motherboards can see the whole drive? I wonder if that threw a wrench in the works. 

Assuming the data is not overwritten, perhaps any steps that can be takes to uninstall ubuntu and restore/recover Widows is the direction I need to go. 

I'm scared to, but fixmbr is tempting. I don't want to cause further damage at this point though, not knowing exactly where or what went wrong.

```

SoUS@SoUS-desktop:~$ sudo fdisk -lu 

Disk /dev/sda: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders, total 66055244 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           9    16434494     8217243   54  OnTrackDM6

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3488226

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    15711569     7855753+  83  Linux
/dev/sdb2        15711570    16498754      393592+   5  Extended
/dev/sdb5        15711633    16498754      393561   82  Linux swap / Solaris

```

Thanks,
SoUS

---

### Post by martrn on 2008-04-27
> **SoUS said:**
> I'm not sure what I'd have done to overwrite my ntfs drive/system. From the code below, doesn't it look like I installed to the 8.5gb drive? The only other thing I see, is that "Disk /dev/sda" line ends with Ontrack. That utility loads when my PC boots, right after the BIOS stuff finishes. Westerndigital and Seagate use that for some reason so Windows(?) or certain motherboards can see the whole drive?


When you install ubuntu it installs grub.  Grub is a boot manager that loads an operating system such as ubuntu or any windows-like operating system.  When you installed ubuntu it would overwrite any previous bootloader written to  including but not limited to the windows bootloader (this can be fixed as you point out) and also OntrackkySeagatyBiosChangerBootloader, whatever that is.

> **SoUS said:**
> 
I wonder if that threw a wrench in the works. Assuming the data is not overwritten, perhaps any steps that can be takes to uninstall ubuntu and restore/recover Widows is the direction I need to go. I'm scared to, but fixmbr is tempting. I don't want to cause further damage at this point though, not knowing exactly where or what went wrong.



It sure did your OntrackkySeagatyBiosChangerBootloader is gone, grub has removed it from your disk.  You would need to contact the OntrackkySeagatyBiosChangerBootloader forums to find out how to put that master boot recorder thing back.

---

### Post by SoUS on 2008-04-27
Now that's the first thing to make me laugh all day. Not laughing at your idea/suggestion, just the "Y"s after Ontrack and seagate.

I'm going looking there now.

At the Ontracky site.

---

### Post by SoUS on 2008-04-27
I took out the 8.5 mb drive with ubuntu on it and booted with a seagate CD. That Disk Wizrd (or?? program) is still showing me both of my original partitions  on that 200gb drive. The mbr (or??) still shows up grub when I try to boot from the hard drive. 

I do still need to figure out how to get the OnTrack disk manager back on that drive, then perhaps hopefully might boot into Win 2000 or get the recovery consol to fix it. 

I'm thinking there's still hope, just need to figure how to safely get grub out of that mbr or boot sector or where ever it's living and likely the OnTrack disk manager back in there. (Or where ever it's supposed to be.)

Any and all assistance in getting back to Win 2000 is ssssoooo much appreciated.

SoUS

---

### Post by martrn on 2008-04-27
I do not know the answer to your question, as you have probably guessed by my reference to the OntrackkySeagatyBiosChangerBootloader thingy.

Most people here know about linux installations, and open source software because if something don't work, they can look at the source code, technical documentation and find out how it does.  With things like the OnTrack disk manager its proprietary software, and from what you say, it is still working.  People here also get a little fed up sometimes with the support offered or not offered by proprietary software.

Surely you have some technical documentation on how it does work.  I visited the site after your last post but found no pdf's or anything. Doesn't ontrack offer any support or anything.  It would be difficult for anyone to advise, as I dunno how it works I have no lincence to install ontrack or anything.

---

