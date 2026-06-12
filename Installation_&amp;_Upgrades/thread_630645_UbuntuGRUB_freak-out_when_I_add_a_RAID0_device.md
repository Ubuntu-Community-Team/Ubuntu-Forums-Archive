---
title: "Ubuntu/GRUB freak-out when I add a RAID0 device"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Wayno-san on 2007-12-03
This problem has been a thorn in my side for over a week now I'm about ready to give up on Ubuntu.  :(

Here's the skinny: I had 3 hard drives on my machine with 3 OSes... _and Ubuntu/GRUB worked fine_...
Then I added a RAID0 device (2HDs on Nvidia fakeRAID), which does not have any Ubuntu files on it and which I don't need to access from Ubuntu.  I added this as the LAST boot HD in BIOS.

First GRUB, then UBUNTU fall to their knees.  With GRUB, I get an Error 17.  I can get whatever OS to boot up if I use the "Super GRUB Disk".  Why does Super GRUB not complain when it's using the same menu.lst?  I double checked the hard drive pointers, 'device.map', use 'rootnoverify', tried putting /boot on different partitions, etc.  I've tried re-installing Ubuntu/GRUB with and without the dmraid package and with/without the RAID0 device connected but still I get this Error 17 if I enable the RAID0 device (or if it's already enabled).

Then, Ubuntu crashes when booting in one of two ways:
1-If RAID0 is enabled when I install Ubuntu/GRUB):
running scripts /init-bottom
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
(initramfs)>

OR

2-If I enable the RAID0 after installing Ubuntu/GRUB)"
mount different device under /dev/mapper directory
eg: /dev/mapper/nvidia_eahaabcc1 see dmraid doc for details
fsck failed

[COLOR="Green"]So my question is: What **EXACTLY **do I need to do to Ubuntu and GRUB _BEFORE I can add_ a RAID0 device to the system so neither will freak?[/COLOR]

Just to clarify, I'm NOT trying to install any part of Ubuntu or GRUB on the RAID device and I only need to access the RAID device from GRUB to boot the Vista that's on it.  I turn the RAID device on in BIOS as my LAST HD in the boot order so it's not effecting the "hd0, hd1, etc." drive order at all.

Thanks, 
Wayne

---

### Post by Pumalite on 2007-12-03
It doesn't matter. Ubuntu has to know about your Raid from the start. You are adding something to the mix AFTER you have configured Ubuntu for a different hardware.

---

