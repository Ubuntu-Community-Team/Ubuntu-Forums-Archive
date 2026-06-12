---
title: "Installed..Stuck at &quot;Loading Operating System...&quot;"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by fisaacs on 2011-03-24
Coming back to linux from a long time (4+ years since any regular use) away.

Installed 10.10 just fine on my macbook pro 1.1 after some finagling with the text-based installer.

Now I'm doing it on my desktop (custom built gaming rig, Gigabyte 870A-UD3 motherboard, raid on 2 drives and a 200gig sata drive where I installed ubuntu on 3 partitions (/, /home, swap)

I didn't set the raid up myself and tbh I don't know my butt from a hole in the ground when it comes to raid, other than that its g-raid for the controller in bios and the 2 drives are striping.

I told the ubuntu installer to put the bootloader in the small partition of the raid array that precedes the actual data partitions.  install appeared to go fine,but when I boot, all I get is a black screen with terminal text saying "Loadig Operating System..." and a blinking cursor.

I cannot, under any circumstance wipe the win7 raid partition and computer didn't ship with a win7 disk.  I'd like to recover both the ubuntu install and win7 install, but can reinstall ubuntu as needed.

Going to try reinstalling ubuntu to the 200gb drive and setting it as the primary boot drive in bios just to get booting, then figure out how to tell grub to get into win7  any advice/assistance is appreciated in advance.

[UPDATE]
I switched up the primary boot drive in BIOS and got my ubuntu installation up and running, but now I just need to add the windows 7 raid installation to GRUB2  Any tutorials on this out there?

---

### Post by fisaacs on 2011-03-24
Ok, So I got grub to boot to my raid array and hit 2 different problems.

on hd1,1 (presumably where the old windows bootloader was) I went straight to a blinking cursor
on hd1,2 (presumably the main raid array) I got "Boot MGR Missing"

I'm guessing I have to restore the windows bootloader to the old partition?  Any way to do this via linux?

---

### Post by fisaacs on 2011-03-25
BUMP. I still cant get the windows system booted back up and have now managed to break the ubuntu installation due to trying tobfix the windows drive mbr.  Does anyone have any idea of what i cam do or should i just boot an ubuntu live disc backup the contents of my raid and reinstall?

---

### Post by Rubi1200 on 2011-03-25
Hi,

you might want to do the following so we can get a better overview of the current state of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by fisaacs on 2011-03-25
OK, here goes...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/mapper/jmicron_GRAID

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

jmicron_GRAID1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of 
                       jmicron_GRAID1 and looks at sector 22080304 of the 
                       same hard drive for core.img, but core.img can not be 
                       found at this location. No errors found in the Boot 
                       Parameter Block.
    Mounting failed:
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

jmicron_GRAID2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.0 GB, 16039018496 bytes
64 heads, 32 sectors/track, 15296 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32    31,326,207    31,326,176   c W95 FAT32 (LBA)


Drive: jmicron_GRAID ___________________ _____________________________________________________

Disk /dev/mapper/jmicron_GRAID: 2000.4 GB, 2000381018112 bytes
255 heads, 63 sectors/track, 243199 cylinders, total 3906994176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/jmicron_GRAID1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/jmicron_GRAID2            206,848 3,906,992,127 3,906,785,280   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       added052-304a-bd4d-b730-e8fdc14be7eb   ext2       casper-rw                     
/dev/mapper/jmicron_GRAID1 609487219486F8B4                       ntfs       System Reserved               
/dev/mapper/jmicron_GRAID2 146A8B296A8B06A8                       ntfs                                     
/dev/mapper/jmicron_GRAID: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                jmicron_raid_member                               
/dev/sdc                                                jmicron_raid_member                               
/dev/sdd1        19DD-1225                              vfat       PENDRIVE                      
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
jmicron_GRAID
jmicron_GRAID1
jmicron_GRAID2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
aufs             /                        aufs       (rw,noatime,si=19c8252b)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /casper-rw-backing       vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop1       /cow                     ext2       (rw,noatime,errors=continue)


=========================== sdd1/boot/grub/grub.cfg: ===========================


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

=================== sdd1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 ff dd 01 45 77 00 00  00 00 00 00 02 00 00 00  |....Ew..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 25 12 dd 19 4e  4f 20 4e 41 4d 45 20 20  |..)%...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 b2  ee 00 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
```

---

### Post by Rubi1200 on 2011-03-25
Thanks for posting the output here.

I am no expert on RAID installs, but I will pass this information on to forum member ronparent who I hope will have an answer for you.

Meantime, please be patient and wait for his response before you make any more changes.

Thanks.

---

### Post by ronparent on 2011-03-25
> Meantime, please be patient and wait for his response before you make any more changes.
Good advice. You seem to have made a number of inadvised changes that may have damaged win 7 to the point that it will have to be fixed.

Your best move still seems to be installing Ubuntu to the separate 200Mb drive. I don't see that drive or the Ubuntu installation? Do you know how to change the boot order in the bios of your system?

I suggest proceeding as follows. 1) Unplug your two raid drives and verify that the boot order in bios will boot to the 200Mb drive. Apparently the install image is on a key. 2) Insert that key and boot on it. Use it to install Ubuntu to the 200Mb drive drive. Now at least you will have a complete bootable system barring any system specific boot problems. 3) Boot to the new install and install dmraid and gparted to that new system. 4) Now replug the raid drives and verify that the 200 Mb drive remains 1st ib the bios boot order. 5) Boot into your Ubuntu and verify that the ntfs file systems are intact. Your NTFS win directories hould now be visible and mountable. 6) open a terminal window and run '**sudo grub-update**' If the win7 system is bootable it will be picked up in the grub menu and will be available on the next reboot.

I suspect from what you described that win7 will have to be recovered. That is unavoidable at this point and will be difficult without a win 7 installation disk. If the file system is still readable you will be able to back up or recover any of your files with Ubuntu. Post what you do find. I'm sure that someone can help with the Ubuntu aspects. And some of our posters might be able to help with windows as well. Good luck.

---

### Post by fisaacs on 2011-03-27
Thanks for all the advice.

Got ubuntu back on the 200gb drive. (windows recovery cd had messed up the mbr and the usb stick I was using was doing something funky so I did a CD install.

Ubuntu does allow me to get in and view/copy my windows files so they're at least recoverable if I have to do a full reinstall.

Unfortunately the contents of my raid array are too big to fit the 200gb drive, so I'm going to have to get something bigger.

In light of this I've decided I'm going to do the following: (and research the process for this more and possibly open a new thread to iron out how I'm going to do it.)

1. Upgrade 200gb drive to a 2tb drive (to match size of Raid Array) use this for win backups / possible dedicated storage of my media if I decide to keep linux up 90+% of the time which is my intent.
2. Dual-boot install of Windows and Ubuntu off of the raid array.
(went ahead and ordered a windows disk in light of the issues already caused by PC builder not shipping system with one.)

---

