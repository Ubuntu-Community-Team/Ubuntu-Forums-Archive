---
title: "[SOLVED] Problems dual booting with Ubuntu and windows xp using two separate hard dri"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by Iceman99one on 2008-08-19
I am new to linux and I had two IDE hard drives one running win xp home (40Gb seagate) and the other a blank drive(40Gb Western Digital). I wanted to run a dual boot configuration with win xp and ubuntu on separate drives. After reading many tutorials and asking a few questions I decided to set up the blank drive as master to install ubuntu on and the win drive as the slave when I ran the Install CD and went through the installation process. This seemed to be the easiest way to go about this dual boot.

During the installation everything seemed to be going well, i made sure to installl ubuntu onto the blank drive. If i remember correctly the blank drive appeared as hda0 and the win drive appeared as hdb0. After restarting my machine the grub boot menu appeared seemingly correct showing the option to boot into either Ubuntu or windows.

I can boot fine into Ubuntu but when I try to boot into windows I get this error message:

Error 21: Selected disk does not exist

Press any key to continue...

Any help is much appreciated...

Thanks a lot!

---

### Post by lackoblacko on 2008-08-19
check your grub menu.lst to see if the right hard drive is selected for windows.

---

### Post by Iceman99one on 2008-08-19
Here is what the end portion of menu.lst file looks like:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

I'm not sure if it is correct or not. I am relatively new, and I am not entirely sure of the exact fuctions of all the code.

Thanks for your help!

---

### Post by caljohnsmith on 2008-08-19
Your Windows entry in the menu.lst appears correct if you are truly booting off your Ubuntu HDD, and didn't accidentally have Grub installed to the MBR of your Windows HDD. To help troubleshoot, please post the output of:
```
sudo fdisk -lu
sudo grub
  grub> geometry (hd0)
  grub> geometry (hd1)
  grub> quit
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
```
Also, in your menu.lst, does the Ubuntu entry use (hd0,0)?

---

### Post by Iceman99one on 2008-08-19
Ok--
Here is the output of the commands you gave me:

For fdisk -lu:
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78140159    39070048+   7  HPFS/NTFS

```

For sudo grub:
   
```

grub> geometry (hd0)
drive 0x80: C/H/S = 4865/255/63, The number of sectors = 78165360, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

```

```

grub> geometry (hd1)
drive 0x81: C/H/S = 4865/255/63, The number of sectors = 78165360, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7

```

For sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump:
 
```

2+0 records in
2+0 records out
2 bytes (2 B) copied, 0.0276005 s, 0.1 kB/s
0000000 ff00                                   
0000002

```

And for sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump:

```

2+0 records in
2+0 records out
2 bytes (2 B) copied, 0.022292 s, 0.1 kB/s
0000000 0000                                   
0000002

```

Yes, the Ubuntu entry uses (hd0,0)
```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=f2a23c91-e393-4095-8f3
3-d9e3f5c61e8c ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=f2a23c91-e393-4095-8f33-d9e3f5c61e8c ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

```

Thanks for your help!

---

### Post by caljohnsmith on 2008-08-19
Iceman99one, those commands show that everything appears to be in order. Can you change the boot order of your HDDs in BIOS, or by hitting F12 or F8 on startup, so you can boot your Windows HDD directly? I'm asking because we need to confirm it is still bootable, since everything else seems to be OK in order for Grub to boot it.

Also, try adding this as an additional entry at the bottom of your menu.lst:
```
title    2nd Hard Disk Drive
root     (hd1)
chainloader    +1
```
And see if that will boot the Windows HDD.

---

### Post by Pumalite on 2008-08-19
Read this thread:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=confused57](http://ubuntuforums.org/showthread.php?t=179902&highlight=confused57)

---

### Post by Iceman99one on 2008-08-19
Ok--

Right a start up I can get two menus...

one is the boot device menu and looks like this:

_Boot device menu_

1. Normal
2. Diskette Drive
3. Hard-Disk Drive C:
4. IDE CD-Rom Device

Enter a choice _

I can't get anywhere but to ubuntu from there

and the other is the installation menu and part of it looks like this:

Primary Drive 0............Hard Drive
Primary Drive 1............Off
Secondary Drive 0..........CD-Rom Reader
Secondary Drive 1..........Off

The addition that I made to the menu.lst file added another option on the grub boot menu which gives me the same error message:

```

Error 21: Selected disk does not exist

Press any key to continue...

```

Thanks for your help!

---

### Post by Iceman99one on 2008-08-19
Ok guys I fixed it. All is well!!!

I was reading through the how to thread that Pumalite recomended and I read the part about the dell machine with the Primary Drive 1 controller turned off by default. I went hmmm.... that sounds familiar. So I rebooted and went into my intstalation menu and sure enough my controler was off to. So I turned the controler to auto and sure enough when I tried to boot into windows... tadaa it worked!!!

Thanks to all for your help... it is much appreciated!

Cheers!!!

---

### Post by caljohnsmith on 2008-08-19
Before you installed Ubuntu, did you originally have the Windows HDD set as master and were able to boot it OK? 

Also, in your /boot/grub/device.map file, does it have the following lines:
```

(hd0)	/dev/sda
(hd1)   /dev/sdb
```

---

### Post by Iceman99one on 2008-08-19
Yes it was set as master and I was able to boot into it.
But now that I turned the secondary IDE channel on it works fine!

And yes it has those lines...

---

### Post by caljohnsmith on 2008-08-19
> **Iceman99one said:**
> But now that I turned the secondary IDE channel on it works fine!

What do you mean exactly? Are you able to boot Windows from Grub now?

---

### Post by Iceman99one on 2008-08-20
Ok--

By reading that thread I figured out that my dell computer has a utility wired in somewhere that controls the IDE channels for all the ports on your motherboard. And to get your computer to work with two hard drives you need to enter this utility at startup and turn the secondary channel on to be able to boot from the drive in question.

So I went in and turned it on and now I am successfully booting (through grub) into ubuntu and windows!

---

### Post by Pumalite on 2008-08-20
> **Iceman99one said:**
> Ok guys I fixed it. All is well!!!

I was reading through the how to thread that Pumalite recomended and I read the part about the dell machine with the Primary Drive 1 controller turned off by default. I went hmmm.... that sounds familiar. So I rebooted and went into my intstalation menu and sure enough my controler was off to. So I turned the controler to auto and sure enough when I tried to boot into windows... tadaa it worked!!!

Thanks to all for your help... it is much appreciated!

Cheers!!!

Glad you got it working! Good luck.

---