### Post by Wayno-san on 2007-12-03
I tried it both ways... with the RAID0 device connected when I do the Ubuntu/GRUB install, and without it connected.  As stated in the first post, I still get a GRUB and Ubuntu error even when the RAID0 is connected when I install the OS.  :(  

I think the missing link is that I have to somehow install 'dmraid' when I install Ubuntu, even though I don't install the Ubuntu on the RAID device.  Additionally, I think 'dmraid' needs to somehow be a part of the bootup sequence.

What do you think?

Thanks, 
Wayne

---

### Post by Pumalite on 2007-12-03
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Wayno-san on 2007-12-03
It appears that most of this doesn't apply since I'm not installing Ubuntu onto the RAID device.  The first part looks like a PITA and I'm not familiar enough with the command line to even try it.  I think I'd be posting A LOT for requests for help if I did try.  LOL

But it appears that the section _Install the Bootloader Package_ is something that I need to do to get rid of the Error 17 (hopefully).  The doc then states the next chapter does not apply.  Finally, it looks like configuring the fstab file under _Mount your FileSystems_ might also apply.

Do you think it would be possible to install the OS w/o GRUB first, then load it in the LIVE CD to adjust the fstab file, then finally install GRUB?

Thanks, 
Wayne

---

### Post by meierfra on 2007-12-03
5 days  ago you claimed in this  [thread ]("http://ubuntuforums.org/showthread.php?t=624220") that you solved your problem.. What has happened since then?

---

### Post by Wayno-san on 2007-12-04
meierfra, 
Basically this: [http://ubuntuforums.org/showthread.php?t=626279](http://ubuntuforums.org/showthread.php?t=626279)

My latest kernel got corrupt somehow (Ubuntu would not boot when I selected that option in GRUB).  Tried to get some help to fix it but no luck with the suggestions so I tried doing a re-install a few times since then to get it back... but every time I reinstall I end up getting one of the errors specified in my first post here.  :(     It's embarrassing because I thought we had this licked.  Guess I shouldn't have celebrated so quickly.  I spent the entire weekend trying to re-install in different ways to get it to work... using the standard and alternate CDs, with and without RAID0, different drive boot orders, etc.  I did a nice load last night (with RAID0 drives off) thinking I would back it up by copying the partition so I wouldn't have to re-install again. I set everything up the way I wanted it and made a backup.  The config got screwed up again... so I copied the backup partition back over... and then I get all these fsck errors!!!!!!!!!!!!!   Argh!!!!!!  ](*,)     REALLY frustrating.

So it looks like I have to try to re-install AGAIN... but I'm not going to  proceed until I have a solid plan and decent confidence that it will work.  I'm hoping that someone that has set up a similar configuration will chime in...

-Wayne

---

### Post by meierfra on 2007-12-04
It seems to me that Grub  reaches the kernel and so Grub is install correctly in the MBR and the "root (hd?,?)" statements in menu.lst are correct.    That should also mean that the grub menu appears at boot-up (fter pressing "esc" if necessary). Is that true?

Did you ever  compare the "root=UUID=......' statement  in menu.lst with the output of "sudo blkid"

Also see what happens if  you to replace    "root=UUID=..." by "root=/dev/xyz", where /dev/xyz is your ubuntu /-partition.

---

### Post by Wayno-san on 2007-12-04
Yes, GRUB appears when I boot up.... but if I have the RAID0 drives enabled in BIOS I get an "Error 17" after "Stage 1.5" and it stops there before getting to the OS selection menu... unless I use the _Super Grub Disk_... then it boots up fine.  

[I]>Did you ever compare the "root=UUID=......' statement in menu.lst with the output of "sudo blkid"

Also see what happens if you to replace "root=UUID=..." by "root=/dev/xyz", where /dev/xyz is your ubuntu /-partition.<[/I]

No, I didn't know about the blkid command.... I will do and I will try your replacement suggestion also.


Thank you, 
Wayne

---

### Post by psusi on 2007-12-04
I think you are having the two following problems:

1)  If you install with the raid enabled, Linux sees the raid disks first and so grub installs there, even though you told the bios to map them after the other disks because grub has no way of detecting this.

2)  If you add the raid later, the kernel again sees the raid disks first, which moves the old disks around so it can't find the root filesystem.

Post your /boot/grub/menu.lst file and your /etc/fstab.  

To solve problem 1, you need to tell grub about the proper order of your disk drives and reinstall it, to solve problem 2, you need to correct your menu.lst to point to the right root filesystem.

---

### Post by Wayno-san on 2007-12-04
My last install attempt was with the RAID0 device disabled during install so I should probably re-install again with it enabled before I generate these logs.  They'll probably be more meaningful then.

Thanks again, I'll report back tomorrow.
-Wayne

---

### Post by Wayno-san on 2007-12-05
OK, I re-installed Ubuntu yet again.  I documented the entire procedure.  You can skip to the end to see the results and then take a look at the info.

**0.5.** My boot order in BIOS is:
Ch0 M
SATA1 M
SATA2 M
SCSI-0
(The SCSI-0 is the RAID0 device which are drives on SATA3 & SATA4.  Ch0 M is the only IDE drive.)

**1.**  Booted Live CD x64
**2.**  Installed dmraid
**3.**  Ran the following commands to see what gives...

```
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "nvidia_aafdehbg" already active
RAID set "nvidia_aafdehbg1" already active
RAID set "nvidia_aafdehbg2" already active
RAID set "nvidia_aafdehbg3" already active
RAID set "nvidia_aafdehbg5" already active
RAID set "nvidia_aafdehbg6" already active
RAID set "nvidia_aafdehbg7" already active
RAID set "nvidia_aafdehbg8" already active
RAID set "nvidia_aafdehbg9" already active
ubuntu@ubuntu:~$ 
```

**4.**  ```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc3bbc3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     4193028   320625269   158216121    7  HPFS/NTFS
/dev/sda2              63     4192964     2096451   82  Linux swap / Solaris
/dev/sda4       320625270   488392064    83883397+   f  W95 Ext'd (LBA)
/dev/sda5       320625333   425481524    52428096    b  W95 FAT32
/dev/sda6       425481588   434285144     4401778+  93  Amoeba

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x383e1ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   104856254    52428096   83  Linux
/dev/sdb2       104856255   488392064   191767905    5  Extended
/dev/sdb5       104856318   209712509    52428096   83  Linux
/dev/sdb6       209712573   488392064   139339746    7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b056ae8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     3148739     1574338+   7  HPFS/NTFS
/dev/sdc2         3148740     6297479     1574370   82  Linux swap / Solaris
/dev/sdc3   *     6297480    79698464    36700492+   7  HPFS/NTFS
/dev/sdc4        79698465  1250274689   585288112+   f  W95 Ext'd (LBA)

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34e434e3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   111683879    55841908+   b  W95 FAT32
/dev/hda2       111683880   312576704   100446412+   f  W95 Ext'd (LBA)
/dev/hda5       111683943   312576704   100446381    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_cddecffe", stripe, ok, 488397166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_cddecffe", stripe, ok, 488397166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_aafdehbg", stripe, ok, 625142446 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_aafdehbg", stripe, ok, 625142446 sectors, data@ 0
ubuntu@ubuntu:~$ 

```

**5.**  ```
ubuntu@ubuntu:~$ sudo dmraid -s
*** Set
name   : nvidia_cddecffe
size   : 976794112
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
*** Active Set
name   : nvidia_aafdehbg
size   : 1250284800
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
```

**6.**  
Next I started the installer and went with the Manual partitioning option.  See attachments "GParted1.jpg" & "GParted2.jpg".

**7.**
 I removed all the mount points except for the swap file on SATA1, and "/" & "/home" on SATA2.  See attachments "GParted1a.jpg" & "GParted2a.jpg".

**8.**
The "Ready to Install" screens shows this:
```
If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
 partition #2 of SCSI1 (0,0,0) (sda) as swap
 partition #1 of SCSI2 (0,0,0) (sdb) as ext3
 partition #5 of SCSI2 (0,0,0) (sdb) as ext3
```

And the advanced options I left as default (install bootloader on (hd0)).

**9.**  Install complete....

Prior to rebooting I ran some of the suggested commands.

**10.**
```
ubuntu@ubuntu:~$ sudo blkid
/dev/mapper/nvidia_aafdehbg1: UUID="7400C5E300C5AC84" LABEL="xp64_swap" TYPE="ntfs" 
/dev/mapper/nvidia_aafdehbg9: UUID="1C8306454586080" LABEL="Scratch" TYPE="ntfs" 
/dev/mapper/nvidia_aafdehbg8: UUID="1C82FE30FD8B080" LABEL="Data" TYPE="ntfs" 
/dev/mapper/nvidia_aafdehbg7: UUID="1C82FE30EA78380" LABEL="Settings" TYPE="ntfs" 
/dev/mapper/nvidia_aafdehbg6: UUID="1C82FE30C452980" LABEL="Programs" TYPE="ntfs" 
/dev/mapper/nvidia_aafdehbg5: UUID="1C82FE30A7B6600" LABEL="Entertainment" TYPE="ntfs" 
/dev/mapper/nvidia_aafdehbg3: UUID="5630A68630A66D25" LABEL="Vista32" TYPE="ntfs" 
/dev/mapper/nvidia_aafdehbg2: TYPE="swap" UUID="89c43a42-2121-4386-ad84-edc42232cefc" 
/dev/sda1: UUID="6A9CCEEC9CCEB1BD" LABEL="x64_XP" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="126a1207-bfc1-4988-862c-159b16145d79" 
/dev/sda5: LABEL="Shared Data" UUID="2C30-2C31" TYPE="vfat" 
/dev/sda6: UUID="9add84de-84e9-4842-b985-2b27f3619e66" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="005db310-044b-45a9-b369-60d287c237be" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="f325605f-df78-4448-bb91-a80d08544d33" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="17F9DA65715CEB16" TYPE="ntfs" 
/dev/hda1: LABEL="WIN2K" UUID="3E0E-67FF" TYPE="vfat" 
/dev/hda5: UUID="1C82C4C04386300" LABEL="TRANSIENT" TYPE="ntfs" 
ubuntu@ubuntu:~$
```

The UUID= reference appears to be correct.

**11.**
```
ubuntu@ubuntu:/target/boot/grub$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> geometry (hd0)
geometry (hd0)
drive 0x80: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/hda
   Partition num: 0,  Filesystem type is fat, partition type 0xb
   Partition num: 4,  Filesystem type unknown, partition type 0x7
grub> geometry (hd1)
geometry (hd1)
drive 0x81: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 4,  Filesystem type is fat, partition type 0xb
   Partition num: 5,  Filesystem type unknown, partition type 0x93
grub> geometry (hd2)
geometry (hd2)
drive 0x82: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> geometry (hd3)
geometry (hd3)
drive 0x83: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type unknown, partition type 0x7
grub> geometry (hd4)
geometry (hd4)
drive 0x84: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sdd

```

**12.**  Original menu.lst
```
ubuntu@ubuntu:/target/boot/grub$ cat menu.lst
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
# kopt=root=UUID=005db310-044b-45a9-b369-60d287c237be ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=005db310-044b-45a9-b369-60d287c237be ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=005db310-044b-45a9-b369-60d287c237be ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

**13.**  Which I modified to add XP64.  The result is this:
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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=005db310-044b-45a9-b369-60d287c237be ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=005db310-044b-45a9-b369-60d287c237be ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=005db310-044b-45a9-b369-60d287c237be ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Vista or 2000
hide		(hd1,1)
unhide		(hd3,2)
rootnoverify	(hd0,0)
makeactive
chainloader	+1

# This entry I added manually.  Hiding the Vista partition (hd3,2) to keep
# XP from wiping out the restore points.  
title		XP64
hide		(hd3,2)
unhide		(hd1,1)
rootnoverify	(hd1,0)
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I'm not sure if I should be using the reference (hd3,2) here in the hide command since this is a reference to a RAID0 partition... maybe that's why I'm getting the Error 17.  This DOES appear to work though as my Vista restore points do not get wiped out even after XP is run.

**14.**Device.map file:
```
ubuntu@ubuntu:/target/boot/grub$ cat device.map
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc
(hd4)   /dev/sdd
```

This appears as I would expect.

**15.**Fstab file: 
```
ubuntu@ubuntu:/target/boot/grub$ cat /target/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=005db310-044b-45a9-b369-60d287c237be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=f325605f-df78-4448-bb91-a80d08544d33 /home           ext3    defaults        0       2
# /dev/sda2
UUID=126a1207-bfc1-4988-862c-159b16145d79 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Hmmm.... looks like some of the drives are missing..... :confused:

**16.**  Reboot time!

**17.**  Upon reboot GRUB returns an Error 17.  

**18.**  I booted with the _Super Grub Disk_ and was able to load into the OS from the Linux menu (which used my menu.lst file without complaints).  Ubuntu didn't complain during its boot process (this time).

**19.**  Now I'm in the OS inputting this info.  I also installed "dmraid" and allowed the OS to update itself.  I'm worried that once I reboot, Ubuntu will fail to boot up due to one of the errors mentioned in the 1st post.

Thank for looking into this guys.  I think somewhere GRUB needs a "device" reference to the RAID0 partitions but I'm not sure if this needs to be in the menu.lst or elsewhere.  With regards to Ubuntu itself I'm not sure what needs to be done to keep it from failing to boot in the future.   

Right now I'm going to try to reboot and if it succeeds, make an image of the partition.  This didn't help me earlier but maybe this time....

---

### Post by Wayno-san on 2007-12-05
Well, I just rebooted... and Ubuntu wouldn't boot up.  Got this:

running scripts /init-bottom
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
(initramfs)

I'm going to go cry now....:sad:

---

### Post by meierfra on 2007-12-05
Sorry I don't understand why you thought reinstalling would make a difference.

Please describe exactly what happens during boot up. Does the grub menu appear? It seems the last time you told me that it doesn't. But I would be very surprised if you get this
> 
running scripts /init-bottom
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
(initramfs)

error message, before you choose Ubuntu at the Grub menu.

---

### Post by meierfra on 2007-12-05
If you press "c" at the grub menu,  and type "find /boot/grub/stage1", what is the output?

Did you ever try replacing "root=UUID....." by "root=/dev/sdb1" in menu.lst?

---

### Post by Wayno-san on 2007-12-06
I re-installed so I could document the whole process "fresh".  GRUB fails before it reaches the menu....  I just get:

```
GRUB loading stage 1.5
GRUB loading, please wait...
Error 17
```

If I use the _Super Grub Disk_ and choose ~Linux (Auto 1), it loads the menu fine and will initiate the boot on each of the OSes.

In response to your post from 11:34 PM:

I'm only able to get to that point by booting with the _Super Grub Disk_.  Actually, I only see 

```
(initramfs)
```

on the screen, but I hit ALT-F1 (or something like that) and I could see what (apparently) caused Ubuntu to stop booting:

```

ERROR: adding /dev/mapper/nvidia_cddecffe to RAID set
kinit: name_to_t(/dev/disk/by-uuid/126a1207-bfc1-4988-862c-159b16145d79) = sda2(8,2)
kinit: trying to resume from /dev/disk/by-uuid/126a1207-bfc1-4988-862c-159b16145d79
kinit: No resume image, doing normal boot...
mount: Mounting /dev/disk/by-uuid/005db310-044b-49a9-b369-60d287c237be on /root
failed: Device or resource busy


running scripts /init-bottom
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
(initramfs)
```


I didn't try "root=UUID....." by "root=/dev/sdb1" replacement yet... will give that a go now....

---

### Post by meierfra on 2007-12-06
Since you do not get to the grub menu, changing the UUID's will not cure the Error 17. But it might help Super Grub to get further. 


Did you ever try to fix the Error 17 in the same way  we fixed the Error 22 in your first thread:

Boot from the LiveCD.

Mount the ubuntu partition:

sudo mount -t ex3 /dev/sdb1 /ubuntu

gksudo gedit /ubuntu/boot/grub/menu.lst

In menu.lst change    all root (hd2,0)"  to root (hd0,0)". Save the file.

sudo grub
root (hd2,0)
setup (hd2)
quit

Then boot from the Ubuntu Drive.

---

### Post by meierfra on 2007-12-06
> I think you are having the two following problems:

1) If you install with the raid enabled, Linux sees the raid disks first and so grub installs there, even though you told the bios to map them after the other disks because grub has no way of detecting this.

