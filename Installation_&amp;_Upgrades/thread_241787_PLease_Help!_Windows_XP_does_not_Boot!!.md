---
title: "PLease Help! Windows XP does not Boot!!"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by sforeste on 2006-08-22
Hello! I am new to Linux and we decided that we would like to look at an alternative to Windows XP. We found Ubuntu and downloaded it and burned the CD and tried to put it on 1 computer but either the computer was too old or there was not enough room to run from the CD.

So we have a main computer here that is virtually brand new with 2 hard drives and lots of space. So we were given permission to allow Ubuntu to be installed as a dual boot and we would make Windows XP the primary boot and use Ubuntu to play around with and get familiar with and make a decision to switch over at a later time.

The installation went smoothly and I just selected all of the defaults and it all installed without a hitch. We like very much Ubuntu and played around with it but when we were ready to leave for the day we tried to boot the computer again and all it does is boot into Ubuntu. The CD is not in the computer.

I have looked at the bootloader file and all it has is Ubuntu and Windows is NOT listed as a option. I have no idea how to use GRUB and I have searched the internet as well as your forums and guides to resolve this problem and I have been here for almost 4 hours and I am feeling very sick now because they are not going to be able to use this main church computer tomorrow.

I really need somone's help with getting this computyer to boot back into Windows as all of the church information is badly needed. Can someone please help me to resolve this terrble problem fast!! Thank you!!

PS: I will need to be lead in what to do as I know nothing about Linux or Grub or what to look for through Ubuntu.

---

### Post by chinaski on 2006-08-22
pls open a termina and post the output of 

```
cat /boot/grub/menu.lst
```

---

### Post by chinaski on 2006-08-22
> **chinaski said:**
> pls open a terminal and post the output of 

```
cat /boot/grub/menu.lst
```

edit: also, do you remember *if *and *where* you installed GRUB during Ubuntu installation process?

I made I mess with posts... didn't mean to quote myself but only edit first post... nevermind...

ok, you have to:

1) from top menu choose -> Applications -> Accessories -> Terminal

a winbdow opens and that's the command line interface

inside it type
```
cat /boot/grub/menu.lst
```
and hit enter

then copy&paste here what it gives you in return (you can use your mouse as under windows to copy&paste)

---

### Post by Fatjoint on 2006-08-22
Don't worry, we'll get you going again.  With the right info, it's possible to get you back up and running in just a few minutes.



1) from top menu choose -> Applications -> Accessories -> Terminal

a winbdow opens and that's the command line interface

inside it type:

```

cat /etc/fstab

```

Then copy and paste it into your reply.  The information that Chinaski asked you with the information this gives will help us get you going again.

---

### Post by victron on 2006-08-22
Hello there,

I am having a similar problem.  I first installed dapper, then xp, and found to my unsurprised dismay that windows had wiped out grub.  So I tried following some tutorials and such, as evidenced by what I will add below, but to no avail; selecting windows at my new grub menu merely echos the settings I typed into my menu configuration file, then freezes.  Isn't there a way of running whatever script the ubuntu installer uses to re-setup grub?  I remember installing xp, then breezy, and it did a fine job at setting things up without me having to type anything into a terminal.  Well anyways, please give me some words of advice.

The output from the two files you mentioned above:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /music          vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hdb1       /storage        vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


--------------------------------------------


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=/dev/hda1 ro

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Windows XP, SP2
map             (hd0,3) (hd0,0)
map             (hd0,0) (hd0,3)
root            (hd0,3)
chainloader     +1

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

Thanks!

---

### Post by sforeste on 2006-08-22
Thank you for those that are trying to help me now. I am currently at home and no longer in front of the church computer. I had to phone the pastor and inform him of the problem but that we had the permission of the associate pastor and the church administrator to install Ubuntu on the main computer. It is currently 10:10 PM here in Toronto and I will post the information requested as son as I am back at the church tomorrow. Good night everyone and thank you for your offer of assistance as it is greatly appreciated!

---

