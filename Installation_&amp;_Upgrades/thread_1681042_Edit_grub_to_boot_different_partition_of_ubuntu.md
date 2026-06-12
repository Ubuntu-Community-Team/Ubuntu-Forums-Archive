---
title: "Edit grub to boot different partition of ubuntu?"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by jflinux on 2011-02-03
So, I'm dual boot with Vista(TM) and UBUNTU(tm) and ran out of space on Ubuntu partition:

I booted Ubuntu 10.04LTS live CD and shrank the VISTA.
It would NOT let me grow the extended partition???
So now I have:
sda1 ntfs  /media/TOSHIBA_SYSTEM_VOLUME  1.46GB  
sda2 ntfs  /media/SQ004588V03          88GB
sda4 ext3     THIS IS MY NEW PARTITION   15GB
sda3 extended
   sda5 ext3  /    THIS IS MY OLD UBUNTU partition  6GB
   sda6  linux swap                                                        340MB

Then I used gparted on live CD to copy files from old partitin sda5 to sda4.
But grub still boot to old partitiion.

[SIZE=5][U][I][B]How do I change grub to work?
Is it grub or grub2?
Thank
J
[/B][/I][/U][/SIZE]
[SIZE=5]_***/boot/grub$ ls***_[/SIZE]
default     e2fs_stage1_5  grubenv            jfs_stage1_5  menu.lst~        
minix_stage1_5     stage1  xfs_stage1_5
device.map  fat_stage1_5   installed-version  menu.lst      
menu.lst.110201  reiserfs_stage1_5  stage2

[SIZE=5]_***/boot/grub$ egrep hd menu.lst***_[/SIZE]
# root        (hd0,0)
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
## e.g. groot=(hd0,0)
## e.g. defoptions=vga=791 resume=/dev/hda5
rootnoverify    (hd0,1)

[SIZE=6]_***/boot/grub$ cat menu.lst***_[/SIZE]
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=85251b80-f37e-4576-832b-fd73013eddbe

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 10.10, kernel 2.6.35-25-generic
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro  single
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro  single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-23-generic
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro quiet splash 
initrd        /boot/initrd.img-2.6.35-23-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro  single
initrd        /boot/initrd.img-2.6.35-23-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=85251b80-f37e-4576-832b-fd73013eddbe ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, memtest86+
uuid        85251b80-f37e-4576-832b-fd73013eddbe
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by grahammechanical on 2011-02-03
you say

> Then I used gparted on live CD to copy files from old partitin sda5 to sda4. But grub still boot to old partitiion.

Do you mean that you did a fresh install of Ubuntu on to sda4? If so, then GRUB would be updated to know to boot from sda4 not sda5 as part of the installation process. Which GRUB are you using GRUB or GRUB2? 

In a terminal run update-grub or update-grub2. Something should search for all possible operating systems and update the boot menu accordingly.

Regards.

---

### Post by jflinux on 2011-02-03
> **grahammechanical said:**
> you say
Do you mean that you did a fresh install of Ubuntu on to sda4? If so, then GRUB would be updated to know to boot from sda4 not sda5 as part of the installation process. Which GRUB are you using GRUB or GRUB2? 

In a terminal run update-grub or update-grub2. Something should search for all possible operating systems and update the boot menu accordingly.
Regards.

Not a fresh install.   Sda5 is the OLD too SMALL partition.
Sda4 is the copy of sda5 in a Larger partition,
but it still boot the old small partition.   I just don't understand grub, more of a lilo guy.

---

### Post by oldfred on 2011-02-03
How did you copy it? It may make a difference if permissions were not preserved or if UUID is actually the same?

Do you want to keep grub legacy? most have converted to grub2 now.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

this also has instructions on reinstalling old grub.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by jflinux on 2011-02-03
> **oldfred said:**
> How did you copy it? It may make a difference if permissions were not preserved or if UUID is actually the same?

gparted from the unbuntu live CD did the copy.  I assume it preserved everything??

I can redo that if there needs be done another way.
Mainly want to copy stuff from small partition to big partition to give me more
disk space.
Thanks.

---

### Post by oldfred on 2011-02-03
That should be find but it may have copied the UUID. results.txt whould show that.

or do sda4 & sda5 have same number?
sudo blkid

The two files that are important are grub and fstab. They often refer to partitions, but most of the time now use UUIDs.

---

