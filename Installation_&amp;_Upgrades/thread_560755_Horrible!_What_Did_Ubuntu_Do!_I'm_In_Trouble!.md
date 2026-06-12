---
title: "Horrible! What Did Ubuntu Do?! I'm In Trouble!"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by Whohlme on 2007-09-26
Help!

I was setting up a dual XP/Ubuntu machine for my brother, whom I had conviced to want a Dual-boot system. I set up the installer and used the Guided partition editor and the setting said something like "resize IDE slave partition #2. I adjusted the graphical slider to 20 GB and otherwise followed the installer normally.

However, when I rebooted, I found that Windows XP was not a boot option! That is horrible because my brother had some data that he didn't back up even though I told him to! 

I think I have an idea of what happened. There are 2 Hard drives on the computer, one 160 GB and one 40 GB. I think Ubuntu installed on the 40GB one (slave) and somehow set itself up to boot at startup. Another thing I forgot to mention was that at startup, it says Booting from CD, which I have never seen before. 

This mishap has made me feel very bad because I have set up 2 dual boot systems in this very simple manner already, and this failure distresses and alarms me. I tried disconnecting power from the slave drive, which gave the boot error of "error loading OS", so I know it's the slave it's booting from. How do I rearrange the real master drive back to master so I can boot from it? 

Also, as a last resort is there a way to remove Ubuntu and return to normal? I don't think so, but just in case...

Thanks alot for all you help in advance.

---

### Post by R.Bucky on 2007-09-26
I am not savvy to installing an OS per hard drive, however I do know that installation of the MS operating system needs to occur first. So, install MS then partition the remaining space for Linux.

---

### Post by Pumalite on 2007-09-26
Connect both hard drives. Let's see your system. Get a Knoppix:[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Boot from it (it will mount all your drives/partitions automatically). See if you can find your Windows files and report back

---

### Post by Whohlme on 2007-09-26
Will any other live CD do? I have Xubuntu, Ubuntu, DSL, Puppy and Zenwalk LiveCD's.

---

### Post by Buffalo Soldier on 2007-09-26
I don't think you need to reformat or do anything that drastic. What's the ouput for:
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

---

### Post by Pumalite on 2007-09-26
The beauty of Knoppix is that it mounts all your drives/partitions automatically, so you have immediate access to all your files without any great technical knowledge.
(BTW, I mentioned Knoppix because your post left me under the impression that you did not have access to Ubuntu)

---

### Post by nonewmsgs on 2007-09-26
i would guess you have a sata and a pata and ubuntu put grub on the wrong drive.  everything is most likely fine.

---

### Post by Whohlme on 2007-09-26
So if everything is fine, how do I get back my XP hard drive?

---

### Post by ljonesj on 2007-09-26
one thing to do is put in the windows reinstallation cd if you have a full install disk. then but into the disk wait for it tell to install a fresh copy or repair windows go with repair windows then it will ask you which part usually 1. press that and it asks for a password with home just press enter with pro put in your admin password that was put in in the intial install. after that type fixmbr it will ask if you want and it could destroy the info type yes. then exit and reboot it should be fine if not try again i had to do it twice to get it to work right

---

