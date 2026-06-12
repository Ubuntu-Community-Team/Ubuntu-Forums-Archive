---
title: "[SOLVED] GRUB broke after HD added, setup does not fix"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Wayno-san on 2007-11-26
[SIZE="3"]Hi,
I have a box that was set up with Windows2k, Windows XP64, and Ubuntu. Using GRUB I was able to choose which OS I wanted to boot to and everything worked fine. Due to random reboot issues with (and only with) XP64 I purchased a copy of Windows Vista Ultimate 32bit. I didn't want to corrupt my current OSes so I also bought a couple of hard drives and set them up in RAID0 (nForce 4) configuration for the Vista install. I WAS going to disconnect all the other drives before installing Vista to keep it's boot manager's grubby fingers off of the other OSes but once I hooked up the RAID drive my GRUB would no longer boot giving me an Error 22. I tried reinstalling GRUB but no joy. 

Using the supergrub boot disk I was able to boot into Ubuntu a few times with the liveCD but now it just boots me to a "(initramfs)" prompt.  I have no idea what this is or how to fix it.  I tried reinstalling GRUB per a few posts but it did not correct the problem.  Here's the pertinent (I think) info.

Grub install attempt:
```

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,4)
grub> root (hd2,4)
root (hd2,4)
grub> setup (hd
setup (hd
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+17 p (hd2,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> setup (hd
setup (hd
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+17 p (hd2,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

geometry (hd2)
drive 0x82: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sdb
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x7
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type unknown, partition type 0x7
grub>

```

Output from 'fdisk -lu':
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34e434e3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63   111683879    55841908+   b  W95 FAT32
/dev/hdc2       111683880   312576704   100446412+   f  W95 Ext'd (LBA)
/dev/hdc5       111683943   312576704   100446381    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc3bbc3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     4193028   488392064   242099518+   7  HPFS/NTFS
/dev/sda2              63     4192964     2096451   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x383e1ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   488392064   244188000    f  W95 Ext'd (LBA)
/dev/sdb5        10506510   215303129   102398310   83  Linux
/dev/sdb6           16191     6313544     3148677    7  HPFS/NTFS
/dev/sdb7         6313608    10506509     2096451    7  HPFS/NTFS
/dev/sdb8       215303193   488392064   136544436    7  HPFS/NTFS

Partition table entries are not in disk order
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b056ae8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     3148739     1574338+   7  HPFS/NTFS
/dev/sdc2         3148740     6297479     1574370   82  Linux swap / Solaris
/dev/sdc3         6297480    79698464    36700492+   7  HPFS/NTFS
/dev/sdc4        79698465  1250274689   585288112+   f  W95 Ext'd (LBA)

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 1015 MB, 1015021568 bytes
255 heads, 63 sectors/track, 123 cylinders, total 1982464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x001d6da1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63     1982463      991200+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(122, 254, 63) logical=(123, 102, 43)

```

Menu.lst:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        7

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# kopt=root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.20-16-generic
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 7.10, kernel 2.6.20-15-generic
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu 7.10, memtest86+
root        (hd2,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title        Microsoft Windows 2000 Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Professional x64 Edition
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

device.map:
```

(fd0)    /dev/fd0
(hd0)    /dev/hdc
(hd1)    /dev/sda
(hd2)    /dev/sdb
(hd3)    /dev/sdc
(hd4)    /dev/sdd