### Post by confused57 on 2006-08-22
> **sforeste said:**
> Thank you for those that are trying to help me now. I am currently at home and no longer in front of the church computer. I had to phone the pastor and inform him of the problem but that we had the permission of the associate pastor and the church administrator to install Ubuntu on the main computer. It is currently 10:10 PM here in Toronto and I will post the information requested as son as I am back at the church tomorrow. Good night everyone and thank you for your offer of assistance as it is greatly appreciated!
You might also want to post the output of:
```
sudo fdisk -l
```
The -l is a small "L".

This will give the partition tables on your hard drives.

---

### Post by confused57 on 2006-08-22
victron,

Here is an excellent "howto" for reinstalling grub using the Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by victron on 2006-08-22
Hehe it just so happens that's the first tutorial I tried.

After that didn't work, you'll notice I added the two "map" lines that I ripped off another tutorial because xp supposedly does not like to run in a non-first-drive-first-partition scenario.  Do you know what I should type into the .lst file to get it to work properly?

Thanks.

edit: btw to clarify the "that didn't work"... What happened after the tutorial you posted was that GRUB would only boot to Ubuntu.  It doesn't seem to recognize windows... So I followed more tutorials which told me to edit the .lst file.

---

### Post by confused57 on 2006-08-23
> **victron said:**
> Hehe it just so happens that's the first tutorial I tried.

After that didn't work, you'll notice I added the two "map" lines that I ripped off another tutorial because xp supposedly does not like to run in a non-first-drive-first-partition scenario.  Do you know what I should type into the .lst file to get it to work properly?

Thanks.

edit: btw to clarify the "that didn't work"... What happened after the tutorial you posted was that GRUB would only boot to Ubuntu.  It doesn't seem to recognize windows... So I followed more tutorials which told me to edit the .lst file.
What is the output of the command I mentioned earlier:
```
sudo fdisk -l
```
(see previous reply)
This may give an indication of what may be needed to get Windows to boot.

---

### Post by victron on 2006-08-23
Alright here it is:

```

Disk /dev/hda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1305    10482381   83  Linux
/dev/hda2            1306        1371      530145   82  Linux swap / Solaris
/dev/hda3   *        1372        3560    17583142+   b  W95 FAT32
/dev/hda4            3561        4864    10474380    f  W95 Ext'd (LBA)
/dev/hda5            3561        4864    10474348+   7  HPFS/NTFS

Disk /dev/hdb: 13.6 GB, 13613064192 bytes
255 heads, 63 sectors/track, 1655 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1655    13293756    c  W95 FAT32 (LBA)

```
edit: I hope my attempt at BBCode works...
edit2: Yes it did, but how do you make sure code is in monospaced font...

Thanks again.

---

### Post by confused57 on 2006-08-23
> **victron said:**
> Alright here it is:

```

Disk /dev/hda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1305    10482381   83  Linux
/dev/hda2            1306        1371      530145   82  Linux swap / Solaris
/dev/hda3   *        1372        3560    17583142+   b  W95 FAT32
/dev/hda4            3561        4864    10474380    f  W95 Ext'd (LBA)
/dev/hda5            3561        4864    10474348+   7  HPFS/NTFS

Disk /dev/hdb: 13.6 GB, 13613064192 bytes
255 heads, 63 sectors/track, 1655 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1655    13293756    c  W95 FAT32 (LBA)

```
edit: I hope my attempt at BBCode works...
edit2: Yes it did, but how do you make sure code is in monospaced font...

Thanks again.

I'm assuming you reinstalled Windows on hda3, but I see you also have a bootable flag on hdb1 and there's not one on hda1 for Linux.
I'm not sure, but if you did install Windows on hda3, this entry in your menu.lst "might" boot Windows:
```
title Windows XP
root (hd0,2)
makeactive
chainloader +1
```

---

### Post by victron on 2006-08-23
Okay I just noticed those flags after you mentioned them... I don't remember setting it up in that odd fashion seeing as how hda3 is just a bunch of mp3 files. Windows is installed to hda4, and apparently it made itself a sort of "inner partition" which is now called hda5. By the way, hdb1 is a bunch of documents and such, so in effect, save for the swap partition, every partition that is in fact supposed to be bootable does not have the bootable flag, and vice versa.  Somehow I have been able to boot both linux and windows though, just not together.  Anyways, I tried:

