---
title: "Grub setup is 100% correct, but doesnt work"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2008-09-28
[COLOR="Red"][SIZE="5"]Solved![/SIZE][/COLOR]
Solution is [here]("http://ubuntuforums.org/showpost.php?p=5874005&postcount=10").


[COLOR="Red"][SIZE="4"]Issue:[/SIZE][/COLOR]
```
# Modified by YaST2. Last modification on Sun Sep 28 15:41:36 PDT 2008
default 0
timeout 8
gfxmenu (hd0,1)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows Vista x64
    rootnoverify (hd1,0)
    chainloader (hd1,0)+1

title Windows Vista x32
    rootnoverify (hd0,1)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE x64
    root (hd0,1)
    kernel /boot/vmlinuz root=/dev/disk/by-id/scsi-SATA_Hitachi_HTS5416_SB2481SJK4SGBE-part2 resume=/dev/sda3 splash=silent showopts vga=0x31a
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE x64
    root (hd0,1)
    kernel /boot/vmlinuz-2.6.25.16-0.1-pae root=/dev/disk/by-id/scsi-SATA_Hitachi_HTS5416_SB2481SJK4SGBE-part2 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.25.16-0.1-pae

```

here is fdisk -l output:
```
linux-5xr0:~ # fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x053e5bef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12272    98566807    7  HPFS/NTFS
/dev/sda2   *       12272       18930    53480354+  83  Linux
/dev/sda3           18930       19457     4241159+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e85b147

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488382464    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82273118

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```

I have vista x64 on a separate harddrive(500gb), and vista x32 and linux on my 2nd(150gb). I'm pretty sure i set that up correctly, BUT in the bootloader, weather i select the x64 or x32 then BOTH boot to the x32  HELP PLEASE

---

### Post by caljohnsmith on 2008-09-28
You have two identical 500 GB drives, sdb and sdc. Which has Windows Vista 64-bit, and what is on the other HDD? Your menu.lst/grub.conf appears to be for OpenSUSE, so just out curiosity, is there some particular reason you are posting in a Ubuntu forum? Do you have OpenSUSE installed in sda2?

---

### Post by ArchCorsair on 2008-09-28
> **caljohnsmith said:**
> You have two identical 500 GB drives, sdb and sdc. Which has Windows Vista 64-bit, and what is on the other HDD? Your menu.lst/grub.conf appears to be for OpenSUSE, so just out curiosity, is there some particular reason you are posting in a Ubuntu forum? Do you have OpenSUSE installed in sda2?

yes, its openSUSE. but it's a boot problem, so it really shouldn't make a difference weather its ubuntu or openSUSE. There are 2 500gb HDDs, 1 is the Vista x64, 2 is my external i use for backups.

---

### Post by louieb on 2008-09-28
> **ArchCorsair said:**
> ```

title Windows Vista x64
    rootnoverify (hd1,0)
    chainloader (hd1,0)+1

title Windows Vista x32
    rootnoverify (hd0,1)
    chainloader (hd0,0)+1

  

```...
BUT in the bootloader, weather i select the x64 or x32 then BOTH boot to the x32  HELP PLEASE
Your chainloading two different partitions. If you get the same thing no mater what you choose that means one thing. The boot sector of your 64 bit install partition is the same as the boot sector of the 32 bit install partition.

Just a wild as guess but believe you need to boot your 64 bit install CD and select the recovery console and run the command **fixboot**.

---

### Post by WWSmith36 on 2008-09-28
Windows must and will only boot to primary hard drive.  That is why it always load the 32bit version.  You need to fool windows into thinking the 64bit version is on the primary hard drive.

In ubuntu you would have to change the vista 64 entry to

title Windows Vista x64
    rootnoverify (hd1,0)
    map (hd0) (hd1)
    map (hd1) (hd0)
    chainloader +1

---

### Post by WWSmith36 on 2008-09-28
bump

---

### Post by Bakon Jarser on 2008-09-28
Are both windows installs on the same hard drive?  You have them each mapped to a different hard drive there.

---

### Post by ArchCorsair on 2008-09-28
This is my setup:
HDD #1: 500gb Internal -> Vista 64bit (1 partition)
HDD #2: 150gb Internal -> Vista 32bit AND openSUSE 64bit +4gb swap
HDD #3: 500gb EXTERNAL. not to worry about.

> **Bakon Jarser said:**
> Are both windows installs on the same hard drive?  You have them each mapped to a different hard drive there.

No, my primary OS (vista x64) is installed on the 500gb internal and vista x32 is installed on the 150gb internal

---

### Post by Bakon Jarser on 2008-09-29
```
# Modified by YaST2. Last modification on Sun Sep 28 15:41:36 PDT 2008
default 0
timeout 8
gfxmenu (hd0,1)/boot/message
##YaST - activate


###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows Vista x64
    rootnoverify (hd1,0)
    map (hd0) (hd1)
    map (hd1) (hd0)
    chainloader +1

title Windows Vista x32
    rootnoverify (hd0,1)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE x64
    root (hd0,1)
    kernel /boot/vmlinuz root=/dev/disk/by-id/scsi-SATA_Hitachi_HTS5416_SB2481SJK4SGBE-part2 resume=/dev/sda3 splash=silent showopts vga=0x31a
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE x64
    root (hd0,1)
    kernel /boot/vmlinuz-2.6.25.16-0.1-pae root=/dev/disk/by-id/scsi-SATA_Hitachi_HTS5416_SB2481SJK4SGBE-part2 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.25.16-0.1-pae
```

I think it should look something like that.  Might have to play with the vista 64 rootnoverify numbers.

---

### Post by ArchCorsair on 2008-09-29
I have fixed it. Here is the solution (thanks to WWSmith36)

[COLOR="Red"][SIZE="5"]Solution:[/SIZE][/COLOR]
```

title Windows Vista x64
rootnoverify (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```

---

