---
title: "UUID and disk cloning"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by ntalamai on 2008-01-26
Hello,

I am pretty new to Ubuntu (7.10) so please bear with me. Here comes my problem: I had a 300GB IDE hard disk, with Windows and Ubuntu installed. Everything worked fine.

Then I decided to purchase a 500GB SATA hard drive and use as my primary drive, while keeping the old 300GB IDE one as a backup. I used Acronis TrueImage to repartition the new hard disk and transfer all partitions into it.

I will go gradually to the current state of the problem, as I believe this is the best way to describe my situation. Apologies if long stories bore you...

Step 1:
Unplug the old 300GB IDE one and plug the 500GB SATA one. Windows booted perfectly, so did Ubuntu (I have to admit that Acronis did a great job), BUT in Ubuntu I had no SWAP. 
blkid outputs:
```
/dev/sda1: UUID="EDCD1C8DCD1A9EB" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="f95569d9-5504-4145-a9de-207921941fc3" 
/dev/sda3: UUID="63f7cd46-f14b-4e6c-8dbb-75da9a2c7331" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="adfc9d32-bc04-48c1-8e34-1de87acd7d78" SEC_TYPE="ext2" TYPE="ext3" 
```

What had happened is: when Acronis cloned the hard disk, sda1, sda3, sda4 got exactly the same UUIDs as with my previous hard drive. But swap had gotten a new UUID for unknown reasons. After searching, the solution was to find the new UUID for the swap partition and overwrite it into the fstab file, and behold, everything works fine!

Step 2:
That is, until I decided to attach both of my drives in order to use the old 300GB IDE as a backup. BIOS is set so that OS loads from the 500GB SATA one. That is fine. I can see the GRUP menu, and then whatever I choose, it boots from old hard drive! That is, if I choose Windows it boots from hda1, instead of sda1. For linux it uses hda3 instead of sda3.

Cause must be that the partitions in both drives have the same UUID. Apart from the swap on /dev/sda2, /dev/hda2 which as I explained before, are different. This has the effect that even when the OS boots from the old drive, the SWAP is located on the new one! This is because the SWAP UUID in the fstab file is that of the new hard disk.

To recap:
a) Cloned old 300GB IDE to new 500GB SATA with Acronis. 
b) Using only the 500GB I had a minor problem with SWAP which I overcame. Apart from that everything is perfect.
c) Using both hard disks, in loading, the old hard disk boots, because partitions have the same UUIDs!

Here are some useful files:
/boot/grub/menu.lst
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
# kopt=root=UUID=63f7cd46-f14b-4e6c-8dbb-75da9a2c7331 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=63f7cd46-f14b-4e6c-8dbb-75da9a2c7331 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=63f7cd46-f14b-4e6c-8dbb-75da9a2c7331 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

/etc/fstab when I only use the 500GB drive. I will boot from both and will post the fstab file from there. 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=63f7cd46-f14b-4e6c-8dbb-75da9a2c7331 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=adfc9d32-bc04-48c1-8e34-1de87acd7d78 /home           ext3    defaults        0       2
# /dev/sda1
UUID=0EDCD1C8DCD1A9EB /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=f95569d9-5504-4145-a9de-207921941fc3 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

sudo fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d5fe889

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7708    61914478+   7  HPFS/NTFS
/dev/sda2            7709        7977     2160742+  82  Linux swap / Solaris
/dev/sda3            7978       10150    17454622+  83  Linux
/dev/sda4           10151       60801   406854157+  83  Linux
```

Is there any proper way of fixing this? With "proper" I mean a way to alter UUID or sth in order to have both hard disks intact. I do not want to format the old hard disk yet. That is a "brute force" approach that will be my last resort.

If anything is not clear, please do ask!

Thanks!

---

### Post by ntalamai on 2008-01-26
Ok, now I have both hard disks in the system. The fstab file reads:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=63f7cd46-f14b-4e6c-8dbb-75da9a2c7331 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=adfc9d32-bc04-48c1-8e34-1de87acd7d78 /home           ext3    defaults        0       2
# /dev/sda1
UUID=0EDCD1C8DCD1A9EB /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=f95569d9-5504-4145-a9de-207921941fc3 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

And the output of sudo fdisk -l is:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d5fe889

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7708    61914478+   7  HPFS/NTFS
/dev/sda2            7709        7977     2160742+  82  Linux swap / Solaris
/dev/sda3            7978       10150    17454622+  83  Linux
/dev/sda4           10151       60801   406854157+  83  Linux

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06b7a520

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3971    31897026    7  HPFS/NTFS
/dev/hda2            3972        4093      979965   82  Linux swap / Solaris
/dev/hda3            4094        5917    14651280   83  Linux
/dev/hda4            5918       36481   245505330   83  Linux

```

Both hard drives are recognised.. BUT if I go to my computer I cannot see the new drive... :confused:

Any suggestions (apart from formating the old hard drive) are most welcomed...

---

### Post by ntalamai on 2008-01-27
Hi,

why isn't anyone answering my question? If it doesn't make sense or there are bits that I don't explain properly, please do ask!

---

### Post by slaguth on 2008-01-27
I have the same problem, having moved from an 160GB drive to a 300GB drive using Maxtor MaxBlast (made by Acronis?). The only thing is that grub seems to choose randomly between what drives to boot instead of choosing the same one every time, and swap wasn't a problem for me.

I have another thread on more or less the same topic, but the only advice I've gotten so far is format the drive. ([http://ubuntuforums.org/showthread.php?t=679144]("http://ubuntuforums.org/showthread.php?t=679144"))

I would appreciate any help you get on this. Otherwise I am just going to have to format the old drive and recopy everything.  (Which has the additional annoying property that I can't use MaxBlast to clone the drives automatically or I will get into the same problem again.)

---

### Post by EdWh on 2008-01-27
Hi Folks.
Just a note to say, I use Acronis from my WinXP drive to do all my formats, etc. 
I use Acronis True Home to clone my Hdd and it will enlarge your current drive to fit  the new drive and increase partitions and sizing as needed   Just go to clone drive and follow prompt's  you will get messages that the drive has Linux on it and leads you to believe it will be a problem and it is not.   It will clone the boot sectors and all, only problem I had is following prompts it take some time to vector all the info, you need to be patient and let it do it's work.   I have never had it fail, and I use it every month to clone to a second drive for a back up.                           Hope it helps.  (True home not Disk Management). Ed.

---

### Post by ntalamai on 2008-01-29
Hello there,

I am glad that someone has the same problem, this at least means that I didn't do anything wrong. 

Btw, it GRUB cannot randomly select between the two drives: it only selects the old drive! :(

Anyway, I am afraid that formatting the old drive partially causes another problem (don't know if you experienced it as well). For some reason I can no longer see the windows partition! :confused:

Previously, the partition was mounted to /media/hda1. Now 
```
ls -l /media/hda1
total 0

```

Ok, I found quick fix to this solution. fstab was changed changed to:
```

# /dev/sda1
UUID=0EDCD1C8DCD1A9EB /media/sda1     ntfs    defaults,umask=007,gid=46 0      

```,

But there was no directory /media/sda1 (only /media/hda1). So I needed to create the directory /media/sda1/ where the auto-mount process during the bootup will mount the device /dev/sda1.

Hope this helps somehow.

---

### Post by ntalamai on 2008-01-29
Btw, I formatted the old drive using Acronis again. I booted into windows having connecting only the old drive. There is an option in Acronis to do destructive format on the drive. It reboots, locks the drive and that's all. 

Anyway it sucks we cannot keep that drive as well as a backup of not only the data, but the programs as well. I didn't try to use the old drive externally, via a USB connection. But that's not a proper solution, is it? I mean we should be able to use this drive internally, were it not for the UUID problem. :(

---

### Post by tact on 2008-01-29
You have discovered that when you clone disks you also clone the UUID and that sometimes has negative impacts.

To fix this you have to create new UUIDs for each partition on the cloned drive.  Then whenever 
both drives are plugged in to the same machine - all partitions will have unique UUIDs

Steps you must take for each and EVERY partition on the cloned drive:
1.  Generate a new UUID

At the terminal prompt type:
```
uuidgen
```
(a unique number you can use as a UUID will appear - copy to paste into next command)

```
sudo tune2fs /dev/sdb? -U paste_above_number_here
```
(replace sdb? with whatever your drive designation actually is - e.g. sdb2, hdb3, etc)

You can check the UUID associated with a partition with this command at a terminal:
```
vol_id /dev/sdb?
```

Repeat the above for each partition and now you will have a "clone" drive that at least has 
unique UUIDs for each partition and wont cause problems due to duplicated UUIDs caused by the cloning process.

note:  If you tried to change the UUID on your linux-swap partition above you got an error right?  To change the UUID for that linux-swap partition you are going to have to run a partition editor like gparted (sudo apt-get install gparted).  Delete the swap partition and recreate it.  This action generates and saves a new UUID.  Use vol_id to find what it is.

Now....if you changed the partition UUID's for any bootable partition,  that partition will no longer be able to boot because:
a.  the new UUIDS wont match your grub boot setup and
b.  the new UUIDs wont match the references in /etc/fstab

So....
EDIT MENU.LST and FSTAB
correct all the UUID's in both files.  (if you forgot it use the vol_id command to find out)

One more thing about bootable partitions and changed UUID's....  if you ever run "update-grub" the old UUIDs will come back and bite you.  trust me. 

And don't forget that some updates (like a new kernel) will have your system automatically run "update-grub" and so you dont escape saying you just wont do that.

So...
Now you have to actually boot from your new clone drive and since you edited /boot/grub/menu.lst to set the corerct UUID's it should boot.

 Once booted... delete  /boot/grub/ menu.lst and recreate it - this is the only way to get your new system to pick up the new UUIDs.  As mentioned above if you dont do this step... any time in the future an "update-grub" is done on this system the OLD UUIDs will turn up in your grub menu.lst and your system will not boot.

So the steps to backing up menu.list and deleting it in one step are:
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak

then:

sudo update-grub

Done.

---

### Post by tact on 2008-01-29
> **ntalamai said:**
> Btw, I formatted the old drive using Acronis again. I booted into windows having connecting only the old drive. There is an option in Acronis to do destructive format on the drive. It reboots, locks the drive and that's all. 

Anyway it sucks we cannot keep that drive as well as a backup of not only the data, but the programs as well. I didn't try to use the old drive externally, via a USB connection. But that's not a proper solution, is it? I mean we should be able to use this drive internally, were it not for the UUID problem. :(

having duplicate UUID's will cause problems even if you connect the drive as an external USB drive (it will not automount for one)

See whether you can understand that I wrote above. See if it helps.    (Its all been posted before in these forums and had you searched on relevant terms would have turned up this advice days ago)  

Ciao

---

### Post by tact on 2008-01-29
> **ntalamai said:**
> ...Anyway it sucks we cannot keep that drive as well as a backup of not only the data, but the programs as well. I didn't try to use the old drive externally, via a USB connection. But that's not a proper solution, is it? I mean we should be able to use this drive internally, were it not for the UUID problem. :(

I have a spare HDD and have it in a case connected via USB then use the built in linux commandline program dd to periodically clone my internal HDD.

Actually - after cloning the internal drive to the external (thus giving me a fully bootable copy of my working drive)  I always take swap the drives - removing the internal drive and replacing it with the external one.   That way I KNOW the clone is working, boots, etc...   and I KNOW that the backup I have is also good (because it was only moments before the working internal drive).  hehehe.

Of course the above process is time consuming and so I do not do it all that often...  but very regularly between  full cloning exercises I use grsync to back up changed files from internal to external drive.  (and of course every time I connect to the corporate LAN in the office my system auto backs up to the corporate file server too.)

The thing is..  whenever I do the cloning I have to follow the steps I outlined in other posts to ensure that all the partitions on the cloned drive have unique UUID's else when I connect it (even via USB) I can have problems.

You can do it... just need to jump thru some hoops.  Its not linux or windows' faults.  Its how HDD cloning works.  :)

---

### Post by ntalamai on 2008-01-30
Hello tact,

thanks for your advice. Truth is that I googled a bit (a lot) before posting to the forum. Perhaps I didn't use the right keywords (UUID disk cloning ubuntu).

I didn't try the steps cause I have already formatted the old hard disk and I don't wont to risk damaging something already working. Anyway I will save your post for future reference - your tutorial seems completely sensible. 

Just a question: why should I change the UUIDs of the new hard disk, and not change the UUIDs of the old drive? The uuid generation algorithm should give different id for the old drive than those it had before, right? At least the GUID algorithm in Microsoft COM takes into account host's local time, so it should be different. That way I don't have to change grub. But anyway, it all depends what you want to do with the old hard disk. Perhaps the best option is to do what you do: clone into an external drive and get a full backup of your system. Or set-up a RAID. Anyway, let's not go into that now, as it has to do with budget/time constraints, etc.  

> Once booted... delete /boot/grub/ menu.lst and recreate it - this is the only way to get your new system to pick up the new UUIDs. As mentioned above if you dont do this step... any time in the future an "update-grub" is done on this system the OLD UUIDs will turn up in your grub menu.lst and your system will not boot.

So the steps to backing up menu.list and deleting it in one step are:
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak

then:

sudo update-grub

By first deleting and then updating, I suppose that in the future, there will be no "update-grub" problems, right?

Thanks again.

---

### Post by tact on 2008-01-30
> **ntalamai said:**
> Just a question: why should I change the UUIDs of the new hard disk, and not change the UUIDs of the old drive? 


Yep you can change either - whatever works best for you.  Just remember if you change UUID on a partition you want to boot some day that you have to boot from it at some stage and to the "delete/recreate" menu.lst trick so that "update-grub" does the right thing in the future.

> **ntalamai said:**
> 
By first deleting and then updating, I suppose that in the future, there will be no "update-grub" problems, right?


Yep thats the idea. It seems thatwhen the update-grub process runs for the first time (or whenever it cannot find /boot/grub/menu.lst) it then reads the UUIDs from the partitions, puts them in menu.lst and saves them somewhere.   I dont know where it saves them, but on any subsequent run of update-grub it uses the saved values.    Which is no problem at all unless you changed UUIDs .

---

