---
title: "SATA not detected during install"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by KaibutsuX on 2010-12-22
I recently built a new system, hoping that a new SATA chip would be better supported by Ubuntu as I've had this problem ever since Hardy. When running the LiveCD from both Lucid and Maverick in either the 32 or 64 install disks, my drives show up in Gparted, but NOT in the allocate drive space window of the installer.

I have two SATA drives, one 400G and one 1TB drive. I believe the 400 is 1.5Gb/s and the 1TB is 3Gb/s but I'm not sure. I know neither are SATA6.

When I run the installer using F6, I get no drives showing up. When I boot into the LiveCD, I can see the drives in Gparted, I can mount them and browse them, but when I double click the installer icon, I get absolutely nothing in the partition manager window. Essentially I cannot, nor have I been able to  install either 32 or 64-bit linux ever since Hardy.

It's starting to get a little ridiculous that I'm having this much trouble just getting the installer to recognize two fairly common drives.
Here is what I have tried:
pci=nomsi
noapic
nolapic
nodmraid
The acpi=off option from the F6 menu.

I have done all of the above in every possible permutation with single options, combined with multiple options. I have also gone in to the bios changing my SATA mode to enhanced, AHCI, IDE, RAID. I have disabled the Marvell Raid controller, I have set it to AHCI mode. I have done all of these bios settings in conjunction with the F6 options and I still get nothing in the installer window. However no matter what, the LiveCD always works just fine.

I have reset the bios to factory settings and tried again from there.
I have Windows7 currently installed on one drive (but it doesn't matter, it doesnt recognize on even a blank drive) and I have used windows to create a separate 150GB partition on the 400GB drive. I left it untouched, unformatted and got nothing. I formatted the new 150GB partition to ext3 and still nothing.

Here is the output of what you're going to ask next:
lspci - 
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 VGA compatible controller: nVidia Corporation G96 [Quadro FX 580] (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
07:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
ubuntu@ubuntu:~$ 

dmesg | grep sd
[    3.223393] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.225435] sd 0:0:0:0: [sda] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    3.246647] sd 0:0:0:0: [sda] Write Protect is off
[    3.246650] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.248909] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.249039] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    3.249114] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.249169] sd 1:0:0:0: [sdb] Write Protect is off
[    3.249171] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.249180]  sda:
[    3.249242] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.249323]  sdb: sdb1
[    3.255302] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.259289]  sda1 sda2 sda3
[    3.259449] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.469797] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    4.470084] sd 4:0:0:1: Attached scsi generic sg4 type 0
[    4.470369] sd 4:0:0:2: Attached scsi generic sg5 type 0
[    4.470656] sd 4:0:0:3: Attached scsi generic sg6 type 0
[    4.480518] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    4.481143] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    4.482017] sd 4:0:0:2: [sde] Attached SCSI removable disk
[    4.482641] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[    4.607811] sd 5:0:0:0: Attached scsi generic sg7 type 0
[    4.609579] sd 5:0:0:0: [sdg] 7892040 512-byte logical blocks: (4.04 GB/3.76 GiB)
[    4.610076] sd 5:0:0:0: [sdg] Write Protect is off
[    4.610078] sd 5:0:0:0: [sdg] Mode Sense: 00 00 00 00
[    4.610079] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[    4.613074] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[    4.613077]  sdg: sdg1
[    4.752516] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[    4.752519] sd 5:0:0:0: [sdg] Attached SCSI removable disk
[    5.274291] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)

sudo fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24aa43b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       29009   232910848    7  HPFS/NTFS
/dev/sda3           29010       48641   157694040   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ab54b32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdg: 4040 MB, 4040724480 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f218b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        1018     3944719    c  W95 FAT32 (LBA)

I am running in a liveCD right now from a USB drive (tried from CD too, but constantly rebooting is faster from this USB)

If anyone has any ideas, I would love to hear them. I'm out of options and ideas, I work from home often and I use linux, but if I am unable to install it (I'm not doing wubi) I will simply switch to another distro. I can't believe that this is still a problem after so long and not even a new motherboard (and complete new system) has not made a difference. You would think that even just one hard drive might be visible, but I'm getting nothing.

---

### Post by Quackers on 2010-12-22
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by KaibutsuX on 2010-12-23
The 1TB disk in question is this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185)

