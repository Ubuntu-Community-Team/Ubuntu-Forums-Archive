---
title: "Unable to boot ubuntu 10.04 after windows 7 Re-installation."
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by prasenjit007 on 2010-05-10
Hello Everybody....
I "USED" to have a dual booting pc...with Windows 7 & ubuntu 10.04.(NOT Wubi)
2 Days back my windows 7 crashed...so i had to reinstall windows 7. But after reinstallation there was no option to boot into ubuntu 10.04. My system automatically boots into windows 7.
I need to fix my ubuntu installation so that i get an option to select which OS to boot...at the startup.

Plz help...its URGENT..
Am a newbie...and i don't want to reinstall ubuntu.
Any help would be appreciated.
Thnks!

---

### Post by darkod on 2010-05-10
Don't worry, it takes just two commands. But to make sure I give you correct ones, boot with the 10.04 cd in live mode, and in terminal do:

sudo fdisk -l

Post the results. Once we know your root partition, it's easy to reinstall grub2.

---

### Post by prasenjit007 on 2010-05-11
Hey buddy thnks for the rply..
here is the output for the command [B]sudo fdisk -l
[/B]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000acfa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6534    52480000    7  HPFS/NTFS
/dev/sda2            6534        9801    26239258   83  Linux
/dev/sda3            9801       24851   120893440    7  HPFS/NTFS
/dev/sda4           24852       38913   112953015    5  Extended
/dev/sda5           24853       38913   112944982+   7  HPFS/NTFS

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c175e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         490     3928032    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(488, 254, 63) logical=(489, 5, 27)


Hey one thing i need to confirm that after reinstalling grub 2...will i be able to boot into windows 7....???
It won't get currupted or unbootable????
Sorry for silly question but am totally new to this kind of stuffs...

Thnks in Advance.....:)

---

### Post by darkod on 2010-05-11
Don't worry, win7 will be just fine. Boot again in live mode and in terminal do:

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will reinstall grub2 back on the MBR of your hdd, /dev/sda. Your ubuntu partition is /dev/sda2 as you can see in the results.

Restart after that and all should be fine.

---

### Post by Gafalos on 2010-05-11
Hi,

I have the same problem with prasenjit007 and I just gave it a try with the commands you suggested. However, It didnt work for me. 
When I type the command "sudo  fdisk -l"  this is what i get:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9f32097

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       15536   123248640    7  HPFS/NTFS
/dev/sda3           15536       19803    34281933+   7  HPFS/NTFS
/dev/sda4           19804       30402    85129217    5  Extended
/dev/sda5           19804       19866      499712   82  Linux swap / Solaris
/dev/sda6           19866       30402    84628480   83  Linux

should I change something on the commads?

Thank you in advance.
Apostolis

---

### Post by darkod on 2010-05-11
> **Gafalos said:**
> Hi,

I have the same problem with prasenjit007 and I just gave it a try with the commands you suggested. However, It didnt work for me. 
When I type the command "sudo  fdisk -l"  this is what i get:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9f32097

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       15536   123248640    7  HPFS/NTFS
/dev/sda3           15536       19803    34281933+   7  HPFS/NTFS
/dev/sda4           19804       30402    85129217    5  Extended
/dev/sda5           19804       19866      499712   82  Linux swap / Solaris
[COLOR=Red]/dev/sda6           19866       30402    84628480   83  Linux
[/COLOR] 
should I change something on the commads?

Thank you in advance.
Apostolis

Yes, your ubuntu root partition is /dev/sda6 and it's still on the same device (disk), /dev/sda.

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Basically you mount the root partition as /mnt and you tell grub2 to install to /dev/sda (the MBR of the disk) and specifying where you mounted the root with the --root-directory parameter.

Hope it makes sense. :)

---

### Post by Gafalos on 2010-05-11
sorry man, ignore my last message.
Probably a mistyping was the problem.
It worked when i copied and pasted the commands.

Thank you.

---

### Post by Gafalos on 2010-05-11
I did it again with "sda6" to be sure :). 

Thank you very much.

---

### Post by darkod on 2010-05-11
> **Gafalos said:**
> sorry man, ignore my last message.
Probably a mistyping was the problem.
It worked when i copied and pasted the commands.

Thank you.

Hmmm... It shouldn't have worked at all in your case if you tried to mount /dev/sda2 and then install grub pointing to it as root partition. That is not the root partition.

