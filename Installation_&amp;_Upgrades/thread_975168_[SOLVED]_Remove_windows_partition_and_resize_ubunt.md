---
title: "[SOLVED] Remove windows partition and resize ubuntu partition"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Mr_JMM on 2008-11-08
Hi,

I currently have a dual boot XP / Ubuntu drive partitioned as per below. I now want to remove the windows partition and resize the Ubuntu partition so that the entire drive becomes Ubuntu.

> /dev/sdc1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sdc2           22193       30401    65938792+   5  Extended
/dev/sdc4            3917       22192   146801970    b  W95 FAT32
/dev/sdc5           30141       30401     2096451   82  Linux swap / Solaris
/dev/sdc6           22193       23497    10482349+  83  Linux
/dev/sdc7           23498       30140    53359866   83  Linux


I have a GParted disk and can do this no problem but I have a few questions / concerns first:

1. sdc1 is marked as boot. If I reformat sdc1 what happens to the boot flag, is it required, do I have to reflag it when I format?

2. Because of the dual boot, I have a partition for /home (sdc7) and a seperate partition (sdc4) that I used as a documents drive (music, website local folders, pictures etc) which was accessible from both Windows and Ubuntu. In an ideal world, I'd prefer to extend /home to encompass sdc7 and the newly aquired windows space (so make sdc1, sdc4 and sdc7 one big fat partition.
2a. Is this possible?
2b. Should I copy every thing over from sdc7 to home first then just delete sdc7 -> resize sdc4? Will that be safe?
2c. Can this be repeated for sdc1?

3. Does it matter what order the /(root) and /home partitions are in? If it's possible, then should I make /(root) the first partition?

4. I can sort out any issues that may come up in grub due to change in mappings so no worries there but will the mappings / partition labels be automatically changed (so sdc4 becomes sdc2)?

