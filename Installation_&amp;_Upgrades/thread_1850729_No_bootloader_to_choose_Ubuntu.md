---
title: "No bootloader to choose Ubuntu"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by ThePooba on 2011-09-27
Hi, i recently installed Ubuntu 11.4 on a separate partition of my hard drive so i could dual boot windows 7 and Ubuntu but when the Ubuntu installation is successful and i restart there is no boot loader to choose from windows and Ubuntu, tried live mode in Ubuntu and tried to follow BASIC directions on how to re install grub but no luck, Any help? (I'm absolutely new to linux)

---

### Post by vinterkind on 2011-09-27
Hi,

First thing. You've got a Boot Loader.
In Ubuntu, install the "startup manager" via Software Management. 
With this program you can alter the Boot settings.

ALternatively you can press the left shift key to make the bootloader visible.

cheers,

---

### Post by jordinf on 2011-09-27
I am having the same problem bro and cant find a answer anywhere.

startup manager work get the first time I want to boot into windows but after that there is no why I know of to boot back into ubuntu and left **** does nothing for me so ill keep looking and let you know if I can find something.

---

### Post by Elfy on 2011-09-27
> **ThePooba said:**
> Hi, i recently installed Ubuntu 11.4 on a separate partition of my hard drive so i could dual boot windows 7 and Ubuntu but when the Ubuntu installation is successful and i restart there is no boot loader to choose from windows and Ubuntu, tried live mode in Ubuntu and tried to follow BASIC directions on how to re install grub but no luck, Any help? (I'm absolutely new to linux)

I assume that you can boot - can you open a terminal and run this please

```
sudo fdisk -l
cat /etc/default/grub
```

Paste the outputs here.

---

### Post by temporary88 on 2011-09-27
in file  /etc/default/grub 
comment following lines
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true

and check number of seconds 
GRUB_TIMEOUT=10

---

### Post by vinterkind on 2011-09-27
Additionally it could be, that you're updating Ubuntu and it "corrects" your Bootentries.
So if you've started e.g. "windows" on third place (linux and recovery on first and second place)
and you've update ubuntu you've got a menu like

linux1
recovery1
linux.old
recovery.old
windows

but the third entry is now linux. So you boot up into linux again...
check on your startup manager. I can provide other hints, but that's the easiest.

---

### Post by jordinf on 2011-09-27
```
matthew@matthew-ET1331G:~$ sudo fdisk -l
[sudo] password for matthew: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d450f4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567        1580      102400    7  HPFS/NTFS
/dev/sda3            1580       97524   770668363    7  HPFS/NTFS
/dev/sda4           97524      121602   193405953    f  W95 Ext'd (LBA)
/dev/sda5          112805      121602    70654976    7  HPFS/NTFS
/dev/sda6           97524      112316   118819840   83  Linux
/dev/sda7          112316      112804     3921920   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdg: 8103 MB, 8103395328 bytes
255 heads, 63 sectors/track, 985 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001de1d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         986     7913440+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(984, 254, 63) logical=(985, 46, 21)
matthew@matthew-ET1331G:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
matthew@matthew-ET1331G:~$ ^C
matthew@matthew-ET1331G:~$ 
```When I start Startup Manager linux is the first and Windows 7 is last on the list and windows is sda2 if that helps at all

I can change it on Startup Manager to boot windows and it will work but there is no choice it just boots windows without and I cant go back to ibuntu sense there is no startup manager in windows i dotn think

---

### Post by vinterkind on 2011-09-27
first you should alter as said your /etc/default/grub

[B]#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10[/B]

and if you want to see what's going on ...
[B]GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""[/B]

the generated configuration is in /boot/grub/grub.cfg. 
you could check on your devices UUID. 

the one you've been searching you can get with

```
blkid
```

---

### Post by vinterkind on 2011-09-27
some hints here

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jordinf on 2011-09-27
I get this


/dev/sda1: LABEL="PQSERVICE" UUID="E664486F64484491" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="469849029848F24B" TYPE="ntfs" 
/dev/sda3: LABEL="eMachines" UUID="B0A84A95A84A59CC" TYPE="ntfs" 




mine looks exactly like that i guess im just screwed reinstalling ubuntu  every time i want to use it sadly appreciate your time bro

---

### Post by vinterkind on 2011-09-27
ok.

your /dev/sda6 (linux) is missing.

Does Ubuntu boot ? And do you have a Bootloader visible ?
Where did you install GRUB ?

Some years ago, you could only boot a system if your bootloader is within the range 
of the 1 .. 1024 cylinder of the harddrive. Some older guys still want to install the bootloader
in this first part of the HD. It's an older issue. But since GRUB2 doesn't have those probs 
I guess everything else works fine ?

---

### Post by jordinf on 2011-09-27
Yes it boots but there is no boot loader menu at all ever.

It just boots to linux every time endless I use Startup Manager to boot to windows....But then I cant figure out how to boot ubuntu instead of windows sense it now permanent to default windows every time after.

everything seams to work I guess but I cant go back and forth from windows to ubuntu If i install ubuntu its boots ubuntu every time no menu ever and If i use startup manager to change it to windows then it boots windows every time and i dont know how to change the boot within windows

---

### Post by jordinf on 2011-09-27
Deleted

---

### Post by vinterkind on 2011-09-27
Sorry I couldn't help. 

Maybe next time you could try to press the shift key (must've been the left one)
right after the BIOS POST and first Hardware Initialisation to enter the boot menu.

---

### Post by jordinf on 2011-09-27
```
matthew@matthew-ET1331G:~$ sudo fdisk -l
[sudo] password for matthew: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d450f4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567        1580      102400    7  HPFS/NTFS
/dev/sda3            1580       97524   770668363    7  HPFS/NTFS
/dev/sda4           97524      121602   193405953    f  W95 Ext'd (LBA)
/dev/sda5          112805      121602    70654976    7  HPFS/NTFS
/dev/sda6           97524      112316   118819840   83  Linux
/dev/sda7          112316      112804     3921920   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8103 MB, 8103395328 bytes
255 heads, 63 sectors/track, 985 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001de1d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         986     7913440+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(984, 254, 63) logical=(985, 46, 21)
matthew@matthew-ET1331G:~$ 
```**** does nothing and i dont see anything but a black and flash of the screen before ubuntu loads......all good man you tried thx for your time


Anyone know how to change the boot mark from sda2 to say sda6 so it boots with menu or even sda5 for windows where do i edit this file

---

### Post by vinterkind on 2011-09-27
to change your boot mark go to console and type

```
fdisk /dev/sda
```

then you get an interactive menu where you can change your active boot partition.

m - help
a - activate bootflag.

just press a, and chose your disk.

---

### Post by jordinf on 2011-09-27
I tried it just keep saying...

unable to open /dev/sda
matthew@matthew-ET1331G:~$

---

