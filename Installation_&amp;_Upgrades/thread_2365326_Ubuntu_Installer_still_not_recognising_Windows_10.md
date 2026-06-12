---
title: "Ubuntu Installer still not recognising Windows 10"
date: 2017-07-05
forum: Installation &amp; Upgrades
---

### Post by philonous79 on 2017-07-05
I would be very grateful for help installing Ubuntu 17.04 alongside Windows 10. 

At the moment the installer does not give me the option to install Ubuntu alongside an existing Windows 10 installation. I have searched the forums and have already done the following:

1. Turned off quick start (and quick launch)
2. Turned off hibernation
3. Set the laptop to UEFI with legacy boot
4. Turned off secure boot
5. Run chkdsk at boot and restarted (twice)

I have also installed Ubuntu using 'something else', creating root, swap, and home partitions. The USB stick with the install media is GPT / UEFI bootable. However, the computer still boots into Windows and none of the boot menu options allows me to boot into Ubuntu. The computer is a Dell Latitude 7370, if that is relevant.

Many thanks in advance!

---

### Post by ajgreeny on 2017-07-05
I am not sure what exactly you mean by
**3. Set the laptop to UEFI with legacy boot.**

If this is a UEFI system you may do better to choose either UEFI or legacy BIOS, not the hybrid manner that I think you may have chosen.

However, it is important that both OSs are using the same manner, ie, both UEFI or both legacy BIOS, so if Windows 10 is UEFI your Ubuntu must also use UEFI.

So we can be sure of the current situation see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by yancek on 2017-07-05
Check the official Ubuntu documentation at the site below and compare what is explained to what you did.  You need to boot and install UEFi if you have windows 10 UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by philonous79 on 2017-07-05
Thanks to both of you! I'll investigate tomorrow and write back with answers to your questions.

---

### Post by philonous79 on 2017-07-06
Ajgreeny, thanks again for your suggestions! My computer was set to UEFI, but with the 'Enable Legacy Option ROMs' ticked. I unticked that option and booted into the installer again. Unfortunately, the Windows installation was still not recognised.

I then installed and ran the Boot-Repair program as suggested. At the end I chose the paste bin option, but the URL produced can't (I assume) be correct: [http://paste2.org/](http://paste2.org/) . There was, however, an error message in Terminal to the effect that I need to specify the version of Gtk, Notify and AppIndicator3 for the import. I'm afraid I don't know how to do this. 

Thanks again.

---

### Post by philonous79 on 2017-07-06
Update: I've now created a bootable Boot-Repair Disk. As it doesn't seem to be able to work with my wireless card, and since I have no Ethernet port, I can't post the URL. However, I have copied the .txt file into the Windows partition. Unfortunately, I can't seem to attach it in this forum (I get an error sign when I try to upload the file in the Attachments dialogue box) and so I'll copy the full text into a post. My apologies if this is that's not the right thing to do!

---