5. Can I safely change sdc3 from an extended partition to all being logical (as I'll now have less than 4)?

As much as I'd love to be able to say this is to completely remove windows, it's not. I've got XP running on VirtualBox.

Many thanks as always,

James

---

### Post by bulldog on 2008-11-08
This is a little more complex.
If you are gonna mess around with partitions,ALWAYS BACKUP ALL YOUR DATA!

In my understanding is sdc1 a primary partition,you can't add this one to the extended partition.
Make this one a /data or what ever you want.

The bootflag is of no concern in this case,ubuntu can boot from primary and logical partitions as well,the hdd layout is not important.

Your fat partition can be added to your /home,because it's a logical partition within the same extended partition as the /home partition.

You'll have to understand some things.
1/ A hdd can have four primary partitions max,a primary is needed for windows to boot from.
2/ If you want to have more than four partitions,you need to give up one primary,to make an extended partition.
In the extended partition you can make as many logical partitions as you want,but you can't reclaim the extended partition without removing all logical partitions within.

So in basic, you can resize logical partitions,who are located in the same extended partition. [backup your data first!]
You cannot add the primary [sdc1] to the extended partition so there's no way to add sdc1 to sdc4

---

### Post by Mr_JMM on 2008-11-08
Good point about Ubuntu being on an extended partition.

I've had a quick search around and I gather that there is no way to convert an extended partition into a primary partition without losing the data; Is this correct?

If this is correct, my best guess is :
1. Back up everything.

2. re-allocate sdc1 as /(root) and sdc2 as /home.

3. Delete the entire extended partition.

4. Extend the /home partition to encompass what was the extended partition to leave just the root, home and swap.

5. Move everything that was on root (sdc6) to the new sdc1.

What I want to avoid doing is reinstalling Ubuntu from scratch onto the new root. Is it possible to take an image of the entire root partition and then burn this to the new root?

Many thanks again.

---

### Post by bulldog on 2008-11-08
Okay,I have to disagree with you.
The best thing,in my opinion that is,is to backup your valuable data,nothing more.
Then remove the extended partition,the logical partitions first ofcourse.
Remove the primary as well,so you get a big one partition hdd.

Now create a primary partition 10GB for / format ext3 set bootflag on
[in case you want to install future ubuntu releases without loosing the 'old' one,create 2x 10GB partitions]
Create a primary 2GB swap format as swap
Create a primary /home as big as you want

Reinstall ubuntu is done in half an hour,and it would be much,much quicker than trying to make an image and copy this one back.
Just choose 'manual' when you come to the partitioner and mount one 10GB partition as / and set it to format ext3
Mount swap as swap and your home partition as /home and proceed with the install.
This is by far the quickest way to do things.

To explain the second 10GB partition.
When a future release comes out,and you want to try it without the risk of loosing your working install,do it as follows.
Install / on the second 10GB partition and set it to format ext3 bootflag on.
Mount swap as swap
Now,and this is important,mount /home as /home,and be sure it's NOT set to format!!
Choose a new user-name and password,so there will be a new folder created in your existing /home.
Now you have a clean install and you can copy data from the old ubuntu /home folder to the new ubuntu /home folder,like your mail and firefox settings and bookmarks.
This is the way I do it for a few years,and I like it.
No more troubles with upgrading,just a clean install.
If the new ubuntu works well and you don't use the old one anymore,just empty your old /home folder [hidden files] and just install the next release using the user-name and password you used by the first install,etc.

---

### Post by caljohnsmith on 2008-11-08
If you want to move your entire Ubuntu root partition sda6 to sda1, it can be done, and I can give the method that has worked for me. Here are the basic steps you would do from your Live CD:
[LIST]
[*]Mount both sda1 and sda6
[*]Copy the entire file system from sda6 to sda1 with "cp -ax"
[*]Reinstall Grub to the MBR so that it points to sda1 now instead of sda6
[*]Change your /boot/grub/menu.lst to use the new sda1 partition
[*]Change your /etc/fstab to use the new sda1 partition
[/LIST]
If you want more specifics, let me know, but that's the general idea. :)

---

### Post by Mr_JMM on 2008-11-09
Hi,

caljohnsmith, bulldog, thank you.

I'm going to try a mix of both solutions:

bulldog: You are correct. The easiest and quickest method is to simply wipe and restart. Could probably do it in less than 30 minutes no problems. I also really like your idea having the two /(root) partitions to try out different kernels so I'll probably do that one.

However, I like to be difficult and I like to learn new things so I'm going to do this the long complicated way as per caljohnsmith.

One thing though: Are programs and their settings (such as Firefox and Thunderbird (along with the profiles folders) and VirtualBox) all stored on the root partition or home?

What I want to avoid doing is to keep having to install Firefox, Thunderbird, OpenOffice 3, Zimbra Desktop etc. and then trying to pull all the profiles info (including emails, settings etc.) across. Most of the set ups for these was shear luck and I struggle to replicate it to get it right first time. I guess that caljohnsmith's method does allow all this to be retained but it's only an issue if they are in root.

Many more thanks.

---

### Post by bulldog on 2008-11-09
Most people want the quick way to get running again.
Refreshing to read of someone who wants to do it the 'hard way':D

Settings of programs and stuff are located in your /home folder.
Tab view,select display hidden folders or something like that,and you can see them all.

Hope you can make things work and learn some on the way doing so.
Good luck to you.

---

### Post by Mr_JMM on 2008-11-11
Hi, I've got to the point now where I'm going to have to ask for more help please.

partitions now looks like this:
/dev/sdb1   ext3   15GB   boot     (/root)
/dev/sdb4   ext3   10GB            (development partition)
/dev/sdb3   linux-swap   4GB       (swap)
/dev/sdb2   extended   204GB
/dev/sdb5   ext3   204GB           (/home)

The above is the order they appear on the disk.

Q1. Does it matter that the drive labels(sdbx) are in disorder?


I moved /(root) using the cp -ax method above.

I have a second drive with Kubuntu loaded.

The grub menu comes up, I select Ubuntu, the first Ubuntu screen appears (Ubuntu logo with loading bar) but then it loads Kubuntu. I checked that GRUB for Ubuntu points to the Ubuntu drive (tried all just to be sure). I checked that the UUID's in fstab match (they changed after the moving of partitions so I re-wrote it).

I want to try and be stubborn and not reinstall the root of Ubuntu but I will as a last resort.

Can anyone help me sort out what's causing the Ubuntu option to boot Kubuntu?

One difficulty I am having is that the sdx label changes depending on whether I'm using Gparted, Ubuntu CD or Kubuntu boot. I tried resetting GRUB using the usual method ( terminal -> sudo grub -> find stage1 -> root (hdx,y) -> setup (hdx) ) but I don't think it's a GRUB issue. My thoughts are still with the FSTAB file unless their is another file that controls what is booted.

Please do ask if you need more info.

Many thanks as always.

James

---

### Post by caljohnsmith on 2008-11-11
> **Mr_JMM said:**
> 
Q1. Does it matter that the drive labels(sdbx) are in disorder?

Having the partition numbering different than the physical order on the HDD is not a problem. :)