Since Ubuntu has never recognized either of my drives since Hardy in two completely different systems, I doubt it has anything to do with my current configuration. The only thing in common between systems is Intel brand cpu, Asus brand motherboard and the same hard drives.

I'm not going to reboot into a live cd to download a third party shell script. If you need more information than lspci, fdisk and dmesg, then please ask.

---

### Post by oldfred on 2010-12-23
With a very new system, I am suspicious of a BIOS setting or two.

I have saved some comments where users did fix boot issues. See if any of these may apply:

Some issues on booting install:
BIOS settings need USB mouse & keyboard
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
BIOS should be set for IDE compatibility mode
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)

---

### Post by KaibutsuX on 2010-12-23
Thanks for the reply, as far as I can tell, I have tried everything in that list. I've tried every possible combination of the IDE/RAID/AHCI settings.

For what it's worth, I am pretty sure that this is a command-line option. I actually got it to install ONE time using some combination of the pci=nomsi command line parameter and I think the apic=off F6 option, but of course I didn't write it down and I've tried everything I can think of but can't get it to recognize again.

Regardless, I don't think we should think of this as a boot issue. LiveCD boots just fine. Linux just will not install. I can see my drives in the livecd, they work perfectly. But when I double click on the install icon, I get 0 drives in the list. Whether I do it from the icon for command line from the install cd, no drives showing up.

---

### Post by oldfred on 2010-12-23
If you turned RAID on then you may have written RAID meta data to the drives that can interfere with a normal desktop install. 

I still think some of the BIOS settings like LBA or if you plugged into the 6GB/s ports.

Boot script will show if drives can be seen at all, and if RAID meta data is on drive.

---

### Post by KaibutsuX on 2010-12-23
Results of bootscript.......
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/mapper/pdc_djgfddjd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdg1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdg1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

pdc_djgfddjd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   466,028,543   465,821,696   7 HPFS/NTFS
/dev/sda3         466,029,585   781,417,664   315,388,080  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 4040 MB, 4040724480 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7892040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             62     7,889,499     7,889,438   c W95 FAT32 (LBA)


Drive: pdc_djgfddjd ___________________ _____________________________________________________

Disk /dev/mapper/pdc_djgfddjd: 1000.2 GB, 1000204795904 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953524992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_djgfddjd1                 63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_djgfddjd1 A4289C2F289BFF0C                       ntfs       Storage                       
/dev/mapper/pdc_djgfddjd: PTTYPE="dos" 
/dev/sda1        8A164E89164E766B                       ntfs       System Reserved               
/dev/sda2        CAB651CAB651B7A1                       ntfs                                     
/dev/sda3        399c41dd-2317-4b77-b89f-6c0b8389c900   ext4       Linux                         
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        A4289C2F289BFF0C                       ntfs       Storage                       
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdg1        6E3F-2F19                              vfat                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdg1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdg1/boot/grub/grub.cfg: ===========================


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

=================== sdg1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

---

### Post by oldfred on 2010-12-23
Even script had trouble with sdb, but it shows mapper in sda? Are you running RAID or LVM logical Volume Management? 

If not running raid or LVM:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by KaibutsuX on 2010-12-24
Sudo apt-get remove dmraid
ill write this down for future reference, but this means ill always need to install from a live cd unless someone knows how to achieve this from cmd line without first booting into the livecd?

---

### Post by oldfred on 2010-12-24
The liveCD did not used to have RAID drivers, just the alternative installer which is also used for servers. But I think they now include something, so you can use liveCD and make the changes before you install. You just need to get to a command line. Not sure if any of the boot parameters under F6 relate or not. Have not looked lately.

---

### Post by psusi on 2010-12-24
You do not need to uninstall dmraid, you need to remove the raid signatures from the disk with dmraid -E, or your bios raid utility.

---

### Post by Quackers on 2010-12-24
Or
```
sudo dmraid -rE /dev/sdX
```
where X is the disk designation (sda, sdb etc)

---

### Post by dino99 on 2010-12-24
have had similar hard times with a marvel chip on an older card (ich7r) and a pata sata mix.

i finally found the way:
- set to ahci mode (or compatible if that choice exist)
- check your hdds status (master/slave) & the MB doc
- try different plug/order scheme (primary/secondary) place(s)

---