```

To complicate matters I now have a Vista OS installed on the RAID drive.  I tried adding all the OSes to its boot loader using EasyBCD but I'm only able to get Win2K and Vista working.  Ubuntu doesn't load it the correct drive and partition do not show up in EasyBCD under the add entries option.  WinXP64 also will not load (I think it's trying to use the Win2k bootloader files).

Any suggestions on how to best correct this?  I was up to 5AM last night and spent most of today struggling with this problem.  I'm no Linux GURU and Vista is new to me also.

[/SIZE]

---

### Post by dabl on 2007-11-26
Hmmmm -- that's a pretty good mess you've got going there!  :)

I'm not convinced that the grub output is correct.  It says Linux root is on hd2,4, but that corresponds to sdc5, which doesn't exist, so that dog won't hunt.  Actually, the only possible partition that could be a Linux filesystem is sdb5, which in Grub-speak would be hd1,4, because everything else is NTFS, W95, or swap.

Moreover, are you aware you have 2 swap partitions?  What's the deal with that -- if you only have one Linux system, why would you need 2 swap partitions?

Maybe this will help: [http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Good luck with it!  :)

---

### Post by Wayno-san on 2007-11-26
Thanks for the quick reply... I'm going to check out the link you sent right now... I've been reading so much stuff on the subject my eyes are beginning to water... 

I'm currently only using one swap partition, I created another on the RAID drive because I was going to switch to using that thinking it might increase swap speed a little it being on the faster drive.  I'll worry about that after I get this boot mess sorted out though.... 

I'm also trying EasyBCD and it shows my Ubuntu partition as Drive 2, Partition 0.... this can't be correct either because I have 2 swap partition prior to the Linux partition on that drive...  EasyBCD shows them swapped around (they're Partition 1 and 2).  

2,4 actually looks reasonable to because when I look at the partitions (see image "Drive view from XP64.jpg") it shows the Ubuntu partition on Hard Disk 2.  Assuming the Extended partition is #1, 1st swap is #2, 2nd swap is #3, Linux would be #4.  Am I interpreting this incorrectly?

You're correct, this is quite a mess....

---

### Post by Pumalite on 2007-11-26
[http://ubuntuforums.org/showthread.php?p=3845108#post3845108](http://ubuntuforums.org/showthread.php?p=3845108#post3845108)

---

### Post by Wayno-san on 2007-11-26
Pumalite, 
I'm not trying to install Ubuntu onto the RAID drive... or did your link have to do with my SWAP partition plan?  If so, I guess I can keep the SWAP where it's at.

I just performed another grub setup... I noticed that even when I run the commands root (hd2,4) and then setup (hd2,4), it must somehow overwrite my MBR because when I reboot the computer tries to run GRUB and not the Vista boot loader.  Unfortunately it still fails on Error 22.

---

### Post by meierfra on 2007-11-26
Which  hard drive are you booting from? After

sudo grub
root (hd2,4)
setup (hd2)
quit

you need to boot from your ubuntu drive. This should  get you to  the grub-menu at boot up.  But you will still get an error message  once you select ubuntu.  (This  can be fixed by editing the menu.lst,  We'll worry about that  after you got the grub-menu to appear.)

---

### Post by Wayno-san on 2007-11-27
I'm booting from Disk 0, which is my first and only IDE drive.  It contains Windows 2000 in its 1st partition and the MBR.  I've attached the output of my Vista drive map.

If I disable the 2nd SATA controller (the one with the new Hard drives) GRUB boots up fine with no Error 22.  I can boot into Ubuntu, Windows 2000, and Windows XP64.... but no Vista since that's on the disabled drives.  When I re-enable the SATA controller I get Error 22 again.

Oh, and I actually ran 'setup (hd2,4)', not 'setup (hd2)'.... for some reason the GRUB TAB auto-complete feature doesn't work on my computer.

---

### Post by Wayno-san on 2007-11-27
I was thinking...
Is there a way to completely remove GRUB from Ubuntu, and then reinstall it again having it rebuild the menu.lst and device.map files? I noticed that running GRUB/setup does not do this. Maybe then GRUB would "see" the new drives I installed and adjust the files accordingly....

Let me know what you think...

Thanks!

---

### Post by meierfra on 2007-11-27
Try each of these :

1)  Since your are booting from IDE drive, this should work

```

sudo grub
root (hd2,4)
setup (hd0)
quit

```

If it didn't  work out, change the boot order in the bios  (try all the different settings with the IDE drive first)


2)  > Is there a way to completely remove GRUB from Ubuntu, and then reinstall it again having it rebuild the menu.lst and device.map files? I
Yes:


```

cd /boot/grub
mv cp menu.lst menu.lst.backup
sudo update-grub
sudo grub-install  --recheck  /dev/hdc
```

But I think  it will generate the exact menu.lst which you have right now. So it should be equivalent to 1). 

Again try with different boot orders

3)  
```