### Post by philonous79 on 2017-07-06
```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]



============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


/dev/sda1 ends after the last sector of /dev/sda


GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048 1,953,525,134 1,953,523,087 Data partition (Windows/Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/nvme0n1p1   9ABB-3B74                              vfat       SYSTEM
/dev/nvme0n1p3   6E92CB0F92CADB2B                       ntfs       
/dev/nvme0n1p4   C488BC2488BC16C0                       ntfs       Windows RE tools
/dev/nvme0n1p5   a9f2e342-3056-4732-a757-cc2151d7e9cd   swap       
/dev/nvme0n1p6   8541d70b-ec06-4649-8e33-d867d4241370   ext4       
/dev/nvme0n1p7   35789fa6-eca2-4a80-9f8a-745313edf385   ext4       
/dev/sda1        171A-2A0D                              vfat       BOOT-REPAIR
/dev/zram0       0cef691e-8822-4a90-bd4c-2afbfc5b59a6   swap       
/dev/zram1       f68721e7-3865-4d60-9340-9a6ddf043643   swap       
/dev/zram2       9c103fbe-db32-4b5d-b368-66a439e1ab1d   swap       
/dev/zram3       9e6ed1a2-3b33-487d-a8aa-fba1bfa8cc4e   swap       


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Jul  6 16:01 ata-TOSHIBA_MQ01UBD100_24GBT6JAT -> ../../sda
lrwxrwxrwx 1 root root 10 Jul  6 15:59 ata-TOSHIBA_MQ01UBD100_24GBT6JAT-part1 -> ../../sda1


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)



=========================== sda1/boot/grub/grub.cfg: ===========================


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


menuentry "Boot-Repair-Disk session" {
 set gfxpayload=keep
 linux /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
 initrd /casper/initrd.lz
}
--------------------------------------------------------------------------------


============================== sda1/syslinux.cfg: ==============================


--------------------------------------------------------------------------------
DEFAULT loadconfig


LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------


=============================== StdErr Messages: ===============================


File descriptor 9 (/proc/10745/mounts) leaked on lvs invocation. Parent PID 17392: bash
File descriptor 63 (pipe:[34847]) leaked on lvs invocation. Parent PID 17392: bash
  No volume groups found


ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-07-06__16h01 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/10745/mounts) leaked on lvs invocation. Parent PID 12278: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
mount: wrong fs type, bad option, bad superblock on /dev/nvme0n1p6,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so


mount /dev/nvme0n1p6 : Error code 32
mount -r /dev/nvme0n1p6 /mnt/boot-sav/nvme0n1p6
mount: wrong fs type, bad option, bad superblock on /dev/nvme0n1p6,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so


mount -r /dev/nvme0n1p6 : Error code 32
mount: wrong fs type, bad option, bad superblock on /dev/nvme0n1p7,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so


mount /dev/nvme0n1p7 : Error code 32
mount -r /dev/nvme0n1p7 /mnt/boot-sav/nvme0n1p7
mount: wrong fs type, bad option, bad superblock on /dev/nvme0n1p7,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so


mount -r /dev/nvme0n1p7 : Error code 32


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.



=================== os-prober:
/dev/nvme0n1p6:Ubuntu 17.04 (17.04):Ubuntu:linux


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/nvme0n1p1: LABEL="SYSTEM" UUID="9ABB-3B74" TYPE="vfat"
/dev/nvme0n1p3: UUID="6E92CB0F92CADB2B" TYPE="ntfs"
/dev/nvme0n1p4: LABEL="Windows RE tools" UUID="C488BC2488BC16C0" TYPE="ntfs"
/dev/nvme0n1p5: UUID="a9f2e342-3056-4732-a757-cc2151d7e9cd" TYPE="swap"
/dev/nvme0n1p6: UUID="8541d70b-ec06-4649-8e33-d867d4241370" TYPE="ext4"
/dev/nvme0n1p7: UUID="35789fa6-eca2-4a80-9f8a-745313edf385" TYPE="ext4"
/dev/sda1: LABEL="BOOT-REPAIR" UUID="171A-2A0D" TYPE="vfat"
/dev/zram0: UUID="0cef691e-8822-4a90-bd4c-2afbfc5b59a6" TYPE="swap"
/dev/zram1: UUID="f68721e7-3865-4d60-9340-9a6ddf043643" TYPE="swap"
/dev/zram2: UUID="9c103fbe-db32-4b5d-b368-66a439e1ab1d" TYPE="swap"
/dev/zram3: UUID="9e6ed1a2-3b33-487d-a8aa-fba1bfa8cc4e" TYPE="swap"



1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


mount: wrong fs type, bad option, bad superblock on /dev/nvme0n1p6,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so


mount /dev/nvme0n1p6 : Error code 32
mount -r /dev/nvme0n1p6 /mnt/boot-sav/nvme0n1p6
mount: wrong fs type, bad option, bad superblock on /dev/nvme0n1p6,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so


mount -r /dev/nvme0n1p6 : Error code 32
mount: wrong fs type, bad option, bad superblock on /dev/nvme0n1p7,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so


mount /dev/nvme0n1p7 : Error code 32
mount -r /dev/nvme0n1p7 /mnt/boot-sav/nvme0n1p7
mount: wrong fs type, bad option, bad superblock on /dev/nvme0n1p7,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so


mount -r /dev/nvme0n1p7 : Error code 32
Windows not detected by os-prober on nvme0n1p3.


WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util sfdisk doesn't support GPT. Use GNU Parted.



WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util fdisk doesn't support GPT. Use GNU Parted.


Presence of EFI/Microsoft file detected: /mnt/boot-sav/nvme0n1p1/EFI/Microsoft/Boot/bootmgfw_.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/nvme0n1p1/EFI/Boot/bootx64.efi


efibootmgr -v
BootCurrent: 000B
Timeout: 2 seconds
BootOrder: 0001,0009,000B
Boot0001* Windows Boot Manager HD(1,800,32000,766dc9b5-5272-42d6-b030-005e36be56fc)File(EFIubuntugrubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0009* UEFI: PM951 NVMe SAMSUNG 256GB, Partition 1 HD(1,800,32000,766dc9b5-5272-42d6-b030-005e36be56fc)File(EFIbootbootx64.efi)..BO
Boot000B* UEFI: TOSHIBA External USB 3.00, Partition 1 ACPI(a0341d0,0)PCI(14,0)USB(c,0)HD(1,800,7470658f,ae493de1-0abc-489f-985e-8a0f5cd0d1a8)..BO
BootFFF6* BiosConnect           Vendor(5990c250-676b-4ff7-8a0d-529319d0b254,)
BootFFF7* Fix my Dell           Vendor(5990c250-676b-4ff7-8a0d-529319d0b254,)
BootFFF8* Fix my Dell           Vendor(5990c250-676b-4ff7-8a0d-529319d0b254,)
BootFFFB* Diagnostic Boot       Vendor(5990c250-676b-4ff7-8a0d-529319d0b254,)
BootFFFC* Temporary Boot Menu   Vendor(5990c250-676b-4ff7-8a0d-529319d0b254,)
BootFFFD* Graphic Setup         Vendor(5990c250-676b-4ff7-8a0d-529319d0b254,)
BootFFFE* Text Setup            Vendor(5990c250-676b-4ff7-8a0d-529319d0b254,)
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [email]boot.repair@gmail.com[/email]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])



=================== PARTITIONS & DISKS:
nvme0n1p1 : nvme0n1, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, no-os, is-correct-EFI, part-has-no-fstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, not-far, /mnt/boot-sav/nvme0n1p1.
nvme0n1p3 : nvme0n1, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, is-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, haswinload, no-recov-nor-hid, bootmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, farbios, /mnt/boot-sav/nvme0n1p3.
nvme0n1p4 : nvme0n1, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, no-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, no-winload, recovery-or-hidden, no-bmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, farbios, /mnt/boot-sav/nvme0n1p4.
nvme0n1p6 : nvme0n1, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, is-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, farbios, /mnt/boot-sav/nvme0n1p6.
nvme0n1p7 : nvme0n1, maybesepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, no-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, farbios, /mnt/boot-sav/nvme0n1p7.


nvme0n1 : GPT, no-BIOS_boot, has-correctEFI,  not-usb, has-os, 2048 sectors * 512 bytes



=================== parted -l:


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                  Flags
1      1049kB  1000GB  1000GB  fat32        Microsoft Basic Data  msftdata



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


Model: Unknown (unknown)
Disk /dev/nvme0n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End    Size    File system     Name                          Flags
1      1049kB  106MB  105MB   fat32           EFI system partition          boot
2      106MB   123MB  16.8MB                  Microsoft reserved partition  msftres
3      123MB   169GB  169GB   ntfs            Basic data partition          msftdata
7      169GB   230GB  61.3GB  ext4
6      230GB   250GB  20.0GB  ext4
5      250GB   254GB  4096MB  linux-swap(v1)
4      254GB   256GB  1887MB  ntfs            Basic data partition          hidden, diag


=================== parted -lm:


BYT;
/dev/sda:1000GB:scsi:512:512:gpt:TOSHIBA External USB 3.0;
1:1049kB:1000GB:1000GB:fat32:Microsoft Basic Data:msftdata;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


BYT;
/dev/nvme0n1:256GB:unknown:512:512:gpt:Unknown;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:169GB:169GB:ntfs:Basic data partition:msftdata;
7:169GB:230GB:61.3GB:ext4::;
6:230GB:250GB:20.0GB:ext4::;
5:250GB:254GB:4096MB:linux-swap(v1)::;
4:254GB:256GB:1887MB:ntfs:Basic data partition:hidden, diag;



=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/nvme0n1p1 on /mnt/boot-sav/nvme0n1p1 type vfat (rw)
/dev/nvme0n1p3 on /mnt/boot-sav/nvme0n1p3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/nvme0n1p4 on /mnt/boot-sav/nvme0n1p4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)



=================== ls:
/sys/block/nvme0n1 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 nvme0n1p6 nvme0n1p7 power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdc-wdm0 char console core cpu cpu_dma_latency cuse disk ecryptfs fb0 fd full fuse hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null nvme0 nvme0n1 nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 nvme0n1p6 nvme0n1p7 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sg0 shm snapshot snd stderr stdin stdout tpm0 uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control
ls /mnt/boot-sav/nvme0n1p1/1:
ls /mnt/boot-sav/nvme0n1p1: EFI
Temp  . Please report this message to [email]boot.repair@gmail.com[/email]


=================== hexdump -n512 -C /dev/nvme0n1p1
00000000  eb 63 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.c.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 74 3b bb 9a 4e  4f 20 4e 41 4d 45 20 20  |..)t;..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 00 80 50 93 56 1c  |  FAT32   ..P.V.|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  f6 07 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |...t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..|f..f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f...D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d 5a 84 d2 0f  |...p.v....s.Z...|
000000f0  83 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  ff 0d 0a 50 72 65 73 73  |...<.u.....Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/nvme0n1p3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 03 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 57 a3 13 00 00 00 00  |.........W......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  2b db ca 92 0f cb 92 6e  |........+......n|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/nvme0n1p4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 f0 96 1d  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 3f 38 00 00 00 00 00  |.........?8.....|
00000030  00 58 02 00 00 00 00 00  02 00 00 00 00 00 00 00  |.X..............|
00000040  f6 00 00 00 01 00 00 00  c0 16 bc 88 24 bc 88 c4  |............$...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.



=================== df -Th:


Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G   33M  3.9G   1% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      788M  1.3M  787M   1% /run
/dev/sda1      vfat       932G  626M  931G   1% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G   44K  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G     0  3.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/nvme0n1p1 vfat        96M   29M   68M  31% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3 fuseblk    158G   44G  115G  28% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4 fuseblk    1.8G  592M  1.2G  33% /mnt/boot-sav/nvme0n1p4


=================== fdisk -l:


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT



No OS or WinEFI system



=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems  fix-windows-boot



=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2017-07-06
Please use Code Tags if longer terminal or text output.
Easy to add with Forum's advanced Editor and # icon.

Would you please add to Boot-Repair bug and include the error messages you got. I did not get any error messages when I created bug report. Those will help Yann fix issue.
[https://bugs.launchpad.net/boot-repair/+bug/1692778](https://bugs.launchpad.net/boot-repair/+bug/1692778)

Every system except perhaps Dell seems to have UEFI and CSM/BIOS/Legacy as one or the other. Some have posted with Dell that you often need to keep legacy setting on, but still select UEFI.
My desktop (not Dell) has to have 'UEFI only' as boot option. Even the setting 'UEFI or BIOS' only boots in BIOS mode. Or sometimes you just have to experiment, but always have good backups in case experiments go awry. 

You show the new NVMe drives.
Have you updated UEFI/BIOS and NVMe firmware?

Issues are often common by brand as same or similar UEFI/BIOS usually used. So these may help even if not your model.
       Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[URL="https://ubuntuforums.org/showthread.php?t=2345444"]https://ubuntuforums.org/showthread.php?t=2345444
[/URL]
 Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN) 

[URL="https://ubuntuforums.org/showthread.php?t=2345444"]
[/URL]

---