### Post by jflinux on 2011-02-03
> **oldfred said:**
> That should be find but it may have copied the UUID. results.txt whould show that.

or do sda4 & sda5 have same number?
sudo blkid

The two files that are important are grub and fstab. They often refer to partitions, but most of the time now use UUIDs.

/boot/grub# blkid
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="E074CBD574CBAD1A" TYPE="ntfs" 
/dev/sda2: LABEL="SQ004585V03" UUID="4A90D31E90D30EF7" TYPE="ntfs" 
/dev/sda4: UUID="85251b80-f37e-4576-832b-fd73013eddbe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="85251b80-f37e-4576-832b-fd73013eddbe" TYPE="ext3" 
/dev/sda6: UUID="cd3cc320-b49a-4acd-aa37-ae946b5395c3" TYPE="swap"

---

### Post by oldfred on 2011-02-03
The UUIDs are identical so you should have problems. You need to change one, reinstall grub so it tries to boot from sda4 and perhaps update fstab.

Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

If you want to convert to sda4 I would change sda5. The reinstall grub legacy to the MBR. I would check fstab to make sure both / and swap have correct UUIDs.

To install grub legacy 
1. Boot your computer up with Ubuntu liveCD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,3)" for sda4 and (hd0,4) for sda5.
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,3)"  Look at output from #4
6. Type "setup (hd0)"
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by jflinux on 2011-02-03
> **oldfred said:**
> 
To install grub legacy...


Sorry for the confusion, I am running grub 1 rather than grub 2.
$ grub-install -v
grub-install (GNU GRUB 0.97)

Grub 1 is grub legacy I assume?
Do I need to install grub legacy?
Thanks,
J

---

### Post by oldfred on 2011-02-04
The grub in the MBR will be pointed to boot sda5, you have to change that to sda4, assuming everything in sda4 is correct.

When they came out with grub2, they started calling old grub, grub legacy.

Grub2 is still not at version 2, grub2 is just the second version of grub. Maverick uses grub2 version  1.98. Natty is at 1.99.

Grub 0.97 is grub legacy and was just called grub before. But grub 0.97 varies by distribution as it has not been maintained for years and each distribution tweaked it to work for whatever changes they did. For instance Ubuntu updated its distribution of grub legacy to allow ext4 partitions.

---

### Post by jflinux on 2011-03-08
While booted from a liveCD ubuntu10.04:

# tune2fs -U random /dev/sda5
tune2fs 1.41.11 (14-Mar-2010)
root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="E074CBD574CBAD1A" TYPE="ntfs" 
/dev/sda2: LABEL="SQ004585V03" UUID="4A90D31E90D30EF7" TYPE="ntfs" 
/dev/sda4: UUID="85251b80-f37e-4576-832b-fd73013eddbe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="9ed7f7fa-2d25-4223-8dcc-a6ef446c8cc1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="cd3cc320-b49a-4acd-aa37-ae946b5395c3" TYPE="swap" 


Now all I have to do is reformat sda4 and:
cp /dev/sda5 /dev/sda4
to move all my working files to the new partition.
The above command does not really work?   what is a better command to
copy all file to the new partition?
thanks.

---

### Post by jflinux on 2011-03-09
So I rebooted to the new partition and it worked.  
Then I broke it:   I had been working in the old partition, so I
used the copy partition in gparted to copy to the new partition.
It copied the UUID again and now I have duplicate UUIDS again.

Also, it won't boot.
It says file not found on every linux image in the grub boot menu, 
because the UUID of my partitions changed and that UUID is no longer 
on my system:
#sudo bash
# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="E074CBD574CBAD1A" TYPE="ntfs" 
/dev/sda2: LABEL="SQ004585V03" UUID="4A90D31E90D30EF7" TYPE="ntfs" 
/dev/sda4: UUID="9ed7f7fa-2d25-4223-8dcc-a6ef446c8cc1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="9ed7f7fa-2d25-4223-8dcc-a6ef446c8cc1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="cd3cc320-b49a-4acd-aa37-ae946b5395c3" TYPE="swap" 
# tune2fs -U random /dev/sda5
tune2fs 1.41.11 (14-Mar-2010)
root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="E074CBD574CBAD1A" TYPE="ntfs" 
/dev/sda2: LABEL="SQ004585V03" UUID="4A90D31E90D30EF7" TYPE="ntfs" 
/dev/sda4: UUID="9ed7f7fa-2d25-4223-8dcc-a6ef446c8cc1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="dcf09c7f-b940-4d3d-a982-d67c81f09991" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="cd3cc320-b49a-4acd-aa37-ae946b5395c3" TYPE="swap" 

