---
title: "Error during GRUB boot:: Gave up waiting for root device"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by lun7200 on 2010-11-30
hello,

just installed ubuntu 10.10 on my external usb hdd from my 8gb flash drive

doing this on a laptop, my primary hdd (internal) is running windows (230gb of 250gb used) so i got an external hdd (2tb) and I decided to install ubuntu on it

on that same 2tb external:
1.80GB NTFS partition for various files
17gb extended with
      15gb ex2 partition in which i installed ubuntu 10.10
      2gb linux swap space

after installing from usb flash drive, everything was successful and i received the message that the system was going to rebot. after reboot i selected from my initial boot, to boot to my external hdd (my flash drive was disconnected by this point) and my system gets to the grub screen and I select to run ubuntu and after a few minutes i get an error message:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/a0c70102-b5d8-4b82-a14c-225330e1c4d4 does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _ 
``` 

i ran a quick search for similar problems but nothing seemed to help me

i type exit at the time of error (as a previous thread suggested) but that did not seem to help. I read that editing the grub/menu.lst can solve the problem but 10.10 does not have a menu.lst (so i have read) 

i am running 10.10 currently from my flash drive (as a live user) and at the same time my external hdd is also plugged in and i can access most of the files. my external is called media/f326d7c8-357c-4517-87c5-233ab8556f75 according to linux. i have also edited the grub.gfx file and added the rootdelay=90 line and still doesnt work

is there any fix for this? any help is appreciated, i apologise for my bad english. thank you

extra info

```
**sudo gedit /etc/default/grub **

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

```
 **sudo fdisk -l**

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
126 heads, 3 sectors/track, 1292056 cylinders
Units = cylinders of 378 * 512 = 193536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd03d783

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1     1237366   233862112+   7  HPFS/NTFS

Disk /dev/sdc: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders
Units = cylinders of 3040 * 512 = 1556480 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5140     7812592    b  W95 FAT32

Disk /dev/sdd: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bef84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      240892  1934963966    7  HPFS/NTFS
/dev/sdd2          240893      243201    18547012    5  Extended
/dev/sdd5          240893      242932    16386268+  83  Linux
/dev/sdd6          242933      243201     2160711   82  Linux swap / Solaris

```

---

### Post by Elfy on 2010-11-30
Closed - please do not post duplicate threads.

---