title Windows XP
root (hd0,3)
makeactive
chainloader +1

And it still does not work.  Is there some way to re-trigger the script that the ubuntu installer invokes for configuring GRUB?  Or would fixing the boot flags help?  If so, how would I do that... I am on the Ubuntu live CD right now and GParted does not seem to allow me to change any flags.  Thanks.

---

### Post by sforeste on 2006-08-23
Hello Ubuntu Community! I am back at the church computer and I am now posting the requested information below in this post and I am hoping that the community can help us get back to the main computer Windos XP information. I just want to say thank you to everyone who is taking the time to offer their assistance.

herman@herman-desktop:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=/dev/hda1 ro

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
herman@herman-desktop:~$

herman@herman-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
herman@herman-desktop:~$ cat /etc/fstab

herman@herman-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9553    76734441   83  Linux
/dev/hda2            9554        9729     1413720    5  Extended
/dev/hda5            9554        9729     1413688+  82  Linux swap / Solaris
herman@herman-desktop:~$

---

### Post by Tomosaur on 2006-08-23
sforeste, I don't quite know how to tell you this, but... it looks like you've completely formatted windows. How did you install Ubuntu - the graphical installer? If so, it looks like you selected the option to completely wipe your hard drive before installing. I'm very sorry, but you simply can't get Windows back unless you have an installation disk lying around. You see, when you're installing Ubuntu, if you want to set up a dual boot system (ie, windows AND Ubuntu), you need to choose the 'manually edit the partition table' option. You must have selected the first, complete format option instead.

Very sorry, but theres nothing that can be done :S

EDIT: Victron, you do not need a bootable flag on every partition - only Windows needs one. You can change which partitions have the boot flag via this method:
Open a terminal, and type:
'sudo parted -i /dev/hda'

Once inside parted, type the following:
'set 3 flag off'
and then
'set 4 flag on'

Exit parted, and try to boot Windows. Hope that helps you out. The fact that you seem to have two different filesystems residing in the same partition is a bit bizarre, but I'm not sure whether that is actually a problem or not.

---

### Post by randell6564 on 2006-08-23
> **sforeste said:**
> Hello! I am new to Linux and we decided that we would like to look at an alternative to Windows XP. We found Ubuntu and downloaded it and burned the CD and tried to put it on 1 computer but either the computer was too old or there was not enough room to run from the CD.

So we have a main computer here that is virtually brand new with 2 hard drives and lots of space. So we were given permission to allow Ubuntu to be installed as a dual boot and we would make Windows XP the primary boot and use Ubuntu to play around with and get familiar with and make a decision to switch over at a later time.

The installation went smoothly and I just selected all of the defaults and it all installed without a hitch. We like very much Ubuntu and played around with it but when we were ready to leave for the day we tried to boot the computer again and all it does is boot into Ubuntu. The CD is not in the computer.

I have looked at the bootloader file and all it has is Ubuntu and Windows is NOT listed as a option. I have no idea how to use GRUB and I have searched the internet as well as your forums and guides to resolve this problem and I have been here for almost 4 hours and I am feeling very sick now because they are not going to be able to use this main church computer tomorrow.

I really need somone's help with getting this computyer to boot back into Windows as all of the church information is badly needed. Can someone please help me to resolve this terrble problem fast!! Thank you!!

PS: I will need to be lead in what to do as I know nothing about Linux or Grub or what to look for through Ubuntu.

HI!  Welcome to Ubuntu!

Sounds like you installed Grub to ubuntu's drive instead of the MBR (Master boot record).  Use the ubuntu cd and reinstall grub to your MBR.

---

### Post by Herman on 2006-08-23
victron, Is Windows the first partition on your second hard disk? 
If it is, try this entry in menu.lst,
```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

sforeste, Don't give up quite yet, your fdisk output and fstab output only show one hard disk. Didn't you say you had two hard disks in this machine? Maybe Windows is on the other disk? Are you sure that was the complete output for those two commands? 
Unfortuately, I have to got to work now, so I won't be back for twelve hours or more to be any more help. I'll check then though, and see how you are going.
Regards, Herman :D

---

### Post by Tomosaur on 2006-08-23
> **Herman said:**
> victron, Is Windows the first partition on your second hard disk? 
If it is, try this entry in menu.lst,
```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

