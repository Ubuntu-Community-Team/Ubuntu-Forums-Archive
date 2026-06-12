---
title: "Dual-boot on a RAID-0 array - drops to GRUB command line"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by dwigyit on 2011-05-28
I've recently had trouble reinstalling my Ubuntu system as I was getting various unusual errors as described in my old thread [here]("http://ubuntuforums.org/showthread.php?t=1767203").

I thought it was probably something to do with my RAID-0 array which was pre-installed on my laptop from purchase being corrupted or something like that (if it's possible). I decided to simplify things for myself (not understanding RAID arrays much) so I just removed the RAID array and installed Windows and Ubuntu on the now separate hard disks. It worked fine.

I noticed quite a significant performance drop, however, with even Ubuntu boots taking longer than 30 seconds despite my laptop being both high-spec and only a few months old. Windows, as you can imagine, was dreadfully slow. I wasn't entirely convinced that this was entirely due to the loss of the RAID array - as even low-spec laptops with presumably no RAID arrays are supposed to boot Ubuntu in under 30 seconds apparently - but I read that RAID-0 arrays do improve performance so I re-created the array and installed Windows and Ubuntu again.


The problem is that Ubuntu does not install properly. I installed Windows to the entire 1TB disk and then, in Ubuntu, used GParted to shrink the partition by about 30GB (intending to store all my media on the windows partition). The installer loads and finishes with no errors or problems, but unfortunately it jumps to the GRUB command line at every boot and cannot load either Windows or Ubuntu. The Windows CD can repair it but, of course, that leaves me unable to boot Ubuntu :(

Please advise if you can - I'd guess that it's either a GRUB problem or something wrong with the Ubuntu partition



EDIT - I think it is a problem with the Ubuntu partition, as the Ubuntu live CD (USB) can't access it. Was it perhaps because of my use of GParted and, if so, is there an alternative way to do it? Or is it just the Ubuntu installer and RAID-0 arrays not getting along. It should be noted that it worked fine when I first got the laptop and installed Maverick, though I don't know if I used GParted or not.

---

### Post by Quackers on 2011-05-28
What version of Ubuntu are you using? Did you get an error about grub installing to /dev/sda, or similar?

---

### Post by dwigyit on 2011-05-28
11.04 - Natty Narwhal - installed from a live USB

And no, there were no errors during the installation whatsoever - no sign that there was a problem. GRUB is installed and loaded, though - just looks as though it can't find its own folder so it displays the GRUB recovery command line. Seeing as the live CD can't see the Ubuntu partition's contents, I'd guess the problem lies there?

---

### Post by dwigyit on 2011-05-29
Another interesting thing - don't know if this is just to do with the Live CD but it might be important?

There are two 1TB HDDs shown in Disk Utility... but the RAID array only made one out of the 2 500Gb drives. It also seems as though this second one is corrupted (everything is "Unknown") - even though it shouldn't even exist.

Even more interesting (for me, at least :D ) is that the NTFS partition fills the whole of the non-corrupt 1TB drive (the real one, I guess), and it also says it's not partitioned (there should be a 30GB Ext4 partition there with a bit of SWAP space. 

Might it be worth using the Windows partition manager to shrink the Windows partition instead of GParted next time?

---

### Post by Quackers on 2011-05-29
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder).
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dwigyit on 2011-05-29
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_bffjjdgag_Volume0 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks in partition 5 for /boot/grub.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.82 2009-06-09
    Boot sector info:   Syslinux looks at sector 8200 of /dev/sdc1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

isw_bffjjdgag_Volume01: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

isw_bffjjdgag_Volume02: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2048 MB, 2048901120 bytes
64 heads, 62 sectors/track, 1008 cylinders, total 4001760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     3,999,743     3,999,682   b W95 FAT32


Drive: isw_bffjjdgag_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_bffjjdgag_Volume0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bffjjdgag_Volume01   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bffjjdgag_Volume02            206,848 1,953,533,951 1,953,327,104   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bffjjdgag_Volume0p1 8018E5CB18E5BFF0                       ntfs       System Reserved
/dev/mapper/isw_bffjjdgag_Volume0p2 9CF0E73FF0E71DF0                       ntfs       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc1        868D-CBE6                              vfat       UBUNTUSTICK

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bffjjdgag_Volume0
isw_bffjjdgag_Volume0p1
isw_bffjjdgag_Volume0p2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0

include menu.cfg

default vesamenu.c32

prompt 0

timeout 50

ui gfxboot bootlogo

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_bffjjdgag_Volume01


Unknown BootLoader on isw_bffjjdgag_Volume02



=============================== StdErr Messages: ===============================

unlzma: Decoder error
hexdump: /dev/mapper/isw_bffjjdgag_Volume01: No such file or directory
hexdump: /dev/mapper/isw_bffjjdgag_Volume01: No such file or directory
hexdump: /dev/mapper/isw_bffjjdgag_Volume02: No such file or directory
hexdump: /dev/mapper/isw_bffjjdgag_Volume02: No such file or directory

```

There you go ;)   It'd be cool if they loaded this script on the Live CD to start with - seeing how often people ask for it :D

---

### Post by Quackers on 2011-05-29
Your problem appears to be that Ubuntu is not installed to your raid array, but grub is installed to the mbr of that raid array.
It also appears that you have not made any partitions in the raid array for Ubuntu to use. Is that correct?

---

### Post by dwigyit on 2011-05-29
No - as I said in my first post, I used GParted to make an Ubuntu partition and then installed it with the normal installer. Is it possible for the Ubuntu installer to think its copying to a partition when it really isn't and the partition doesn't even exist?

Should I try re-creating the partition with the Windows partition tool?

---

### Post by dwigyit on 2011-05-29
Sorry to double-post again, but even Windows is getting confused now. I used the Windows CD to put the Windows loader back and went into the Windows partition tool, but I get this screen (attatched).


It shows the total drive capacity as 930Gb, and the NTFS partition as the same - but shows Drive C's capacity as only 890Gb. Seems as though the Ubuntu installer did something after all...

---