Anyway, it should work fine after doing it with /dev/sda6, check and see.

---

### Post by Gafalos on 2010-05-11
Hey,

I restarted and booted UBUNTU normally. 
YEAH!!!
Ty m8

I have one more question...:)
Is it possible to change the order in which Ubuntu and Windows 7 appear in the booting list?

I would prefer windows to be first. Can it be?

---

### Post by oldfred on 2010-05-11
If you just want windows to be the default to start, this is the easiest:

Custom Menus ---------------------------------------
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
OR:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.


If you save the file you create with the custom entry to, say, 09_custom, it will not be over written and will be at the beginning of your menu
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

---

### Post by darkod on 2010-05-11
> **Gafalos said:**
> Hey,

I restarted and booted UBUNTU normally. 
YEAH!!!
Ty m8

I have one more question...:)
Is it possible to change the order in which Ubuntu and Windows 7 appear in the booting list?

I would prefer windows to be first. Can it be?

Yes. The quick way I prefer:

Boot your ubuntu and in terminal execute:

sudo cp /etc/grub.d/30_os-prober /etc/grub.d/06_os-prober
sudo chmod -x /etc/grub.d/30_os-prober

If you want the memtest entries gone also execute:

sudo chmod -x /etc/grub.d/20_memtest86+

To finalize execute:

sudo update-grub

Now windows will be on top and the latest ubuntu kernel second. When new kernel is added the newest one will always be second.

You control the timeout and default OS in /etc/default/grub. The default OS is counted from 0, so the first entry is equivalent to 0, the second to 1, etc. If you want to change them, open:

sudo gedit /etc/default/grub

The lines are:
GRUB_DEFAULT=0
GRUB_TIMEOUT=10 (meaning 10 seconds)

Change to what ever value you want. Save and close the file. If you change anything again you need to run:

sudo update-grub

Reading material on Grub2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by prasenjit007 on 2010-05-11
Hey thnks a lot **darkod**
U saved my day....thnks a lot.

Hey i have one more question.
Normally i mount my windows C drive as /windows during ubuntu installation and other drives under /media.
but after reinstalling grub2 i found that now my windows C drive is also mounted under /media.
(Well thats not a prob.at all)

But now during ubuntu booting screen(Violet one)
It says "/windows is not mounted or not present. press s to skip mounting or M for manual operation...(or something like that).

So my question is now how can i remove the /windows entry from "/"(Root) directory...so that it shouldn't give me the same error(As above) at boot time...

---

### Post by darkod on 2010-05-11
> **prasenjit007 said:**
> Hey thnks a lot **darkod**
U saved my day....thnks a lot.

Hey i have one more question.
Normally i mount my windows C drive as /windows during ubuntu installation and other drives under /media.
but after reinstalling grub2 i found that now my windows C drive is also mounted under /media.
(Well thats not a prob.at all)

But now during ubuntu booting screen(Violet one)
It says "/windows is not mounted or not present. press s to skip mounting or M for manual operation...(or something like that).

So my question is now how can i remove the /windows entry from "/"(Root) directory...so that it shouldn't give me the same error(As above) at boot time...

You probably have an entry in /etc/fstab that you need to remove. But wait for someone more experienced than me to help you with exact instructions. PLAYING WITH /ETC/FSTAB CAN MAKE UBUNTU UNBOOTABLE!

Oldfred?

---

