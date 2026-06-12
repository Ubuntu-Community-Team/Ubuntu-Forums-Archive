---
title: "grub not booting windows XP"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by mabuti on 2005-08-19
Hello, I have just installed Ubuntu 4.10 on my computer which had windows XP on it before. However when I select to boot Windows XP from the boot loader, it doesn't boot. What is the problem?
Here is menu.lst file:
title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

And :

root@ubuntu:/boot/grub # fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *       34541      158815    62634600    7  HPFS/NTFS
/dev/hda2               1       33546    16907152+  83  Linux
/dev/hda3           33547       34540      500976    f  W95 Ext'd (LBA)
/dev/hda5           33547       34540      500944+  82  Linux swap

Partition table entries are not in disk order
please help

---

### Post by izmaelis on 2005-08-19
Is there any error message when your computer is booting to non Linux operating system from GRUB?

---

### Post by mabuti on 2005-08-19
Here is the error message:
root (hd0, 0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

Thanks

---

### Post by izmaelis on 2005-08-19
Try removing or comenting **makeactive** line in Windows boot up configuration part in menu.lst file.

---

### Post by mabuti on 2005-08-19
Well, I have just removed the makeactive line, but no changes. Same error message.

---

### Post by izmaelis on 2005-08-19
Ok. Restore that **makeactive** line that you just edited. And replace your **root (hd0, 0)** with **rootnoverify (hd0, 0)**. If that wont help we'll think something else.  :???:

---

### Post by mabuti on 2005-08-19
Still no progress. This was displayed:

rootnoveriify (hd0, 0)
savedefault
makeactive
chainloader +1

---

### Post by crispingatiesa on 2005-08-19
It happen to me after a reinstallation, try to reinstall GRUB.


sudo grub-install /dev/hda

---

### Post by izmaelis on 2005-08-19
[QUOTE=mabuti]
rootnoveriify (hd0, 0)
[/QUOTE]
What's that? (-: It should be **rootnoverify (hd0, 0)**. (no double "i")

---

### Post by mabuti on 2005-08-20
[QUOTE=izmaelis]What's that? (-: It should be **rootnoverify (hd0, 0)**. (no double "i")[/QUOTE]

Typing  error on the forum and not the menu.lst file
Still not booting XP after re-installing grub:

mabuti@ubuntu:~ $ sudo grub-install /dev/hda
Password:
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda
mabuti@ubuntu:~ $


 ](*,)

---

### Post by Jaristr on 2005-08-20
I have the same problem. I thought it might be because I resize'd the windows partition. 
Did you resize too?

The windows partition can be mounted and accessed alright but it just doesn't boot.

---

### Post by mabuti on 2005-08-20
No, I didn't resized it.  When I first installed Utuntu 4.10 four months ago, everything was well. I could boot XP.  
The trouble started last week when I decided to switch to Hoary 5.04. I could not install  it, it complained that my installer CD could be corruted. I burned my downloaded Ubuntu on another CD , but got the same error message durring installation. I then googled around the net and came to reliase that some people also have the same problem, even with shiped CDs I heard. 
So was left with no option but to re-install  Warty 4.10 and thats when I came encounter Grub problems. 
Maybe formating the whole harddisk and install (XP & Ubuntu) would work.

---

### Post by jorann on 2005-09-05
I had the same problem, this is what i made of grub's menu.lst (and it works for me) :

title Microsoft windows XP Professional
rootnoverify (hd0,0)
chainloader +1


that's it :)

---

### Post by drtvasudevan on 2005-09-07
same problem here.
did anyone find out what goes wrong?
did anyone face the same problem with lilo?

i had to go all the way to fdisk and reformat everything.
could not get past a:\prompt in DOS

TV

---

### Post by Swerver on 2005-09-21
What seems to be the problem is that Windows in not on HDD0 and is NTFS
I have the same problem and have tried everything,

i have heard of it working if windows is installed with FAT and on another drive say HDD1, then it can work

if someone knows a way around this
being:
NT is not on HDD0 and uses NTFS please let us know!

---

### Post by Xiata on 2005-09-21
Sum a few things up...

[QUOTE=Jaristr]I have the same problem. I thought it might be because I resize'd the windows partition. 
Did you resize too?

The windows partition can be mounted and accessed alright but it just doesn't boot.[/QUOTE]
Check your boot sector.
If the output of "dd if=/dev/hda2 bs=512 count=1", where /dev/hda2 is your windows partition, does NOT have:```
NTFS
A disk read error occurred
NTLDR is missing
NTLDR is compressed
Press Ctrl+Alt+Del to restart
```
your boot sector is either corrupt or missing. Get your windows CD, go into recovery console, FIXMBR, FIXBOOT, BOOTSCAN /rescan. Then reinstall grub using your Ubuntu cd. (Get instructions for this first, I won't go into details).

[quote=maibuti]
No, I didn't resized it. When I first installed Utuntu 4.10 four months ago, everything was well. I could boot XP.
The trouble started last week when I decided to switch to Hoary 5.04. I could not install it, it complained that my installer CD could be corruted. I burned my downloaded Ubuntu on another CD , but got the same error message durring installation. I then googled around the net and came to reliase that some people also have the same problem, even with shiped CDs I heard.
So was left with no option but to re-install Warty 4.10 and thats when I came encounter Grub problems.
Maybe formating the whole harddisk and install (XP & Ubuntu) would work.[/quote]
There is a reason that there are **MD5sums**s to file located on the mirrors. They are to check if the file you have has become corrupted. Next time before burning, VERIFY that the file is not corrupt. [http://us.releases.ubuntu.com/releases/5.04/MD5SUMS](http://us.releases.ubuntu.com/releases/5.04/MD5SUMS) has the md5sums. It was listed on the bottom of [http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/)

[quote=Swerver]What seems to be the problem is that Windows in not on HDD0 and is NTFS
I have the same problem and have tried everything,

i have heard of it working if windows is installed with FAT and on another drive say HDD1, then it can work

if someone knows a way around this
being:
NT is not on HDD0 and uses NTFS please let us know![/quote]
Swapping HDD1 to HDD0 (since windows doesn't like to boot off a second hard drive)
```

title Windows XP (IDE: Primary Slave, partition 1)
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
chainloader +1

```
rootnoverify (hd0,0) may have to be rootnoverify (hd1,0). You may have to use the hide/unhide commands with grub depending on whether or not you placed your linux partitions in front of your windows system partition.

---