Which drive are you booting from on start up? Are you sure you're booting the sdb drive and not the sda drive? Also, please post the following so I can get a better idea of what state your system is in right now:
```
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo blkid -c /dev/null
sudo mount /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```

---

### Post by Mr_JMM on 2008-11-11
Hi John,

Have checked in Bios that it boots from the Ubuntu drive.

> 
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
-> ```
GRUB
```

> sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
-> ```
ff00
```

> sudo blkid -c /dev/null
```
/dev/sda1: UUID="44295f05-e1f3-43e7-9713-a68e0b8d3b63" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="cae668b6-e4a5-4c7f-9dce-ac7fe7014af7" TYPE="swap" 
/dev/sda3: UUID="0f56c826-26b4-4d6e-bfab-3bf780139f96" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="7720494a-12ba-4dfc-82fb-d3ea706f6dc8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="99c8f274-3a4e-472c-bb74-a61b782e0bb4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="74b8e97b-965d-4bd9-b772-b26225a934fa" TYPE="swap" 
/dev/sdc4: UUID="b108ec38-9657-4e19-bce7-4f09d7e2627b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="a7bbd94c-be55-4533-9be6-32f0de7049d5" SEC_TYPE="ext2" TYPE="ext3" 
```

> cat /mnt/boot/grub/menu.lst
(just the relevant bit)
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=66bfd38b-a2d8-4358-85cd-92bf6cc274a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
boot

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 ro single
initrd          /boot/initrd.img-2.6.27-7-generic
boot

title           Ubuntu 8.10, kernel 2.6.24-21-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
boot

title           Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 ro single
initrd          /boot/initrd.img-2.6.24-21-generic
boot

title           Ubuntu 8.10, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin 
boot


## KUBUNTU KERNALS:
title           Kubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

title           Kubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 ro single
initrd          /boot/initrd.img-2.6.24-21-generic


### END DEBIAN AUTOMAGIC KERNELS LIST

```


> cat /mnt/etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=cae668b6-e4a5-4c7f-9dce-ac7fe7014af7 /home           ext3    defaults        0       2
# /dev/sda1
#UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
#UUID=D0DC5405DC53E3EE /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb4
UUID=4705-9A1E  /media/sdb4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=D00C1EB60C1E9794 /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=331cbe8d-f8a0-47e6-ad40-06ce2a909478 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

```


I can see the first discrepancy is that the above shows menu.lst has Ubuntu as hd0,0 (sda1) yet other shows different... I'm certain this is just because I'm running from a CD. It all varies depending on what I'm using to view the system.

I've also just spotted groot and UUID is wrong.
[EDIT] These have been changed. groot now shows hd0,0 and UUID was replaced by that shown from fdisk -l but still boots into Kubuntu.

---

### Post by caljohnsmith on 2008-11-11
> **Mr_JMM said:**
> 
```
/dev/sda1: UUID="[COLOR="Blue"]44295f05-e1f3-43e7-9713-a68e0b8d3b63[/COLOR]" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="cae668b6-e4a5-4c7f-9dce-ac7fe7014af7" TYPE="swap" 
/dev/sda3: UUID="0f56c826-26b4-4d6e-bfab-3bf780139f96" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="[COLOR="Red"]7720494a-12ba-4dfc-82fb-d3ea706f6dc8[/COLOR]" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="99c8f274-3a4e-472c-bb74-a61b782e0bb4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="74b8e97b-965d-4bd9-b772-b26225a934fa" TYPE="swap" 
/dev/sdc4: UUID="b108ec38-9657-4e19-bce7-4f09d7e2627b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="a7bbd94c-be55-4533-9be6-32f0de7049d5" SEC_TYPE="ext2" TYPE="ext3" 
```
```

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=[COLOR="Blue"]44295f05-e1f3-43e7-9713-a68e0b8d3b63[/COLOR] ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic

```



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=[COLOR="Blue"]44295f05-e1f3-43e7-9713-a68e0b8d3b63[/COLOR] /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=cae668b6-e4a5-4c7f-9dce-ac7fe7014af7 /home           ext3    defaults        0       2
# /dev/sda1
#UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
#UUID=D0DC5405DC53E3EE /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb4
UUID=4705-9A1E  /media/sdb4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=D00C1EB60C1E9794 /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=331cbe8d-f8a0-47e6-ad40-06ce2a909478 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

