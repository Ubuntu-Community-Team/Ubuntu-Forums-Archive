---
title: "No grub after installing Ubuntu 12.04"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by Tracks30 on 2012-06-06
It for some reason couldn't properly install grub during installation, though the rest worked just fine. So Windows 7 boots normally, it just doesn't recognize the fact that Ubuntu exists and doesn't appear to be easily fixed using EasyBCD.
 I ran the bootinfoscript and got the following (copied the bit that seemed relevant):

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........D.8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 7379736 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

```

---

### Post by 23dornot23d on 2012-06-06
It is installed on your second hard drive sdb

All that you need to do - as it boots up select the other drive to boot from .... 
( often means holding a key down at boot ESC or F2 or another Function key - check your computer manual or look online )
( depends on your computer often it flashes up on the boot screen )
this can also be done in the BIOS if you want to do it on a more permanent basis.

sda is windows boot ....

ok looking at the error - not seen that before

[http://www.google.com/search?q=The+integrity+check+of+the+ADV+area+failed&ie=utf-8&oe=utf-8&client=ubuntu&]("http://www.google.com/search?q=The+integrity+check+of+the+ADV+area+failed&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs")[channel=fs]("http://www.google.com/search?q=The+integrity+check+of+the+ADV+area+failed&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs")

The solved ones - may be worth looking through these

[http://www.google.com/search?q=The+integrity+check+of+the+ADV+area+failed&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=The+integrity+check+of+the+ADV+area+failed+solved&oq=The+integrity+check+of+the+ADV+area+failed+solved&aq=f&aqi=&aql=&gs_l=serp.3...12434.17790.0.18068.13.11.2.0.0.0.195.1619.1j10.11.0...1.0.wmv73GKQNkU&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=85078f4c71ae73ac&biw=1136&bih=483](http://www.google.com/search?q=The+integrity+check+of+the+ADV+area+failed&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=The+integrity+check+of+the+ADV+area+failed+solved&oq=The+integrity+check+of+the+ADV+area+failed+solved&aq=f&aqi=&aql=&gs_l=serp.3...12434.17790.0.18068.13.11.2.0.0.0.195.1619.1j10.11.0...1.0.wmv73GKQNkU&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=85078f4c71ae73ac&biw=1136&bih=483)

---

### Post by Tracks30 on 2012-06-06
Are you sure the sdb is not referring to the flash drive I used to run Ubuntu (and used to install it)? Because it definitely works from that, just not from the actual harddrive...

---

### Post by 23dornot23d on 2012-06-06
Looked again .... seems that its not installed properly sda5 is showing no information and the boot on sda is windows .... check some of the solved links that I posted in the previous thread I did ..... as I added to it.

---

### Post by eddier on 2012-06-06
During installation at the disk partitioning stage,way down the bottom you can select which drive to install grub. If you have a second hard drive- grub install defaults to sdb for some odd reason.

I actually installed twice before I discovered what was happening-I had installed Linux to sda1,2,3 but grub had been dumped onto my backup/data drive.:-\"

eddie

---

### Post by wilee-nilee on 2012-06-06
You just need a install of these files to the ubuntu install.

/boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

/etc/fstab is there already the others are just missing.

Is the bootscipt shown all the text from the results.txt?

If the rest of you look carefully, the sdb did not get the grub boot  files it is a multiboot thumb, the files are correct. 

Posting a google  search is not helpful, and the interpretation is incorrect.

---

### Post by oldfred on 2012-06-07
It looks like no part of grub2 installed at all. And you did not post the entire script to see what else may or may not be missing.

You could chroot into your install and run the same commands as the purge & reinstall, although it looks like there is nothing to purge. You may want to run other commands to refresh system, update kernel while in chroot. But this assumes the rest of system is ok.

HOWTO: Purge and Reinstall Grub 2 from the Live CD 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You can also run these while in the chroot (# are comments, do not type):
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a


Or you could try a full reinstall, but we are not sure what caused grub not to install. Sometimes it does not install the boot loader to the MBR, but it usually still installs the rest of grub2.

---

### Post by Tracks30 on 2012-06-07
This is the entire report. Does anything else seem to be wrong?

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........D.8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 7379736 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,265,024    27,469,823       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,469,824   468,527,005   441,057,182   7 NTFS / exFAT / HPFS
/dev/sda4         468,527,102   625,141,759   156,614,658   5 Extended
/dev/sda5         468,527,104   617,289,727   148,762,624  83 Linux
/dev/sda6         617,291,776   625,141,759     7,849,984  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
16 heads, 32 sectors/track, 15296 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,831,551     7,831,520   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A070061D7005FB34                       ntfs       PQSERVICE
/dev/sda2        343A06D03A068ED4                       ntfs       SYSTEM RESERVED
/dev/sda3        A04E779C4E7769C4                       ntfs       Gateway
/dev/sda5        f9f38c87-6e89-48dd-a484-07c6d12dbe92   ext4       
/dev/sda6        b7e1a26a-b383-4846-ae2e-78672767c852   swap       
/dev/sdb1        5C62-909C                              vfat       UDISK 2-0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f9f38c87-6e89-48dd-a484-07c6d12dbe92 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b7e1a26a-b383-4846-ae2e-78672767c852 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-3.2.0-23-generic               1
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f0 dd 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f0  dd 08 00 d0 77 00 00 00  |............w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected


```

