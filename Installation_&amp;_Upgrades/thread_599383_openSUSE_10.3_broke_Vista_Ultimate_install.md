---
title: "openSUSE 10.3 broke Vista Ultimate install"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Next.Step on 2007-11-01
Always like to experiment.
So while waiting to the Gutsy ShipIt CDs I decided to try openSUSE 10.3 with KDE desktop.
Everything worked fine, I've set up a dual-boot with 1 openSUSE partition, 1 swap, 1 windows partition and 1 shared NTFS partition for my personal data.

After the installation had finished, when booting Vista, I've got this greeting:
```
c:\windows\system32\winload.exe is missing or corrupt
```

Here is some technical data:
cat /boot/grub/menu.lst
```
# Modified by YaST2. Last modification on Wed Oct 31 17:3:21 UTC 2007
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Originalname: linux###
title openSUSE 10.3
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/dik/by-id/scsi-SATA_WDC_WD800JB-00FWD-WMAJ96180358-part3 vg=0x317    resume=/dev/sda4 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Originalname: failsafe###
title openSUSE 10.3 | Failsafe
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/dik/by-id/scsi-SATA_WDC_WD800JB-00FWD-WMAJ96180358-part3 vg=normal showopts ide=nodma apm=off acpi=off noresume nosm noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Originalname: windows 1###
title Windows Vista Ultimate
    rootnoverify (hd0,2)
    chainloader (hd0,0)+1
```

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003499

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5366    43102363+   7  HPFS/NTFS
/dev/sda2            5367        8857    28033425    7  HPFS/NTFS
/dev/sda3   *        8928        9729     6442065   83  Linux
/dev/sda4            8857        8927      570276   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Couriously, when installing ubuntu back over SUSE Vista is OK again after a system repair. When having openSUSE instead of ubuntu, Vista install DVD doesn't recognize Vista so I can't repair it.
Anyone can help or point me to the right direction?

---

### Post by PmDematagoda on 2007-11-01
Not sure if this may work out, but try using the Grub entry for Vista by Ubuntu in place of the one automatically created by Open SUSE.

---

### Post by Next.Step on 2007-11-01
I do not have Ubuntu installed.
I've read that there's some data overwritten in the MBR that is checked by Vista and somebody mentioned solving it with EasyBCD. But that's not for me since OBVIOUSLY my windows install is broken!

---

### Post by Pumalite on 2007-11-01
Get Super Grub and fix your Windows: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Next.Step on 2007-11-01
I tried to uninstall GRub with it, nothing happened.
Booting windows not worked through it neither.

---

### Post by Pumalite on 2007-11-01
I'd read the instructions very carefully. Beyond that; you can use Knopixx Live CD and look at your drives/partitions. If they are shot, start again.

---

### Post by Next.Step on 2007-11-01
The drives/partitions are fine. It's windows what's making problems.

---

### Post by stevie_velvet on 2007-11-01
Thats  correct. As it's a Windows Problem, it's outside the scope of *nix
Whatever is in the MBR Kicks off the Windows Boot Manager, which then kicks off 'winload.exe'

Assuming your windows folder is intactt, you will need to repair your Windows Installtion using the Original Vista DVD

---

### Post by Next.Step on 2007-11-01
The windows DVD does not recognize my Vista installation. 
Couriously, when I install Ubuntu, it does.

---

### Post by Fire_Chief on 2007-11-01
Your grub menu.lst file is pointing to the wrong partition for Vista.

Your entry says
```

###Don't change this comment - YaST2 identifier: Originalname: linux###
title openSUSE 10.3
    root (hd0,2)          **<- right**
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/dik/by-id/scsi-SATA_WDC_WD800JB-00FWD-WMAJ96180358-part3 vg=0x317    resume=/dev/sda4 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Originalname: failsafe###
title openSUSE 10.3 | Failsafe
    root (hd0,2)          **<- right**
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/dik/by-id/scsi-SATA_WDC_WD800JB-00FWD-WMAJ96180358-part3 vg=normal showopts ide=nodma apm=off acpi=off noresume nosm noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Originalname: windows 1###
title Windows Vista Ultimate
    rootnoverify (hd0,2)          **<- wrong**
    chainloader (hd0,0)+1

```
The entry for Vista should look like this
```
title Windows Vista Ultimate
    rootnoverify (hd0,0)  
    chainloader +1
```

---

### Post by unixcrab on 2007-11-01
exactly same thing happened to me :( 
10.3 went into the trash...

---

### Post by Next.Step on 2007-11-01
Solved!

I really have no idea how i did this.
Somehow I have redone the MBR with GRUB super disc, and now vista boots fine after a repair using the installation DVD. Then added an openSUSE entry with EasyBCD to Vista Bootloader. Now I use Vista bootloader, and if I select openSUSE it brings me GRUB. Not so nice, but I can live with that,
What a pity, openSUSE. You seemed such a serious distro...

---

### Post by Fire_Chief on 2007-11-01
Congrats! Glad you got it working one way or another.

Would you please change the title of the thread to now have [solved] at the beginning? This is very helpful for future users who might encounter the problem.

Thanks!

---

### Post by Nunslaughter on 2007-11-06
i also have the same problem...
i installed opensuse between vista and ubuntu gutsy...gutsy boots fine with the suse grub, but got the same error like you for vista...and also my dvd didn't see any windows installation...
i'm going to try the solution which Fire_Chief gave, otherwise i'll try that grub super disc...

if that won't work, well, opensuse off my disk...too bad, cause i wanted to try this for some time...

---

### Post by Pumalite on 2007-11-06
> **Next.Step said:**
> Solved!

I really have no idea how i did this.
Somehow I have redone the MBR with GRUB super disc, and now vista boots fine after a repair using the installation DVD. Then added an openSUSE entry with EasyBCD to Vista Bootloader. Now I use Vista bootloader, and if I select openSUSE it brings me GRUB. Not so nice, but I can live with that,
What a pity, openSUSE. You seemed such a serious distro...

I told you; Super Grub never fails!

---

### Post by HMartinho on 2008-03-03
Hi all;

#10 did it for me, it worked like a charm.
Thanks fire-chief!

Cheers.

---

