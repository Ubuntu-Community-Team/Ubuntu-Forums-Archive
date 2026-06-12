---
title: "Unable to see or allocate drive space on install."
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by cb0159 on 2011-06-21
I have an Acer Aspire One that came with Windows 7 starter and 1GB of ram. Needless to say it ran horrible.

I am currently trying to install Ubuntu 11.04 via USB drive. 

The problem that I am having is, whenever I get to the Allocate drive space screen it shows nothing. The box is pink with not text. 

If I click on Install now anyway I receive a No Root File System error.

Currently the hard drive has NO partitions on it, including no file systems. It's completely blank and it is also showing up in my BIOS.

I do not know what other information would be useful so please ask. Any help I can get on getting this installed would be greatly appreciated!

Thanks!

~cb0159

---

### Post by Quackers on 2011-06-21
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by cb0159 on 2011-06-21
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 60868 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    15,633,407    15,633,345   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1912-0E22                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

no block devices found 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by cb0159 on 2011-06-21
I guess I should mention that when I came home I tried to install again for giggles and it went through fine. It saw the HDD fine and installed fine (I think). However, then it wouldn't boot at all. I had to reinstall Ubuntu to my USB in order to get back into the "Trial" mode so I could run the script.

---

### Post by Quackers on 2011-06-21
So you now have Ubuntu installed, but it won't boot, is that correct?
Please re-run the boot script and post the contents of the new Results1.txt
It will give details of what has been installed where - if anything :-)

---

### Post by cb0159 on 2011-06-22
That log is from after I installed Ubuntu. Do you want me to give it another shot?

---

### Post by Quackers on 2011-06-22
In that case then the hard drive is not being seen.
Are you using SATA3 ports?

If you boot into the Ubuntu live desktop and open gparted is there any entry there for your hard drive, or just for the flash drive?
Click on the little arrow in the box displaying /dev/sda for other drives.

---

### Post by cb0159 on 2011-06-22
I will check when I get home. I am beginning to think that HDD is going bad and that is the cause of all my problems. It is a SATA drive though (Toshiba 160GB).

---

