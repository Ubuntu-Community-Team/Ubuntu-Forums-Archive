---
title: "how to boot xp with grub"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by mruschmann on 2011-07-09
I have 3 hard drives:
ubuntu
win 7
win xp

I cant seem to update-grub and find my windows xp hard drive. I can boot it threw bios tho, but i would like boot loader to work.

plz help

---

### Post by drs305 on 2011-07-09
From a terminal, run:```

sudo update-grub
```
Watch the returns and see if the output includes "Found Windows". If it did, it was probably added to your menu. Since you say you can't seem to update grub, does that command return errors or does it just not find Windows?

If not, please download/extract/run the boot info script from the following link while running Ubuntu. It will help us determine what is going on with your system.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by mruschmann on 2011-07-09
It just doesnt find windows xp

---

### Post by mruschmann on 2011-07-09
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done


and of course ....


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x340c340c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee57ee57

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf07cf07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18240   146512768+   7  HPFS/NTFS

---

### Post by mruschmann on 2011-07-09
sdb is my ubuntu HD

---

### Post by mruschmann on 2011-07-09
Here is results:
```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 
    1306869 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   488,394,751   488,187,904   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       976,596       976,563 Swap partition (Linux)
/dev/sdb2         976,597    16,601,597    15,625,001 Data partition (Windows/Linux)
/dev/sdb3      16,601,598 3,907,027,379 3,890,425,782 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   293,025,599   293,025,537   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        34440C63440C29E6                       ntfs       System Reserved
/dev/sda2        C2240DB8240DB109                       ntfs       
/dev/sdb1        4835a675-cce5-4220-8802-5e7078fdf7d1   swap       
/dev/sdb2        83fc41fb-1e00-4e7c-ac8e-229533064dfd   ext4       
/dev/sdb3        d86c241b-5eab-4175-8dc9-aa0a83135e44   ext4       
/dev/sdc1        204C11144C10E5F6                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb3        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
--------------------------------------------------------------------------------

========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```

---

### Post by oldfred on 2011-07-09
Script truncated. Do you have grub4dos in your win7 root folder? That caused script error it seems.

But grub will never find an XP install, as windows litterally moves the boot files from a second install to the first install, so windows can boot it. Then grub only finds the first windows install and boot that, then windows gives you a choice of which windows to boot.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You may be able to move the XP boot files back to your Windows XP partition possibly do windows repairs and then grub will find it and let you boot it directly.

WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Boot.ini has to refer to the correct drive & partition to allow it to work. Sometime fixboot is also required. For windows repairs to work, the windows primary partition has to have a boot flag, but only one boot flag per drive.

---

### Post by mruschmann on 2011-07-10
gonna give this a whirl ... feel confident.

I tried activating the xp driver, nothing came of it.  I should of installed xp then 7.  anyhow, this looks promising:

You can - But you will have to repair the boot manager from the Windows 7  disc.    The reason why is XP will install it's own (older) version,  and XP's boot manager can not boot to win 7.      Repairing using the  Win 7 disc will re-install Win7's boot manager, which can start XP.

report back soon.

---

### Post by mruschmann on 2011-07-12
Ok, this is how i did it.

1 - set windows 7 as hd 0 in bios
2 - download and run easybcd
3 - see if xp boot from windows 7 boot loader
4 - set ubuntu back to hd 0
5 - boot ubuntu and do a sudo update-grub
6 - finds xp
7 - reset window 7 as hd 0
8 - boot into 7, run easy bcd remove xp since grub does it now (will remove boot loader making win 7 quicker to load)
9 - set unbuntu back to hd 0.
10 - cheers!!!!!!

---