### Post by oldfred on 2010-05-11
Lets see what /etc/fstab looks like. Post in code tags (# on edit menu).
```

cat /etc/fstab
```

You can test your fstab and should run this after any changes to make sure it is ok before rebooting. typos can be dangerous. If it just returns its ok or it lists error messages.

```
sudo mount -a
```

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by prasenjit007 on 2010-05-11
Hey guys thnks for ur rply...
but i didn't understand ur instructions completely..cud u plz explain it once more in a detailed way.
am i supposed to run both the commands n post the output?

well when ran **cat /etc/fstab** i got the following msg:

prasenjit@prasenjit-laptop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=7a94da55-8c10-4181-bd23-e8846bb3f6fe /               ext4    errors=remount-ro 0       1
# /media/Disk-1 was on /dev/sda3 during installation
UUID=AE845B29845AF2F7 /media/Disk-1   ntfs    defaults,umask=007,gid=46 0       0
# /media/Disk-2 was on /dev/sda5 during installation
UUID=50945BF7945BDDD2 /media/Disk-2   ntfs    defaults,umask=007,gid=46 0       0
# /windows was on /dev/sda1 during installation
UUID=BAD268F0D268B1F5 /windows        ntfs    defaults,umask=007,gid=46 0       0


Wat does the second command do?
Plz guide me ahead.
thnks!

---

### Post by oldfred on 2010-05-11
the sudo mount -a remounts fstab and will show errors if anything is not correct. You can always check what a command does with man .. (use q to exit from the man listing.) If you run sudo mount -a  it does it give an error?

```
man mount
```I do not see anything, but need to compare UUID's to see if one is wrong:

```
sudo blkid
```

---

### Post by darkod on 2010-05-11
> **oldfred said:**
> I do not see anything, but need to compare UUID's to see if one is wrong:


UUID=[COLOR=Red]BAD268F0D268B1F5[/COLOR] /windows        ntfs    defaults,umask=007,gid=46 0        0

You're spot on, Oldfred. The OP reinstalled win7 which I bet formated the partition and the UUID is not the same any more.

@prasenjit007
As Oldfred said, please post the output of:

sudo blkid

You will have to replace the red value above with the new UUID code of /dev/sda1. After win7 formatted it, it has a new code value. That is assigned at format.

---

### Post by prasenjit007 on 2010-05-11
Hey u guys are very helpful...keep up the good work:KS:P

I ran the command **sudo mount -a**
got the following error:

prasenjit@prasenjit-laptop:~$ **sudo mount -a**
[sudo] password for prasenjit: 
ntfs-3g: Failed to access volume 'UUID=BAD268F0D268B1F5': No such file or directory

ntfs-3g 2010.3.6 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

**Output for sudo blkid:**

prasenjit@prasenjit-laptop:~$ **sudo blkid**
/dev/sda1: LABEL="BASEMENT" UUID="B8C0F342C0F30582" TYPE="ntfs" 
/dev/sda2: UUID="7a94da55-8c10-4181-bd23-e8846bb3f6fe" TYPE="ext4" 
/dev/sda3: LABEL="ALIEN" UUID="AE845B29845AF2F7" TYPE="ntfs" 
/dev/sda5: LABEL="SOLUTUDE STUDIO" UUID="50945BF7945BDDD2" TYPE="ntfs" 
/dev/sdc1: LABEL="PASSPORT" UUID="F114-D4AE" TYPE="vfat" 

As darkod said my UUID has changed from **"BAD268F0D268B1F5"** to **"B8C0F342C0F30582"** for /dev/sda1.

so now do i have to edit the /etc/fstab file and change the UUID for /dev/sda1??
n after changing i won't be having any boot error msg at the violet splash screen?? n wat bout the directory "/windows"? will it be removed?(thats wat i want).

---

### Post by darkod on 2010-05-11
> **prasenjit007 said:**
> 
As darkod said my UUID has changed from **"BAD268F0D268B1F5"** to **"B8C0F342C0F30582"** for /dev/sda1.

so now do i have to edit the /etc/fstab file and change the UUID for /dev/sda1??
n after changing i won't be having any boot error msg at the violet splash screen?? n wat bout the directory "/windows"? will it be removed?(thats wat i want).

If you change it, it will continue mounting /dev/sda1 as /windows. And yes, the error will be gone.

If you want it to stop mounting it, you can change the value in /etc/fstab but at the front of that line put the # sign. The lines that start with # are ignored.

In future you can just remove the # and it will start mounting /dev/sda1 as /windows again.

---

### Post by prasenjit007 on 2010-05-11
Hey since its morning 3:00am i'll edit the /etc/fstab file tomorrow. hey after editing my windows drive will again be mounted under /windows.....thats fine with me. bt right now before editing /etc/fstab and after grub2 reinstallation my windows drive is automatically mounted under /media as i mentioned earlier.....so after editing will that entry(directory) under /media will remain or will it automatically disappear?

---

### Post by prasenjit007 on 2010-05-12
Hey guys thnks a lot for your Responses...
You guys successfully solved all my problems..you guys are simply great!!!

So finally i am very happy to mark this thread as "**SOLVED**"...
thnks once again.

---

### Post by sarang031705 on 2011-09-30
Thank you so much Darkod
You really saved me time on re-installing my ubuntu os
God Bless:popcorn::D):P

---

