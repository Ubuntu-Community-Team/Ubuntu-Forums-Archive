---
title: "moved hard disks, xp won't load"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by epidemiks on 2008-05-23
Hi,

I've been swapping around hard disks to try to figure out a problem booting into the 24-17 kernel, and given up. But now My XP won't boot.. brings a few different errors or just hangs on a black screen.
Probably very simple, but I can't find another thread with troubleshooting I haven't tried..

Here's fdisk -l:
> Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd214d214

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9963    59544922+   f  W95 Ext'd (LBA)
/dev/hda5            2551        9963    59544891    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe75be75

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hdb2            6375       30400   192988845    f  W95 Ext'd (LBA)
/dev/hdb5            6375       30400   192988813+   7  HPFS/NTFS

Disk /dev/hdc: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c1047c2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1182     9494383+  83  Linux
/dev/hdc2            1183        1240      465885    5  Extended
/dev/hdc5            1183        1240      465853+  82  Linux swap / Solaris



here's my menu.lst:

> 

title		Ubuntu 8.04, kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=a1969d86-3b3e-45f5-b232-c72e73b23fdc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=a1969d86-3b3e-45f5-b232-c72e73b23fdc ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

So note windows is on (hd0,0) and so is the 22-14 kernel which actually boots, but they are separate drives.
I've tried all combinations.. (hd0,1),(hd1,0),(hd1,1) etc..
Still I either get a grub error "no partition" or similar, or I get a black screen that hangs till i reboot.
I'm need to get back to XP to edit some photos (ubuntu gfx are not being nice)..

Thanks!

---

### Post by PmDematagoda on 2008-05-23
Could you please specify the location where the XP drive/partition is located(as seen by Linux).

---

### Post by epidemiks on 2008-05-23
XP is on /dev/hda1 .. is that what you mean?

---

### Post by PmDematagoda on 2008-05-23
With (hd0,0), what error do you get?

---

### Post by Kevbert on 2008-05-23
Your problem may be with the /etc/fstab file in that the UUID disk labels no longer match up.  If you enter:
```
ls /dev/disk/by-uuid -lah
```
in terminal, check whether these match up with the entries in fstab.  Edit them if necessary.  Your (posted) menu.lst file looks OK.

---

### Post by lswest on 2008-05-23
since grub sees the linux partition as hd0, you may need to try hd1 or hd2 to boot into XP (when you get to the grub menu, hit "e" to edit the entry, and e again after you find the right line, then edit it, hit enter and "b" to boot (it's a temporary change).  Do this to find out what hdX value works for XP, then edit it permanently in your menu.lst file.

try:
root (hd1,0)
and
root (hd2,0)

---

### Post by epidemiks on 2008-05-23
cheers guys
I can't remember the exact errors with the different 1,0 2,0 attempts - (i've tried up to 4,0).. i'll check now.. meantime, here's fstab:

> proc /proc proc defaults 0 0
# Entry for /dev/hdc1 :
UUID=a1969d86-3b3e-45f5-b232-c72e73b23fdc / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdc5 :
UUID=347402e9-034f-4fac-b9d9-9fe0f0231f91 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/hdd5 /media/Stuff\040Drive ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/hdd1 /media/Swap\040Drive ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/hda5 /media/Audio\040Data ntfs-3g defaults,locale=en_AU.UTF-8 0 0
**/dev/hda1 /media/Audio\040Drive ntfs-3g defaults,locale=en_AU.UTF-8 0 0**

---

### Post by epidemiks on 2008-05-23
Okay, boot errors:

hd(0,0): Error 13: Invalid or unsupported executable format
hd(1,0): Starting Up..  (hangs 10 mins +, reboot req'd)
hd(1,1): Error 12: Invalid device requested
hd(2,0): Starting Up..  (hangs 10 mins +, reboot req'd)
hd(2,1): Error 12: Invalid device requested
hd(2,0): Error 18: Selected cylinder exceeds BIOS max
hd(3,0): Error 21: Seleced disk does not exist
hd(4,0): Error 21: Seleced disk does not exist

All disks are IDE, all are auto detected by BIOS, tried manual too..

---

### Post by dstew on 2008-05-23
I understand you get the grub menu, and you can boot Ubuntu, but not XP. Is that correct? Can you boot XP using a Windows recovery console from the Windows CD? Maybe the problem is with the Windows boot loader. When grub gives you the Starting up... message, that means it is done, and has handed control of the computer over to whatever got loaded.

---

### Post by Pumalite on 2008-05-23
See if you can boot XP with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by epidemiks on 2008-05-23
dstew, I don't have an XP recovery cd/any legit cd.. and yes, I was beginning to consider XP's boot loader may be the cause.

pumalite, I will give it a shot. Gonna see if I can boot straight into XP without linux drive plugged in first.

Thanks guys

I really wish I hadn't upgraded to 8.04. Gutsy was working so well.... :(

---

### Post by Kevbert on 2008-05-23
I've notice on your menu.lst that Ubuntu 8.04 memtest86+ is on hd(1,0).  If Ubuntu works OK this should be hd(0,0).  What make it worse is fstab and fdisk -l suggest you're using hdc for Ubuntu (which should be hd(2,0))...
Probably the best thing to do is to use a Super Grub disk to get Windows working and then re-install Ubuntu.

---

### Post by epidemiks on 2008-05-23
memtest is on 1,0 because i've been sloppy in copy/pasting my menu.lst..
there's more (24.17) kernels from the upgrade that won't boot that i didn't include here.
I'd wipe ubuntu in a heartbeat, get xp up and running again then reinstall ubuntu, but the live cd dies on me.. (ata errors, exactly like the 24.17 kernels)

---