sforeste, Don't give up quite yet, your fdisk output and fstab output only show one hard disk. Didn't you say you had two hard disks in this machine? Maybe Windows is on the other disk? Are you sure that was the complete output for those two commands? 
Unfortuately, I have to got to work now, so I won't be back for twelve hours or more to be any more help. I'll check then though, and see how you are going.
Regards, Herman :D


Unfortunately, the 'fdisk -l' command shows you all of the drives connected to the machine :S

---

### Post by victron on 2006-08-23
> **Herman said:**
> victron, Is Windows the first partition on your second hard disk? 
If it is, try this entry in menu.lst,
```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

sforeste, Don't give up quite yet, your fdisk output and fstab output only show one hard disk. Didn't you say you had two hard disks in this machine? Maybe Windows is on the other disk? Are you sure that was the complete output for those two commands? 
Unfortuately, I have to got to work now, so I won't be back for twelve hours or more to be any more help. I'll check then though, and see how you are going.
Regards, Herman :D

No I installed Windows to the 4th parition (1st for linux, second for linux swap, third for music), but it kind of made itself another sub-partition to sit in... When I could boot into Windows, it used to say that it resided in the "I" drive, and music was in the "C" drive... Anyways, I tried fixing the boot flags like Tomo said, but to no avail.  I reinstalled ubuntu (I wanted to see how fast it would be with my newly discovered Automatix installer anyways), but still, windows does not appear on the GRUB menu.

I think my main problem has something to do with GRUB not recognising NTFS (in GRUB, the filesystem is supposedly "unknown" and if I type "root (hd0,3)" and then "setup (hd0)" it says it can't mount it.  And Windows being picky about not being the first partition is probably not helping.

To sum up, I installed ubuntu dapper first, then windows xp on a non-first partition, then reinstalled ubuntu, and presently my GRUB loader only lists Ubuntu (I have not done anything to manually edit the settings after the fresh re-install).  If anybody has done something like this before, help would be greatly appreciated.

It's not that I'm absolutely dying to get back to windows -- I have a pretty sweet linux setup going -- it's just that certain things require windows, like activesyncing with my pocket pc...

Thanks everybody for you help so far!  Other than that, I can't think of much else to say as I'm fresh out of ideas at this point.

---

### Post by sforeste on 2006-08-23
Church computer update. It appears that there was only one 80GB HD insstalled on this computer which was partitioned into an equal C and D drives. The church would back up their data to the D drive and of course I did not know this going in.

So even though I chose all the right decisions to setup a dual boot computer with Ubuntu, this program does not see it that way and over wrote the partition which for all intense and puposes lost the Windows partition for us and all of the church data.

I have had too professionals call me on the phone at the curch and they both have come to the same conclusion. I am sure that this was not the intention of the Ubuntu community in charge of the release of this product but it would appear that something needs to be done to better the installer program so that a mistake like this dosen't happen accident;y to someone slse.

There is a professional that is coming to the church tomorrow morning at 9:00 AM to see if there is any way to recover from this error but the concensus is that the information is lost. The only way to recover the information would be through a data recovery specialists which would cost a lot of money.

This just a small church in a small community and do not have the aility to do that. Their financial records, donations and much more might be gone but we won't know for sure until tomorrow morning. Please let me say that I am not placing blame for this with anyone! It is just an unfortunate accident and the leaders within the church know that my intentions were to do good and not evil and that I had their permission.

I don't know if you have any influence with this product but it appears that the installer needs work and whatever you can do to influence a better product for everyone I would ask you to do please so that the end result is we do not see this happen to anyone else. Thank you to all who have taken the time to read these post and who have volunteered your time to help it has been greatly appreciated!!

---

### Post by confused57 on 2006-08-23
> **victron said:**
> No I installed Windows to the 4th parition (1st for linux, second for linux swap, third for music), but it kind of made itself another sub-partition to sit in... When I could boot into Windows, it used to say that it resided in the "I" drive, and music was in the "C" drive... Anyways, I tried fixing the boot flags like Tomo said, but to no avail.  I reinstalled ubuntu (I wanted to see how fast it would be with my newly discovered Automatix installer anyways), but still, windows does not appear on the GRUB menu.

I think my main problem has something to do with GRUB not recognising NTFS (in GRUB, the filesystem is supposedly "unknown" and if I type "root (hd0,3)" and then "setup (hd0)" it says it can't mount it.  And Windows being picky about not being the first partition is probably not helping.

To sum up, I installed ubuntu dapper first, then windows xp on a non-first partition, then reinstalled ubuntu, and presently my GRUB loader only lists Ubuntu (I have not done anything to manually edit the settings after the fresh re-install).  If anybody has done something like this before, help would be greatly appreciated.

It's not that I'm absolutely dying to get back to windows -- I have a pretty sweet linux setup going -- it's just that certain things require windows, like activesyncing with my pocket pc...

Thanks everybody for you help so far!  Other than that, I can't think of much else to say as I'm fresh out of ideas at this point.
Yes, it's pretty hard to dualboot with Windows on a partition located after the Ubuntu partition...here's someone who had success doing so(may not help, but it can be done):
[http://www.ubuntuforums.org/showthread.php?t=225583&page=2](http://www.ubuntuforums.org/showthread.php?t=225583&page=2)

---

### Post by Paul133 on 2006-08-23
I'm thinking of dualbooting Ubuntu (which I'll install from the alternate CD) and XP (which I have now), and I think that I'll choose the first option for partitioning, shrinking Windows and using the extra space. Will that kill Windows and should I do the manual partitioning instead? If so, how should I partition my 40GB drive which currently has roughly 15GB used  space and 18GB free space (before defragmentation)? And do I need to defragment if I'm using the text installer?

---

### Post by victron on 2006-08-23
> **confused57 said:**
> Yes, it's pretty hard to dualboot with Windows on a partition located after the Ubuntu partition...here's someone who had success doing so(may not help, but it can be done):
[http://www.ubuntuforums.org/showthread.php?t=225583&page=2](http://www.ubuntuforums.org/showthread.php?t=225583&page=2)

No luck.  I copy and pasted his exact code into my lst file, changing his hd0,1 to hd0,3 for me, and I still get an "error 12" from GRUB.  Then I changed it to hd0,4 just in case (the weird double partition thing windows has going is kind of confusing), but that didn't work either. :(

Is GRUB supposed to report that windows uses an unrecognized filesystem?

---

### Post by Herman on 2006-08-24
victron,
Okay, try this then:
```
 # This entry automatically added by the Debian installer for a non-linux OS
 # on /dev/hda5
 title		Windows XP.
 rootnoverify		(hd0,4)
 savedefault
 makeactive
 chainloader	+1

```Hd0,4 should be correct for hda5, and I suggest changing from root to rootnoverify so Grub won't attempt to mount your NTFS partition.
I hope that helps, Regards, Herman

---

### Post by chinaski on 2006-08-24
> **sforeste said:**
> 
So even though I chose all the right decisions to setup a dual boot computer with Ubuntu, this program does not see it that way and over wrote the partition which for all intense and puposes lost the Windows partition for us and all of the church data.

I do not think Ubuntu installer made any mistake

more likely you choose wrong option, and by writing this you might confuse potential new user reading this thread
> it would appear that something needs to be done to better the installer program so that a mistake like this dosen't happen accident;y to someone slse.

It is a little bit difficult only if you choose to manually edit partition table

on dual boot machines, I always create free space before I install Ubuntu, or choose the "resize" option
> 
I don't know if you have any influence with this product but it appears that the installer needs work and whatever you can do to influence a better product for everyone I would ask you to do please so that the end result is we do not see this happen to anyone else.
I'm sorry, but you could have read some info on how to install it before doing it

if you crash with your car because you never take driving lessons, you cannot actually blame car manufacturer for that

---

