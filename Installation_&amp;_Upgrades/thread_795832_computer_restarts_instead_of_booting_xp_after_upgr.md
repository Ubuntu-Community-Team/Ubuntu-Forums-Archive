---
title: "computer restarts instead of booting xp after upgrade"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Homeschool Hacker on 2008-05-15
(edit: I unintentionally added the icon to the forum post -- I'm not upset with Ubuntu!)

I upgraded to Hardy Haron via the alternate CD.  Since then, my computer restarts whenever I try to boot into XP from grub.

Just for kicks, I changed the XP grub option to:

title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
chainloader	+1

with the same result.

Any help would be appreciated.


Below are the outputs of fdisk -l and menu.lst:


$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ff238c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         261     2096451    7  HPFS/NTFS
/dev/sda2             262       60800   486279517+   f  W95 Ext'd (LBA)
/dev/sda5             262        4177    31455238+  83  Linux
/dev/sda6            4178        4438     2096451   82  Linux swap / Solaris
/dev/sda7            4439        6396    15727603+   e  W95 FAT16 (LBA)
/dev/sda8            6397       10312    31455238+   7  HPFS/NTFS
/dev/sda9           10313       12923    20972826    b  W95 FAT32
/dev/sda10          12924       32504   157284351    c  W95 FAT32 (LBA)
/dev/sda11          32505       45558   104856223+   7  HPFS/NTFS
/dev/sda12          45559       49475    31463271    7  HPFS/NTFS
/dev/sda13          49476       58613    73400953+   c  W95 FAT32 (LBA)
/dev/sda14          58614       60800    17567046    b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x344fc7ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS






menu.lst:

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f905bd90-b2b1-462c-a3c2-1e2f3a29afa6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f905bd90-b2b1-462c-a3c2-1e2f3a29afa6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f905bd90-b2b1-462c-a3c2-1e2f3a29afa6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f905bd90-b2b1-462c-a3c2-1e2f3a29afa6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f905bd90-b2b1-462c-a3c2-1e2f3a29afa6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f905bd90-b2b1-462c-a3c2-1e2f3a29afa6 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f905bd90-b2b1-462c-a3c2-1e2f3a29afa6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f905bd90-b2b1-462c-a3c2-1e2f3a29afa6 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by |{urse on 2008-05-15
youre probably going to have to insert your "legal" xp disk and select 'r' (recovery console) press 1 and enter

type "fixboot"

type "fixmbr"

you should be able to boot into windows but not ubuntu now

then you will need to reinstall grub with an ubuntu livecd.

insert Live CD, boot from it until you reach the desktop.
Open a terminal.
Type "grub"
Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever the command tells you for the following lines.
Type "setup (hd0)", change "(hd0)" to what find /boot/grub/stage1 told you to use
type "quit".
reboot.

Hopefully that helps

---

### Post by Homeschool Hacker on 2008-05-15
I was kind of hoping I wouldn't have to do this.  :/

Any idea on why this happened?

Thanks!

---

### Post by |{urse on 2008-05-15
just to be sure im understanding your problem, is your pc trying to boot windows (i.e you "see the splash but it reboots midway")?

np mang ^^

---

### Post by Homeschool Hacker on 2008-05-15
It doesn't get as far as the splash screen.

When I select "Windows XP" from the grub boot menu, my computer reboots, goes back through the BIOS (and returns to the grub screen).

---

### Post by |{urse on 2008-05-15
LOL it happened because linux kicked xp's *** again. j/k but i bet it's all on the xp side as to why it's not playing nicely.

---

### Post by Homeschool Hacker on 2008-05-15
I'm thinking it has to do with the upgrade, since it worked before I upgraded.  :/

---

### Post by |{urse on 2008-05-15
yeah, sounds like the usual dual boot probs. Try doing the method above, should get you back in business. also if for some reason windows works fine but ubuntu suddenly has trouble booting, you can use the livecd to boot to it and come back for more help.


BY THE WAY, you have the alternate cd, you're going to need to download the livecd to do this.

---

### Post by Homeschool Hacker on 2008-05-15
ok, Thanks, |{urse!

---

### Post by |{urse on 2008-05-15
Make sure and come back to this thread and let me know if it worked. ^^

---

### Post by Pumalite on 2008-05-15
Get Super Grub: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it. See if you can boot Windows. If it's usable; Super Grub will boot it.

---

### Post by Homeschool Hacker on 2008-05-15
I will.  Thanks!

---

### Post by Homeschool Hacker on 2008-05-15
Ok, I tried SuperGRUB to no avail.  Next I'll do the Windows and GRUB recoveries.

---