gksudo gedit /boot/grub/menu.lst
```

In menu.lst change "#groot (hd2,4)" to "#groot (hd0,4)". Save the file.

Then

```

sudo update-grub
sudo grub
root (hd2,4)
setup (hd2)
quit

```
and then boot  from  your ubuntu drive. 

If none of this works,  report any changes and/or error messages. Also let us know the exact boot order in the bios.

---

### Post by Wayno-san on 2007-11-27
OK, I'll give that a try and report back.  Right now my boot order in BIOS is:
1. IDE
2. SATA1
3. SATA2
4. SCSI (RAID0 drive)... not really a SCSI

THANKS!

---

### Post by Wayno-san on 2007-11-28
OK, tried all of this and here is what I have:

1.  All boot orders resulted in:
```

Grub Loading Stage 1.5
Grub Loading, please wait...
Error 22

```

2.  You're correct, same results as for #1.  The only thing was that when it regenerated the new menu.lst file, it didn't include my Windows XP or Windows 2000 options.

3.  With my boot order in BIOS set to:

```

SATA2
Ch 1
SATA1
SCSI-0

```

I was able to boot into Ubuntu w/o the dreaded "Error 22".  I was certain this error was being caused by the addition of SCSI-0 (The RAID0 drives) but this proves my hypothesis incorrect.

Unfortunately with my boot order set like this my Windows 2000 and Windows XP options in GRUB no longer work.  I haven't tried adjusting those partitions in menu.lst yet but I have a feeling that Windows will not like being anything but the (apparent) 1st drive on the system.

---

### Post by meierfra on 2007-11-28
Try this:

At the grub menu during-boot up press "c"  (You might  have to press "Esc" during the count down to get to the grub-menu) 

Type 

geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (hd3)
geometry (hd4)
geometry (hd5)

Look at the output and try to decide which drives contains contains your windows systems  Say you  expect one of your systems to be on (hdx)  where x  is a number form  0 to 5. Then type


root (hdx,0)
map        (hd0) (hdx)
map        (hdx) (hd0)
chainloader +1
boot


Of course x needs to be replaced by its actually value. So for example if you expect windows to be on (hd3),  type

root (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
boot

If this boot you into windows,  add the same commands to menu.lst (but add a title and remove the "boot")
If it didn't work you should be able to reboot by pressing "Ctr Alt Del". Then  just repeat with a different value for x. Try them all.

---

### Post by Wayno-san on 2007-11-28
meierfra, 
IT WORKS!!!  My boot order in BIOS is kind of screwed up.  I tried to adjust it to something more "normal" but then I keep getting that GRUB Error 22.   I think I would need to adjust my device.map file?  Also, in my device.map file I'm not sure why hd0=/dev/hdc... shouldn't it be hda?  For Vista and Win2k I boot into the Vista loader and then select one of the two operation systems.  Here's what I ended up with...   

Boot order in BIOS:
```

SATA2
IDE2
SATA1
SCSI (RAID0)

```

device.map:
```

(fd0)	/dev/fd0
(hd0)	/dev/hdc
(hd1)	/dev/sda
(hd2)	/dev/sdb
(hd3)	/dev/sdc
(hd4)	/dev/sdd

```

menu.lst:
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e8179619-6399-4dbc-ab0a-1db833e9deae ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Vista or Windows 2000 Pro
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64 Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Thank you VERY MUCH for your help!  The geometry command was the missing link for me...

---

### Post by meierfra on 2007-11-28
Great! 

No need to edit "device.map" It is never used unless you specifically asked grub to use it.

> hd0=/dev/hdc... shouldn't it be hda? 

device.map basically uses the data from fdisk.  And fdisk has it as hdc and not hda. But I don't know why fdsik uses hdc.  Sometimes it happens because  some cables are plugged in wrongly.  But  since your systems is working right now, I wouldn't mess with the cables.

---

### Post by Wayno-san on 2007-11-29
I was just thinking.. it's likely that it's "hdc" because that drive is actually the master on the second IDE controller on the mother board.  In that case the Master on IDE1 would be "hda", IDE1 slave would be "hdb", and Master on IDE2 would be "hdc"... and so on....

---