---

### Post by 23dornot23d on 2012-06-07
Looking at the full bootscript info .....

> 
======================== Unknown MBRs/Boot Sectors/etc: ========================  Unknown BootLoader on sda4


Possible problem the bootloader looks as if it was installed to [COLOR=Red]sda4 the extended partition for some reason[/COLOR] ....

Seems a lot of others are reporting a similar problems ....

[http://www.google.com/search?q=Unknown+BootLoader+on+sda4&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=Unknown+BootLoader+on+sda4+extended+partition&oq=Unknown+BootLoader+on+sda4+extended+partition&aq=f&aqi=&aql=&gs_l=serp.3...41221.59440.0.60422.35.28.7.0.0.1.828.5084.0j24j3j6-1.28.0...1.0.Dh8h8d0BatA&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=85078f4c71ae73ac&biw=1136&bih=454](http://www.google.com/search?q=Unknown+BootLoader+on+sda4&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=Unknown+BootLoader+on+sda4+extended+partition&oq=Unknown+BootLoader+on+sda4+extended+partition&aq=f&aqi=&aql=&gs_l=serp.3...41221.59440.0.60422.35.28.7.0.0.1.828.5084.0j24j3j6-1.28.0...1.0.Dh8h8d0BatA&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=85078f4c71ae73ac&biw=1136&bih=454)

If you did not want the boot to go to sda for fear of having a problem with windows - you could always write the bootloader to the flash drive - I sometimes do this as a backup.

 sudo grub-install /dev/sdb

This needs checking using df ..... if you have more than one drive then the flash drive may be identified as something else ..... ( but from what you have said above your flash drive is /dev/sdb

So in the case above it is /dev/sdb

_________________________________________

This will only work after you have [COLOR=Red][B]
re-installed the OS and put the boot loader onto sda5[/B][/COLOR] - if that is what you were trying to do ....

Running  
[COLOR=Red]**sudo grub-install /dev/sdb**[/COLOR]

Will then allow you to boot into sda5 from the flash drive - and when the flash drive is removed it should boot normally from windows as before.

---

### Post by wilee-nilee on 2012-06-07
Oldfreds post is really your best answer here with a purge and install here is the basic commands for that if needed. The rest of the post are guessing and not even close and just clouding the thread.

You are just missing the boot files in the ubuntu install, and grub in the mbr.

Boot a Ubuntu live usb or cd to a terminal and run these commands.

This first command is to confirm the HD is being read as sda, if it is sdb, the change the a to a b in the commands after this first one.

```
sudo fdisk -l
``````
sudo mount /dev/sda5 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
apt-get purge grub-pc grub-common
```You may get an error here as these don't seem to be installed if so just keep running these commands, if asked to remove all grub say yes.```
apt-get install grub-pc grub-common
```Here you will be asked where grub goes, choose the mbr sda or sdb depending on how the first command shows the hard drive as. Use the space key to tick the mbr only
```
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```

---

### Post by Tracks30 on 2012-06-07
> **wilee-nilee said:**
> Here you will be asked where grub goes, choose the mbr sda or sdb depending on how the first command shows the hard drive as. Use the shift key to tick the mbr only

Feeling very silly for asking this: how do I navigate this bit? As in, how do I tick the boxes?
(And, just to make sure, given the choice between these three:
[ ] /dev/sda (320072 MB; ???)
[ ] - /dev/sda5 (76166 MB; /)
[ ] /dev/sdb (4009 MB; ???)
Which one do I want? sda? With sdb being my flash drive.)

---

### Post by wilee-nilee on 2012-06-07
> **Tracks30 said:**
> Feeling very silly for asking this: how do I navigate this bit? As in, how do I tick the boxes?
(And, just to make sure, given the choice between these three:
[ ] /dev/sda (320072 MB; ???)
[ ] - /dev/sda5 (76166 MB; /)
[ ] /dev/sdb (4009 MB; ???)
Which one do I want? sda? With sdb being my flash drive.)

It is confusing at first, the arrow keys will move from choice to choice the space key, is the one that marks them just choose sda.

I said shift my bad. :oops: I have edited the original, sorry about that.

---

### Post by Tracks30 on 2012-06-07
Ah, thanks a lot! It seems to all be working now.

---

### Post by wilee-nilee on 2012-06-07
> **Tracks30 said:**
> Ah, thanks a lot! It seems to all be working now.

Cool, enjoy. ;)

---