### Post by Pumalite on 2007-09-26
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by Wim Sturkenboom on 2007-09-27
> **Whohlme said:**
> So if everything is fine, how do I get back my XP hard drive?By supplying the requested info :(

---

### Post by Whohlme on 2007-09-27
Just to remind you, as for all this output, you asked for it!

Okay, to report back finally:

I loaded a Puppy ISO and mounted the drives it recognized. Apparently it didn't recognize the bigger 160GB drive, but it did recognize the Windows partition on the drive that ubuntu is also on.

Here is the output that Puppy gave me:

# cat /etc/fstab
none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0
# sudo fdisk -1
sudo: can't stat /etc/sudoers: No such file or directory


Then I booted into Ubuntu, and this is output it gave me:

zimbo@zimbo-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=017aa2b9-3947-4d90-9ed5-f393665c8e63 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=3d3990bc-f499-4185-a48f-5c54460f640b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
zimbo@zimbo-desktop:~$ sudo fdisk -1
Password:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
zimbo@zimbo-desktop:~$ sudo fdisk -lu

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           9    16434494     8217243   54  OnTrackDM6

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63     8693999     4346968+   7  HPFS/NTFS
/dev/hdb2         8694000    50848559    21077280    7  HPFS/NTFS
/dev/hdb3   *    50848560    76915439    13033440   83  Linux
/dev/hdb4        76915440    78155279      619920    5  Extended
/dev/hdb5        76915503    78155279      619888+  82  Linux swap / Solaris

Disk /dev/sda: 129 MB, 129499136 bytes
4 heads, 62 sectors/track, 1019 cylinders, total 252928 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          62      252711      126325    b  W95 FAT32
zimbo@zimbo-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=017aa2b9-3947-4d90-9ed5-f393665c8e63 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=017aa2b9-3947-4d90-9ed5-f393665c8e63 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=017aa2b9-3947-4d90-9ed5-f393665c8e63 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
zimbo@zimbo-desktop:~$ 

As a final note, I think the 160GB hard drive is really 130GB, and of course it is not empty, so if that helps. I think I got told the wrong number...

---

### Post by Buffalo Soldier on 2007-09-27
> zimbo@zimbo-desktop:~$ sudo fdisk -1
Password:
fdisk: invalid option -- 1

it should be:
```
sudo fdisk -l
```

small letter version of "L". NOT the the number 1 (one).

And you could wrap the output in the CODE tag so that it's easier to read. Example:

```
vega@stars:~$ sudo fdisk -l
[sudo] password for vega:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        1341     1004062+  82  Linux swap / Solaris
/dev/sda3            1342       14593   106446690   83  Linux
```

---

### Post by Pumalite on 2007-09-27
Well your Ubuntu id doing fine in sdb3 and shows up fine in your menu.lst
We have to create an entry for Windows in menu.lst, but I would like some clarifications first:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 9 16434494 8217243 54 OnTrackDM6

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 63 8693999 4346968+ 7 HPFS/NTFS
/dev/hdb2 8694000 50848559 21077280 7 HPFS/NTFS
/dev/hdb3 * 50848560 76915439 13033440 83 Linux
/dev/hdb4 76915440 78155279 619920 5 Extended
/dev/hdb5 76915503 78155279 619888+ 82 Linux swap / Solaris

Disk /dev/sda: 129 MB, 129499136 bytes
4 heads, 62 sectors/track, 1019 cylinders, total 252928 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 62 252711 126325 b W95 FAT32

Whereis XP? hdb1 or hdb2? You have too many boot flags  I'm about to bet that Grub installed himself in sda1. But you have something in hda1 that intrigues me. It has a bootflag and as format has OnTrackDM6. What is that?

---

### Post by Whohlme on 2007-09-27
Xp is on the biggest hard drive ( I guess that would be the 160GB). 

I have no idea what the bootflag or whatever is that you're talking about.

Maybe this is my fault for installing Linux on a computer that wasn't mine expecting it to be easy.

---

### Post by Pumalite on 2007-09-27
It seems that your 129 GB hard drive is SATA. Is that true?

---

### Post by Whohlme on 2007-09-27
This is what I got when I ran the command with the right character 'l' as opposed to 1.

[HTML] zimbo@zimbo-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1023     8217243   54  OnTrackDM6

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         575     4346968+   7  HPFS/NTFS
/dev/hdb2             576        3363    21077280    7  HPFS/NTFS
/dev/hdb3   *        3364        5087    13033440   83  Linux
/dev/hdb4            5088        5169      619920    5  Extended
/dev/hdb5            5088        5169      619888+  82  Linux swap / Solaris

Disk /dev/sda: 129 MB, 129499136 bytes
4 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 248 * 512 = 126976 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1019      126325    b  W95 FAT32
zimbo@zimbo-desktop:~$  [/HTML]

I hope the tags work, I'm quite a noob at some things...

---

### Post by Pumalite on 2007-09-27
I think that Windows is in sdb1 or sdb2, but will put to the test your assertion in post # 15 that Windows is in hda1.
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then:
gksudo gedit /boot/grub/menu.lst
Add the following at the end (after Ubuntu's memtest entry)

title Windows 
rootnoverify (hd0,0)
makeactive
chainloader +1

Save, exit and reboot

---

### Post by Whohlme on 2007-09-27
EXCELLENT! That worked great, although I must press the escape key to get to the GRUB menu. Nonetheless, Thanks so much! Ubunut's not a monster anymore!

---

### Post by Pumalite on 2007-09-27
You are welcome. Good luck.

---

### Post by Buffalo Soldier on 2007-09-27
> **Whohlme said:**
> EXCELLENT! That worked great, although I must press the escape key to get to the GRUB menu. Nonetheless, Thanks so much! Ubunut's not a monster anymore!

To fix that you need to edit your **/boot/grub/menu.lst** file.

From this:
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

To this:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**[COLOR="Red"]#[/COLOR]** hiddenmenu
```

---

### Post by Whohlme on 2007-09-29
I did 

sudo gedit /boot/grub/menu.lst 

and changed what you said 

and then Windows disappeared from the list!

I changed it back and am going to reboot now I'll be back with a report...

---

### Post by Pumalite on 2007-09-29
Ok.

---

### Post by Whohlme on 2007-09-29
Okay, I had to go back and re edit the boot/grub/menu.lst file and add Windows again. After saving, it seems to be working consistently now. Thanks again, your responses were super speedy! :)

---

### Post by Pumalite on 2007-09-29
You are welcome. Good luck.

---