2) If you add the raid later, the kernel again sees the raid disks first, which moves the old disks around so it can't find the root filesystem.

If psusi is right with his analysis, you should be able to solve your problem by installing Ubuntu with the  raid enabled and then use the method I showed  you a  week ago to reinstall grub and edit menu.lst.

You might also try using Easy BCD in place of Grub.   But I think this is all the advice I'm able to give you  (Sorry just don't know much about Raids)

Maybe psusi or somebody else will be able to help you further.

Does anybody now whether adding a raid can  change the UUID's or the device name (/dev/sdb1 etc) of a partition?

---

### Post by Wayno-san on 2007-12-06
I tried the UUID substitution but it had no effect.  When watching Ubuntu boot (which I'm able to start with _Super GRUB Disk_, I noticed something about a RAID mount but it scrolled by too fast.  Is there a boot log that gets stored somewhere that logs the boot process?  If not, is there a way I can turn one on?

ps:  I added some of the RAID error message (that I was able to catch) to post 16.

---

### Post by Wayno-san on 2007-12-06
In my continuing quest to figure out this RAID install issue I thought I'd try a different distro to see if I would be able to properly set-up the bootloader with my RAID drives... I was hoping to find some clues that way.  Unfortunately Fedora hung during the "install"... I tried it a couple of times.  Then I tried OpenSUSE... which detected my RAID0 device!!!   ...unfortunately it also kept insisting that my SATA1 & 2 drives are also connected in a RAID configuration... which they are not... I have RAID for those two channels turned off in BIOS, the drives just happen to be the same type.  It wouldn't let me partition just the SATA2 drive so I aborted the install for fear that it would mess up the data on my SATA1 drive (which, with my luck, I'm sure it would have).

meierfra, 
I also tried doing the hd2 to hd0 swap and that gets rid of the GRUB Error 17....  unfortunately I haven't had much luck with Ubuntu booting....  Not sure why it's trying to do this: 
ERROR: adding /dev/mapper/nvidia_cddecffe to RAID set

..since there's no RAID drives on those channels....

---

### Post by psusi on 2007-12-07
> **meierfra said:**
> Since you do not get to the grub menu, changing the UUID's will not cure the Error 17. But it might help Super Grub to get further. 


Did you ever try to fix the Error 17 in the same way  we fixed the Error 22 in your first thread:

Boot from the LiveCD.

Mount the ubuntu partition:

sudo mount -t ex3 /dev/sdb1 /ubuntu

gksudo gedit /ubuntu/boot/grub/menu.lst

In menu.lst change    all root (hd2,0)"  to root (hd0,0)". Save the file.

sudo grub
root (hd2,0)
setup (hd2)
quit

Then boot from the Ubuntu Drive.

You ALWAYS setup (hd0) since that is always the drive that PC bios boots from.  Also if I am correct that sdb1 is the /boot ( or / if you have no /boot ) partition, then you want root (hd2,0).

Is sdb1 your / partition, or is it /boot?

---

### Post by Wayno-san on 2007-12-07
Setup is run on (hd2) in that instance because it became (hd0) when I switched the boot order in BIOS on the next reboot.

sdb1 is the / partition.... I do not have a separate /boot partition.

I don't know why it makes a difference but GRUB appears to like it when Ubuntu is on the hd0 drive. (No Error 17)

---

At around 4AM I ended up clearing Windows 2000 off the first partition of the IDE drive (typically my hd0).  I think I'll try installing Ubuntu there to see if that helps.  If that doesn't work, I'll switch my BIOS boot order to SATA1, SATA2, IDE1, RAID (unless I get a better idea in the meantime).

---

### Post by psusi on 2007-12-07
setup (hd2) does not work because the boot sector it writes there will try to load grub from hd2, but after you make the switch, it's now on hd0, which causes error 17 when the boot sector can't find grub on hd2.

Also you said that the IDE drive is what you told the bios to boot from first, which appears to be (hd0) or /dev/hda.

---

### Post by Wayno-san on 2007-12-07
Although your reasoning logically makes sense (and I agree with it), I actually get the GRUB Error 17 when the IDE drive is (hd0).  :confused: 
After I change the SATA2 (with Ubuntu on it) to be drive (hd0) GRUB loads up fine.  Don't ask me why because I have absolutely no idea....

---

### Post by psusi on 2007-12-10
The ide drive is always (hd0) when you are setting up grub, because according to your devices.map, (hd0) is /dev/hda.  Changing the boot order in the bios only effects the bios, which grub only uses when first booting the system.  This is why you want to do a setup (hd0) and set the bios to boot from the ide drive.

---

### Post by Wayno-san on 2007-12-10
Does GRUB utilize the information in the fstab file at all?  I'm wondering if I need to have the other drives/partitions listed in there for GRUB to work properly...  During my initial install I set all the non-Linux partitions to "Do Not Use".

---

### Post by psusi on 2007-12-10
No, Grub has no awareness of fstab.

---

### Post by Wayno-san on 2007-12-11
OK, I ended up deleting my Windows 2000 and installing Linux Mint on my only IDE drive.  I also re-installed Vista on the RAID device since somehow it got corrupted and the desktop would not show up after logging in.  

When I installed LInux Mint it didn't set up GRUB properly so I tried to do it manual and as usual I ran into a bunch of problems...  that my big issue was here, and I'm surprised that it's not noted more often in the GRUB info posts, manual, etc, it that [COLOR="Red"][SIZE="4"]the DRIVE ORDER can be different when booting and when I get into Linux and use the GRUB shell!!!![/SIZE][/COLOR]

And this is not due to the map command either.  For instance, when I ran the geometry command in the boot version of GRUB I got one result, and when I ran it from the linux shell I got a DIFFERENT result (no mapping was used).

Also, even though my device.map file appears correct, the drive order that GRUB returns before the boot is different than the drive order that I have set in BIOS.  This confused me further.... After some trial-and-error I finally figured out which disk was which and now I finally have GRUB set up properly where I can boot into LInux, WinXP, or Vista!  YAY!!!!

Anyhow, just wanted to say thanks again to all of you that offered assistance with this.  =D>

---

