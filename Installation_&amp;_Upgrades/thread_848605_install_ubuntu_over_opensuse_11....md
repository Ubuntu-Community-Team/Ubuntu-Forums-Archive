---
title: "install ubuntu over opensuse 11..."
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by nexgen on 2008-07-03
I have opensuse 11 installed on my main pc i wanted to try it out but im getting some problems with text overlap no sound my graphics setting dont save after a reboot that i now want to install ubuntu over opensuse, but before i do i wanna make sure i do it right. I read i can run gparted and delete the opensuse partitions and then just install ubuntu but last time i did that on my old pc it messed up grub and it wouldent let me boot into XP anymore. What would be a good way to install ubuntu? run the live CD have it over write the opensuse partitions? will it also over write the grub bootloader suse installed to the ubuntu one?

---

### Post by VMC on 2008-07-03
If you just have gparted delete suse partitions including swap and leave XP's NTFS alone, you shouldn't have any problems.

Lets play safe and output what's there now with this:

if using ubuntu livecd:

```
sudo fdisk -l
```

---

### Post by nexgen on 2008-07-03
> **VMC said:**
> If you just have gparted delete suse partitions including swap and leave XP's NTFS alone, you shouldn't have any problems.

Lets play safe and output what's there now with this:

if using ubuntu livecd:

```
sudo fdisk -l
```

i get this 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       34653   267803550    7  HPFS/NTFS
/dev/sda4           34653       60801   210038402+   f  W95 Ext'd (LBA)
/dev/sda5           34653       34915     2101075   82  Linux swap / Solaris
/dev/sda6           34915       37525    20972826   83  Linux
/dev/sda7           37526       60801   186964438+  83  Linux
ubuntu@ubuntu:~$ 

```

---

### Post by VMC on 2008-07-03
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       34653   267803550    7  HPFS/NTFS
/dev/sda4           34653       60801   210038402+   f  W95 Ext'd (LBA)
/dev/sda5           34653       34915     2101075   82  Linux swap / Solaris
/dev/sda6           34915       37525    20972826   83  Linux
/dev/sda7           37526       60801   186964438+  83  Linux
It's a little strange. Can you post your "/boot/grub/menu.lst".
I would think windows should be on "sda2", it appears it's on "sda3". I think the grub menu would reveal an answer.

---

### Post by nexgen on 2008-07-03
> **VMC said:**
> It's a little strange. Can you post your "/boot/grub/menu.lst".
I would think windows should be on "sda2", it appears it's on "sda3". I think the grub menu would reveal an answer.

how do i get /boot/grub/menu.lst? i did a quick google aand tryed "sudo gedit /boot/grub/menu.lst" to see the file but its blank, do i need to be in opensuse or can i still run it from the live cd (which im on right now)?

---

### Post by jnw222 on 2008-07-03
Which partition is grub on

if you do not know
mount all linux partitions and do a search for "menu.lst"

---

### Post by nexgen on 2008-07-03
> **jnw222 said:**
> Which partition is grub on

if you do not know
mount all linux partitions and do a search for "menu.lst"

not 100% sure how to do that so i booted into opensuse to try to get it not sure if this is it.

```
cat /boot/grub/menu.lst
# Modified by YaST2. Last modification on Wed Jul  2 23:19:39 MST 2008
default 0
timeout 8
gfxmenu (hd0,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title Windows Vista
    rootnoverify (hd0,5)
    chainloader (hd0,2)+1

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0 - 2.6.25.5-1.1
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.25.5-1.1-pae root=/dev/disk/by-id/scsi-SATA_WDC_WD5000AAKS-_WD-WCAS87033097-part6 resume=/dev/sda5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.25.5-1.1-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0 - 2.6.25.5-1.1
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.25.5-1.1-pae root=/dev/disk/by-id/scsi-SATA_WDC_WD5000AAKS-_WD-WCAS87033097-part6 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.25.5-1.1-pae

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,5)
    chainloader (hd0,1)+1
```

---

### Post by nexgen on 2008-07-03
Ok so i just restored the Windows Vista MBR i boot into windows just like if linux was never installed now i plan to run gparted and delete the opensuse partitions now i wanna make sure which ones are the partition i can delete.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       34653   267803550    7  HPFS/NTFS[/COLOR]
[COLOR="Blue"]/dev/sda4           34653       60801   210038402+   f  W95 Ext'd (LBA)[/COLOR]
[COLOR="Green"]/dev/sda5           34653       34915     2101075   82  Linux swap / Solaris
/dev/sda6           34915       37525    20972826   83  Linux
/dev/sda7           37526       60801   186964438+  83  Linux
ubuntu@ubuntu:~$[/COLOR]
```
im pretty sure the ones in red i should not touch at all but im not sure about the one in blue and it looks pretty big, the green ones are Good to Go for a reformat.

so question do i leave the blue one alone?

Also is it better to delete the opensuse partition and leave it as unallocated space or make it a blank partition?

---