```

OK, so sda1 is Kubuntu, is that true? If so, your menu.lst above is using the UUID for sda1 (Kubuntu), not sdb1 (Ubuntu); i.e you should change all the Ubuntu kernel lines to use "7720494a-12ba-4dfc-82fb-d3ea706f6dc8". Also, make sure the "# kopt" line uses the sdb1 UUID too. 

Your fstab above also uses the UUID for sda1 to mount on "/" (see highlighted text above), so you should change that to the sdb1 UUID. I think if you make those changes, Ubuntu will probably boot just fine. Let me know how it goes. :)

---

### Post by Mr_JMM on 2008-11-11
[EDIT: Sorry John, I was writing this as you were writing yours so apologies if I repeat anything. Couldn't have got this far without your help and suggestions]

GOTCHA YA BAST**...

I think a glaring case of "..wood for the trees" here.

After realising that it's stupidly difficult to get this right when I'm booted into a system that's on a different drive, I went back to a 7.04 Live CD and corrected everything.

We now have:
```
abcde@abcde-fghijkl:~$ sudo blkid -c /dev/null 
/dev/sda1: UUID="44295f05-e1f3-43e7-9713-a68e0b8d3b63" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="cae668b6-e4a5-4c7f-9dce-ac7fe7014af7" TYPE="swap" 
/dev/sda3: UUID="0f56c826-26b4-4d6e-bfab-3bf780139f96" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="7720494a-12ba-4dfc-82fb-d3ea706f6dc8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="99c8f274-3a4e-472c-bb74-a61b782e0bb4" TYPE="ext3" 
/dev/sdc3: UUID="74b8e97b-965d-4bd9-b772-b26225a934fa" TYPE="swap" 
/dev/sdc4: UUID="b108ec38-9657-4e19-bce7-4f09d7e2627b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="a7bbd94c-be55-4533-9be6-32f0de7049d5" TYPE="ext3" 
```


```
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
# kopt=root=UUID=99c8f274-3a4e-472c-bb74-a61b782e0bb4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=99c8f274-3a4e-472c-bb74-a61b782e0bb4 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
boot

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=99c8f274-3a4e-472c-bb74-a61b782e0bb4 ro single
initrd		/boot/initrd.img-2.6.27-7-generic
boot

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=99c8f274-3a4e-472c-bb74-a61b782e0bb4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
boot

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=99c8f274-3a4e-472c-bb74-a61b782e0bb4 ro single
initrd		/boot/initrd.img-2.6.24-21-generic
boot

title		Ubuntu 8.10, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot


## KUBUNTU KERNALS:
title		Kubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Kubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 ro single
initrd		/boot/initrd.img-2.6.24-21-generic


### END DEBIAN AUTOMAGIC KERNELS LIST

```


```
abcde@abcde-fghijk:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=99c8f274-3a4e-472c-bb74-a61b782e0bb4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=a7bbd94c-be55-4533-9be6-32f0de7049d5 /home           ext3    defaults        0       2
# /dev/sda1
#UUID=44295f05-e1f3-43e7-9713-a68e0b8d3b63 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
#UUID=D0DC5405DC53E3EE /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb4
#UUID=4705-9A1E  /media/sdb4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc1
#UUID=D00C1EB60C1E9794 /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
#UUID=331cbe8d-f8a0-47e6-ad40-06ce2a909478 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

