---
title: "Grub"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by MetalDragon on 2007-09-03
Hi,
New to this so please bear with,

I am duelx2 booting an Intel pc with Vista, XP twice, OSX 10.4.8 and Ubuntu.
I use an MBR boot at start, no probs there.

I have Ubuntu installed with /boot /  and /swap.
When I start Unbuntu I have the selections of the OS's in grub which is all good...but when I start Vista it attempts to starts and then the PC powers off, starting XP is fine, will not find OSX under other operating systems.

I think I need to refresh/update grub could someone please tell me how to go about this in real pain and simple way, like step 1 step 2 etc.

Or at least show me a thread because I cant find one.
recap: no probs with starting any of the OS's from MBR.
           Ubuntu grub installed to /boot.
           Cant start some OS's from the Grub menu

Sorry if this is the wrong forum...:) NewB

---

### Post by Pumalite on 2007-09-03
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by MetalDragon on 2007-09-03
> **Pumalite said:**
> Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

Sweet, sorry to sound so stupid but where do I start from? within ubuntu or from a safe boot.
Complete newB like a week old been on M/soft too long.
Sorry to be a pain U can :lolflag: at me.

---

### Post by Pumalite on 2007-09-03
Applications>Accessories>Terminal

---

### Post by MetalDragon on 2007-09-03
> **Pumalite said:**
> Applications>Accessories>Terminal

Thxs, of I pop to try something new, info in hand.

---

### Post by Pumalite on 2007-09-03
Copy and paste in your post.

---

### Post by MetalDragon on 2007-09-03
> **Pumalite said:**
> Copy and paste in your post.

Sorry? copy n paste What in the post, dont forget newB to all of this.

Well that didnt work, I think I must of did something wrong as it mounted the Mac part and changed the file system linux.

Do I need to nano the menu.lst by hand to update it?

When n how does it update the menu.lst, just trying to understand the running of it all.:(

---

### Post by Pumalite on 2007-09-03
Lets see what you have first; then we'll decide what to do.

---

### Post by MetalDragon on 2007-09-03
> **Pumalite said:**
> Lets see what you have first; then we'll decide what to do.

O.k this is what I got:
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   143362047    71680000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       143362107   206499509    31568701+  17  Hidden HPFS/NTFS
/dev/sda3       206499510   327742064    60621277+   f  W95 Ext'd (LBA)
/dev/sda4       327742065   390716864    31487400   af  Unknown
/dev/sda5   *   206499573   206708354      104391   83  Linux
/dev/sda6   *   206708418   213311069     3301326   82  Linux swap / Solaris
/dev/sda7   *   213311133   327742064    57215466   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sdb2       204796620   390716864    92960122+  17  Hidden HPFS/NTFS


GRUB:
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=f0de7edc-eba7-41f9-b937-e76d7c17aeff ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,4)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=f0de7edc-eba7-41f9-b937-e76d7c17aeff ro single
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=f0de7edc-eba7-41f9-b937-e76d7c17aeff ro quiet splash
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,4)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=f0de7edc-eba7-41f9-b937-e76d7c17aeff ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root            (hd0,3)


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP (loader)
root            (hd0,1)
savedefault
chainloader     +1

Below is what I typed in by hand

[B][I]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title           Windows /XP (loader)
root            (hd1,1)
savedefault
chainloader     +1
[/I][/B]

---

### Post by Pumalite on 2007-09-03
For Windows, should be 'root (hd1,0)

---

### Post by MetalDragon on 2007-09-04
> **Pumalite said:**
> For Windows, should be 'root (hd1,0)

Close I think.

Message on black screen: A error reading disk, Press Ctrl, Alt, Del to reboot.

(hd1) or (sdb2) boots fine by its self if (hd0) is removed.

In fdisk it says a partition is hidden, could this be the reason why it can't read the disk correctly? If so how does one go about getting unbuntu to see the partition

---

### Post by Pumalite on 2007-09-04
This partition is a real problem in most laptops installations. A lot if not all laptop are sold without disk and a 'recovery' partition instead, If this partition is a problem now it will continue to be in the future. If I were you (meaning: wanting to have Windows), I would backup all data, buy an OEM XP for ten bucks(you can use the serial # stuck in the laptop), use DBan to wipe the hard drive, then use Gparted to partition; install Windows in sda1 and then Ubuntu with Grub in the MBR.

---

### Post by MetalDragon on 2007-09-04
> **Pumalite said:**
> This partition is a real problem in most laptops installations. A lot if not all laptop are sold without disk and a 'recovery' partition instead, If this partition is a problem now it will continue to be in the future. If I were you (meaning: wanting to have Windows), I would backup all data, buy an OEM XP for ten bucks(you can use the serial # stuck in the laptop), use DBan to wipe the hard drive, then use Gparted to partition; install Windows in sda1 and then Ubuntu with Grub in the MBR.

Are you talking about an EFI partition or something like that. A hidden one with a restore image on it?
Any way lucky that's not the issue here thank god. Or may be it could be the fix we are all looking for with this primary disk limit, booting and a second IDE drive.  I will look into that when I have some time spare.

OK.... I can now boot XP from Ubuntu on 1st IDE(hd0) with XP being 2nd IDE (hd1):
title           Windows /XP (loader)
root            (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
savedefault
chainloader     (hd1,0)+1

The above Fixed the problem of Autochk program not found when booting XP on the 2nd drive, I also had to make it active.

Things are looking up.

---

### Post by Pumalite on 2007-09-04
Well, good for you!

---

### Post by MetalDragon on 2007-09-05
> **Pumalite said:**
> Well, good for you!

Many thanks for your help, without it I would not of known where to start.:)

---

