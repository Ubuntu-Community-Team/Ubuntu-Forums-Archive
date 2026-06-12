---
title: "grub resuce no device found"
date: 2014-02-27
forum: Installation &amp; Upgrades
---

### Post by juanfra2 on 2014-02-27
Hello, I changed partition and install Ubuntu 12.04 from win7. when I rebooted it was not posible.

with ls, set etc doesn't work, could somebody helpp me? this is my boot info script and the mensaje 

error: no such device: 6ad07239-5fa0-41d8-bcd3-ad451f4cf1ab
grub rescue>



         Boot Info Script 0.61      [1 April 2012]

============================= Boot Info Summary: ===============================
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 6ad07239-5fa0-41d8-bcd3-ad451f4cf1ab root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdc.
sda1: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 
sda5: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /wubildr
sda2: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr /boot/grub/core.img
sda3: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr
sdb1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk
sdb1/Wubi: _____________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS
    Boot files:        /etc/fstab
sdc1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1               2,048    29,747,199    29,745,152   f W95 Extended (LBA)
/dev/sda5               4,096    29,745,151    29,741,056   7 NTFS / exFAT / HPFS
/dev/sda2    *     29,747,200   420,452,351   390,705,152   7 NTFS / exFAT / HPFS
/dev/sda3         420,452,352   976,769,023   556,316,672   7 NTFS / exFAT / HPFS

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 15.5 GB, 15539896320 bytes
31 heads, 31 sectors/track, 31583 cylinders, total 30351360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdc1               3,240    30,351,359    30,348,120   c W95 FAT32 (LBA)

"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda2        00C417CCC417C2B8                       ntfs       WIN7
/dev/sda3        5264391D643904EF                       ntfs       DATA
/dev/sda5        AC664B01664ACBB0                       ntfs       Nuevo vol
/dev/sdb1        5E8A17868A1759BB                       ntfs       Nuevo vol
/dev/sdc1        3433-3231                              vfat       KINGSTON
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

=================== sda2: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/core.img                             1
============================= sdb1/Wubi/etc/fstab: =============================
--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
--------------------------------------------------------------------------------
================= sdb1/Wubi: Location of files loaded by Grub: =================
           GiB - GB             File                                 Fragment(s)
               =                boot/initrd.img-3.11.0-15-generic             71
               =                boot/vmlinuz-3.11.0-15-generic                25
               =                boot/vmlinuz-3.11.0-15-generic.efi.signed     26
               =                vmlinuz                                       25
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
 linux /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
 initrd /casper/initrd.lz
}
menuentry "Install Ubuntu" {
 set gfxpayload=keep
 linux /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
 initrd /casper/initrd.lz
}
menuentry "Check disc for defects" {
 set gfxpayload=keep
 linux /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
 initrd /casper/initrd.lz
}
--------------------------------------------------------------------------------
=================== sdc1: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
=============================== StdErr Messages: ===============================
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by juanfra2 on 2014-03-09
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


[h=2]2nd option : install Boot-Repair in Ubuntu[/h] - [boot your computer on a Ubuntu live-CD or live-USB.]("https://help.ubuntu.com/community/BootFromCD") 
- choose "Try Ubuntu" 
- connect to the Internet 
- open a new [Terminal]("https://help.ubuntu.com/community/Terminal"), then type: 
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update- Press ENTER. 
- Then type: 
sudo apt-get install -y boot-repair && (boot-repair &)- Press ENTER 
 
[h=1]Using Boot-Repair[/h]  
[h=2]Recommended repair[/h] 
[LIST]
[*]launch Boot-Repair from either : 
[LIST]
[*]the Dash (the Ubuntu logo at the top-left of the screen) 
[*]or System->Administration->Boot-Repair menu (Ubuntu 10.04 only) 

[*]or by typing 'boot-repair' in a terminal 
[/LIST]

[*]Then click the "Recommended repair" button. When repair is finished, note the URL (**paste.ubuntu.com/XXXXX**) that appeared on a paper, then reboot and check if you recovered access to your OSs.  

[*]If the repair did not succeed, indicate the URL to people who help you by email or forum.
[/LIST]

---

### Post by oldfred on 2014-03-09
You installed wubi which does not use grub to boot but uses the Windows boot loader. After booting with Windows it will show a grub menu like a full install, but you cannot dual boot to Windows from that.

Because you installed grub you created another /boot partition. Windows is not case sensitive like Linux so you cannot have two partition like this /boot and /Boot as they are seen as the same and will conflict. You want to keep the one with BCD and delete the one with grub.

From your sda2 partition.
       Boot files: /bootmgr [COLOR=#ff0000]/Boot/BCD[/COLOR] /Windows/System32/winload.exe
/wubildr /wubildr.mbr [COLOR=#ff0000]/boot/grub/core.img[/COLOR]

Use Windows or Boot-Repair to install Windows boot loaders to sda & sdb.

---