```

I am still not happy with the fstab file though. I have commented out a lot of it. My thoughts are that a lot of it is the remnants of the previous system layout but I don't know enough to sort out what needs to stay.

I CAN finally boot and all seems to be ok. All files in tact, all programs working correctly with the right settings, addons etc. but before I mark as solved and edit the opening post (for the benefit of others) can you help me to sort out the FSTAB?

Many thanks as always,

James.

---

### Post by caljohnsmith on 2008-11-11
So is the Ubuntu you want to boot on sdb1 or sdc1? You've modified everything above to use the sdc1 UUID. Also, you are mounting sdc5 on /home, is that what you want? You don't have a line in your fstab for a swap partition either, so are you going to use a swap file instead?

---

### Post by Mr_JMM on 2008-11-11
> So is the Ubuntu you want to boot on sdb1 or sdc1? You've modified everything above to use the sdc1 UUID.
According to both Ubuntu Live CD and Ubuntu boot, Ubuntu is on sdc. It is bizarre though that GRUB is set to boot to hd0,0 which should be sda. This baffles me greatly and I have no idea what's going on.


> Also, you are mounting sdc5 on /home, is that what you want?
Again, that is correct according to fsdisk -l I have had to keep an extended partition for the moment until I get around to saving /home onto another drive, remove the extended partition, create a forth Primary, mark as /home and re-upload. For the moment it is correct.


> You don't have a line in your fstab for a swap partition either, so are you going to use a swap file instead?
Now that is an issue. I do have a swap partition. Could you please advise how I can edit / tidy up the fstab? I tried to find some way of having the fstab file recreated (like using terminal or SGD to re-write GRUB) but didn't manage it.


CalJohnSmith, again I'm grateful for all your help with this.

---

### Post by caljohnsmith on 2008-11-11
> **Mr_JMM said:**
> 
According to both Ubuntu Live CD and Ubuntu boot, Ubuntu is on sdc. It is bizarre though that GRUB is set to boot to hd0,0 which should be sda. This baffles me greatly and I have no idea what's going on.

OK, you had me confused, because in post #8 you showed that everything was on sdb, not sdc, but I see now that you must have meant sdc. And about using (hd0,0) in your menu.lst, I understand your confusion, because it comes down to this: on start up, Grub sees the order of HDDs as the same as the BIOS boot order, not as the drives are ordered in Ubuntu's /dev directory. So that means when you are running Grub commands in Ubuntu, then the following is true:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc.
```
But on start up, that's not necessarily true, because on start up it goes like:
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
So if you are booting the sdc drive on start up, then sdc is (hd0), and that is what you should use in the menu.lst. In other words, the bottom line is when running Grub commands in Ubuntu, the first case above holds, but when you need to modify your menu.lst, the second case holds. :)
> **Mr_JMM said:**
> 
Now that is an issue. I do have a swap partition. Could you please advise how I can edit / tidy up the fstab? I tried to find some way of having the fstab file recreated (like using terminal or SGD to re-write GRUB) but didn't manage it.

Unfortunately I don't know of any way to auto-recreate an fstab, but I've tidied up your fstab a bit, so how about copying/pasting the following fstab into yours:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=99c8f274-3a4e-472c-bb74-a61b782e0bb4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5 home partition:
UUID=a7bbd94c-be55-4533-9be6-32f0de7049d5 /home           ext3    defaults        0       2
#/dev/sdc3 swap partition:
UUID=74b8e97b-965d-4bd9-b772-b26225a934fa none swap  sw   0 0
# other media:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
```
Note also that I added a line your fstab for your swap partition, so that should be taken care of. Unfortunately there is one more file you will probably have to fix:
```
sudo mount /dev/sdc1 /mnt
gksudo gedit /mnt/etc/initramfs-tools/conf.d/resume
```
Make sure the UUID in that file uses the same UUID as your swap partition, namely "74b8e97b-965d-4bd9-b772-b26225a934fa". If you have to change it, then next time you boot into the Ubuntu on sdc1, be sure to run:
```
sudo update-initramfs -u -k all
```
And after that you should be all set.
> **Mr_JMM said:**
> 
CalJohnSmith, again I'm grateful for all your help with this.
You're certainly welcome, I know it can be a pain to sort these things out. Hopefully doing the above steps will be all you need to do, but let me know how it goes. :)

---

### Post by Mr_JMM on 2008-11-11
CalJohnSmith, you're a star. All works perfectly now.

I did have to change that last file, so ran the last command as instructed.

Many many thanks for your help (ditto to Bulldog).


I've learned quite a lot from this exercise so although I've gone 3 days without a bootable system (never been so grateful for being able to run from the CD) it's been worth it.

I will edit the first post as I mentioned earlier but may have to wait till tomorrow (it's past midnight here).

Thank you.

James

---

### Post by caljohnsmith on 2008-11-11
That's great news that everything seems to be working OK now. Cheers and have fun with all your Ubuntus. :)

---

