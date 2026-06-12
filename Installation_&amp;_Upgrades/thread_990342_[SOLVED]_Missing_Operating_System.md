---
title: "[SOLVED] Missing Operating System"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by whoeva on 2008-11-22
Hi,

I installed 8.10 64-bit using the alternate cd onto my third HD which is an ide (My 1st 2 HD's are in a raid setup with windows XP installed onto.) Everything went smooth with the install, it detected XP there so I installed grub to the master boot record but when it restarted there is no menu, just straight to windows.

I tried specifying just the ide drive in the boot priority but it just says missing operating system.

I also tried booting into the live cd so I could do the find /grub/stage1 command but I'm guessing since it is on the raid the live cd version can't see it. It just returns the error.

Can anyone help me? I'd really love to get back to using ubuntu for everything and just windows for my games again.

---

### Post by caljohnsmith on 2008-11-22
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by whoeva on 2008-11-22
> **caljohnsmith said:**
> How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```

```
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x59cd of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb31eb31e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40965750  1951431614   955232932+   f  W95 Ext'd (LBA)
/dev/sda5   ?  1169894176  5159863201  1994984513   5a  Unknown

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcca3c085

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05189c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *   719969040   739504079     9767520   83  Linux
/dev/sdc2           16065   719969039   359976487+   f  W95 Ext'd (LBA)
/dev/sdc3       739504080   777594194    19045057+  83  Linux
/dev/sdc4       777594195   781417664     1911735   82  Linux swap / Solaris
/dev/sdc5           16128   512023679   256003776    7  HPFS/NTFS
/dev/sdc6       512023743   719969039   103972648+   7  HPFS/NTFS
```

Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```

```

sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
(returns nothing)
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
```



So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

No commands returned grub so I didn't try this last command, unless I'm doing something wrong? I tried sda1, sda2 etc but these also returned nothing.

---

### Post by caljohnsmith on 2008-11-22
Can you change your BIOS to boot your sdc drive instead of your RAID array? If you can do that, you can install Grub to its MBR (Master Boot Record) and make it bootable. From your Live CD, how about doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, and it should be either (hd2,0) or (hd2,2); use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hd2)
grub> quit

```
Please post the output of all the above commands, reboot, set your BIOS to boot the sdc drive, and you should get the Grub menu on start up if all goes well. If you have trouble booting Ubuntu from the Grub menu, let me know. Otherwise let me know how it goes.

---

### Post by whoeva on 2008-11-22
> **caljohnsmith said:**
> Can you change your BIOS to boot your sdc drive instead of your RAID array? If you can do that, you can install Grub to its MBR (Master Boot Record) and make it bootable. From your Live CD, how about doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, and it should be either (hd2,0) or (hd2,2); use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hd2)
grub> quit

```
Please post the output of all the above commands, reboot, set your BIOS to boot the sdc drive, and you should get the Grub menu on start up if all goes well. If you have trouble booting Ubuntu from the Grub menu, let me know. Otherwise let me know how it goes.

Thank you for your helping me. I did the commands but previewed my reply instead of posting so if you need any more info please ask. Anyway, the root was (hd2,0) so I ran the setup and switched the drive and it booted straght in so we're all into ubuntu. Now just need to get it to dual boot if you can help with that?

---

### Post by caljohnsmith on 2008-11-22
Glad to hear you are in Ubuntu; to add Windows to your Grub menu, first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following at the end:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Most likely the first entry will work, but the second one because it is unclear how your RAID array will appear to Grub on start up. Give that a shot and let me know how it goes, or if neither entry works, let me know exactly what happens when you try each of them from the Grub menu.

---

### Post by whoeva on 2008-11-22
Thank you, will try now...

Edit: Thanks, 1st entry works perfectly. Just need to find my raid in ubuntu somewhere and we're sorted.

---