So now I have an unbootable system.
Grub legacy is on the hard disk.
I have several LIVE cds with either ubuntu10.04 and older ubuntu plus a knoppix live cd.
The live cds probably have grub2 but one of my older ones have grub legacy and lilo.

What is the fastest command to type to get the system running again off hard
disk partition sda4?

---

### Post by oldfred on 2011-03-09
I am not a believer in copying a system partition. You can do it and have to make the setting changes discussed above to UUID, fstab & grub and a grub reinstall to the MBR to find the new copy.

But you can just do an install in about an hour. You can copy settings from old /home to new install if you want. (I use rsync). If you have a separate /home in a different partition, then it is very easy as part of the new install choose to use the old /home without formating, then the new install will find all the old settings and your data that is in /home.

Three ways, essentially the same:
To move /home uses rsync  (create mount may be missinig)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jflinux on 2011-03-10
OldFred,  thanks.   That should work since unbuntu keeps all the data
files in the /home/?????  directory.

I have seen this not work when there were several users and the 
user and user numbers changed:
# id
uid=0(root) gid=0(root) groups=0(root)

Root is always user number 0.
(id - print real and effective UIDs and GIDs)

Of course, recursive chown would fix that.
I'll download the latest ubuntu and install tomorrow.
thanks.

---

### Post by Hedgehog1 on 2011-03-10
```
So, I'm dual boot with Vista(TM) and UBUNTU(tm) and ran out of space on Ubuntu partition:

I booted Ubuntu 10.04LTS live CD and shrank the VISTA.
It would NOT let me grow the extended partition???
So now I have:
sda1 ntfs  /media/TOSHIBA_SYSTEM_VOLUME  1.46GB  
sda2 ntfs  /media/SQ004588V03          88GB
sda3 extended
   sda5  ext3  /    THIS IS MY OLD UBUNTU partition  6GB
   sda6  linux swap            340MB
[COLOR="Red"]sda4 ext3     THIS IS MY NEW PARTITION   15GB[/COLOR]
```

jflinux,

This whole fiasco started because you did not understand how to grow the 'sda3' extended partition.  As is often the case, the 'work arounds' have been many times more painful that actually expanding the partition.

Here are the steps to expand **sda3**:

1) Boot off the LiveCD or LiveUSB stick you used to install.
2) Choose 'try' and fire up gparted.
3) *[COLOR="Red"]<Your missing step>[/COLOR]* Highlight and right click on the **sda6** swap partition, and select 'swap off'.  *[COLOR="red"]This releases the **sda6** & therefore the **sda3** extended partition.[/COLOR]*
4) Unmount the **sda6** Swap partition if it is not already unmounted.
5) Delete the **sda4** partition.
6) Extended the **sda3** extended partition to the end of the 'disk'
7) Relocate **sda6** swap to the end of the **sda3** extended partition.
8] Expand the **sda5** partition to the available space left in the **sda3** extended partition.

Then you will have:

```
sda1 ntfs  /media/TOSHIBA_SYSTEM_VOLUME  1.46GB  
sda2 ntfs  /media/SQ004588V03          88GB
sda3 extended
   [COLOR="RoyalBlue"]sda5  ext3  /   21 GB[/COLOR]
   sda6  linux swap 340MB
```

***The Hedge***

:KS

---

### Post by jflinux on 2011-03-12
[Hedgehog1]("http://ubuntuforums.org/member.php?u=1230016"):   Great post.  I think you are right that the partition was locked by the live CD using swap.  
swapoff -a -v would have been the correct response.

gparted developers:  Please put in good error messages.  "swap partition locked extended partition, type: sudo swapoff -a -v" is way better than 
"operation failed"; I have no way to test this, so my input may be incorrect.  But the fact that 
you guys have a partition editor that works on windows, linux, etc, for free is fantastic.  Great job.

Oldfred:  Great idea. Your idea about reinstall and copy the /home directory  with cp -ax fixed everything. I only
had to bring every software up to the same version as my old
partition.   After copying,  I had to delete a lock file for chrome as it thought it was in use.

Thanks for your help.

SOLVED.

---

