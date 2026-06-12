---
title: "New &quot;simple&quot; installation issue (24.04)"
date: 2024-09-04
forum: Installation &amp; Upgrades
---

### Post by pierrelcv on 2024-09-04
Hello,
I've just bought a new PC (Dell, Vostro) on which Windows 10 was installed and on which I'd like to have Ubuntu 24.04 only (so the situation is pretty straightforward). I set about installing Ubuntu and, despite a small problem with Intel Rapid Storage on the first attempt (which was quickly resolved by switching to AHCI mode in the BIOS), everything went smoothly. I got rid of Windows and all that's left is the freshly installed Ubuntu. Alas, I messed up the password by using a special character that means I can't log in once the system is installed... Anyway, it doesn't matter, it happened to me on another PC, so I reinstalled (the first installation took 10min...) and changed the password. Unfortunately, I couldn't finish installing (or rather reinstalling...) Ubuntu. Everything's going fine right up to the end, which never ends - no apparent error message, just an installation that hangs. I'll give you a few screenshots afterwards, but I've tried three more times and it's still stuck at the same point. Looking at the commands diagonally, I have the impression that it crashes when installing Grub, see just after the last commands :
[IMG]https://i.ibb.co/N2zf94k/20240902-213821.jpg[/IMG]

[IMG]https://i.ibb.co/bJbmNW6/20240902-213500.jpg[/IMG]

Consequently, after that I have tried to repair the boot with boot-repair with a live usb key but it was not working (the process never end and blocked on the following window) :
[IMG]https://i.ibb.co/VmJfq4S/Screenshot-from-2024-09-03-19-17-11.png[/IMG]
Consequently, I have tried to use "boot-repair-disk" ([https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)) and it worked ! See just after :
[IMG]https://i.ibb.co/71npqT7/image.png[/IMG]

After that I have tried to install again (I reall thought that it would work !) but no change !!! The installation process is stucked at the same position (see previous screenshots). Argh !!!!
That's very annoying as I think that my case is very simple (no dual boot, no data to save) I just want to install Ubuntu on the entire hard disk... 

Any idea to fix this issue ?

THANK YOU !!
Pierre

---

### Post by oldfred on 2024-09-04
Are you not able to get Summary Report from Boot-Repair?
May be a corrupted partition.
Does gparted from live installer show partitions and then any with yellow or red icons indicating error of some sort? Click (right click?) on icon for more info.
May need dosfsck on ESP - efi system partition or fsck on ext4 partition(s).
man dosfsck
sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sdXY # where X is drive and Y is partition.
sudo fsck.vfat -t -a /dev/nvme0n1pY # where Y is ESP partition.

---

### Post by pierrelcv on 2024-09-04
Dear oldfred,
I thought that you had access to the report, my bad ! :). Please find just after the complete report :
```

boot-repair-4ppa2074                                              [20240903_2015]

============================= Boot Repair Summary ==============================






Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p2,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file


/boot/efi added in nvme0n1p2/fstab
Mount /dev/nvme0n1p1 on /mnt/boot-sav/nvme0n1p2/boot/efi
No nvme0n1p2/boot/efi/efi/ ubuntu/mint folder

Unhide GRUB boot menu in nvme0n1p2/etc/default/grub

=================== Reinstall the grub-efi of /dev/nvme0n1p2 ===================

chroot /mnt/boot-sav/nvme0n1p2 grub-install --version
grub-install (GRUB) 2.12-1ubuntu7
modprobe: FATAL: Module efivars not found in directory /lib/modules/5.15.0-76-generic
chroot /mnt/boot-sav/nvme0n1p2 modprobe efivars

chroot /mnt/boot-sav/nvme0n1p2 efibootmgr -v before grub install
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,0002
Boot0000* Windows Boot Manager    HD(1,GPT,4db84b79-da95-4bb4-b03a-b8e4eec41187,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000043000100000010000000040000007fff0400
dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 20 03 00 00 00 00 00 79 4b b8 4d 95 da b4 4b b0 3a b8 e4 ee c4 11 87 02 02 / 04 04 46 00 5c 00 45 00 46 00 49 00 5c 00 4d 00 69 00 63 00 72 00 6f 00 73 00 6f 00 66 00 74 00 5c 00 42 00 6f 00 6f 00 74 00 5c 00 62 00 6f 00 6f 00 74 00 6d 00 67 00 66 00 77 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
data: 57 49 4e 44 4f 57 53 00 01 00 00 00 88 00 00 00 78 00 00 00 42 00 43 00 44 00 4f 00 42 00 4a 00 45 00 43 00 54 00 3d 00 7b 00 39 00 64 00 65 00 61 00 38 00 36 00 32 00 63 00 2d 00 35 00 63 00 64 00 64 00 2d 00 34 00 65 00 37 00 30 00 2d 00 61 00 63 00 63 00 31 00 2d 00 66 00 33 00 32 00 62 00 33 00 34 00 34 00 64 00 34 00 37 00 39 00 35 00 7d 00 00 00 43 00 01 00 00 00 10 00 00 00 04 00 00 00 7f ff 04 00
Boot0001* UEFI: General UDisk 5.00    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/CDROM(1,0x23c,0x84c0)0000424f
dp: 02 01 0c 00 d0 41 03 0a 00 00 00 00 / 01 01 06 00 00 14 / 03 05 06 00 00 00 / 04 02 18 00 01 00 00 00 3c 02 00 00 00 00 00 00 c0 84 00 00 00 00 00 00 / 7f ff 04 00
data: 00 00 42 4f
Boot0002* UEFI: General UDisk 5.00, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,MBR,0x14eb2669,0x23c,0x2130)0000424f
dp: 02 01 0c 00 d0 41 03 0a 00 00 00 00 / 01 01 06 00 00 14 / 03 05 06 00 00 00 / 04 01 2a 00 02 00 00 00 3c 02 00 00 00 00 00 00 30 21 00 00 00 00 00 00 69 26 eb 14 00 00 00 00 00 00 00 00 00 00 00 00 01 01 / 7f ff 04 00
data: 00 00 42 4f

chroot /mnt/boot-sav/nvme0n1p2 uname -r
5.15.0-76-generic

chroot /mnt/boot-sav/nvme0n1p2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/nvme0n1p1
mv /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/nvme0n1p2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme0n1p2 efibootmgr -v after grub install
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,0002
Boot0000* Windows Boot Manager    HD(1,GPT,4db84b79-da95-4bb4-b03a-b8e4eec41187,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000043000100000010000000040000007fff0400
dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 20 03 00 00 00 00 00 79 4b b8 4d 95 da b4 4b b0 3a b8 e4 ee c4 11 87 02 02 / 04 04 46 00 5c 00 45 00 46 00 49 00 5c 00 4d 00 69 00 63 00 72 00 6f 00 73 00 6f 00 66 00 74 00 5c 00 42 00 6f 00 6f 00 74 00 5c 00 62 00 6f 00 6f 00 74 00 6d 00 67 00 66 00 77 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
data: 57 49 4e 44 4f 57 53 00 01 00 00 00 88 00 00 00 78 00 00 00 42 00 43 00 44 00 4f 00 42 00 4a 00 45 00 43 00 54 00 3d 00 7b 00 39 00 64 00 65 00 61 00 38 00 36 00 32 00 63 00 2d 00 35 00 63 00 64 00 64 00 2d 00 34 00 65 00 37 00 30 00 2d 00 61 00 63 00 63 00 31 00 2d 00 66 00 33 00 32 00 62 00 33 00 34 00 34 00 64 00 34 00 37 00 39 00 35 00 7d 00 00 00 43 00 01 00 00 00 10 00 00 00 04 00 00 00 7f ff 04 00
Boot0001* UEFI: General UDisk 5.00    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/CDROM(1,0x23c,0x84c0)0000424f
dp: 02 01 0c 00 d0 41 03 0a 00 00 00 00 / 01 01 06 00 00 14 / 03 05 06 00 00 00 / 04 02 18 00 01 00 00 00 3c 02 00 00 00 00 00 00 c0 84 00 00 00 00 00 00 / 7f ff 04 00
data: 00 00 42 4f
Boot0002* UEFI: General UDisk 5.00, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,MBR,0x14eb2669,0x23c,0x2130)0000424f
dp: 02 01 0c 00 d0 41 03 0a 00 00 00 00 / 01 01 06 00 00 14 / 03 05 06 00 00 00 / 04 01 2a 00 02 00 00 00 3c 02 00 00 00 00 00 00 30 21 00 00 00 00 00 00 69 26 eb 14 00 00 00 00 00 00 00 00 00 00 00 00 01 01 / 7f ff 04 00
data: 00 00 42 4f
Warning: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/nvme0n1p2 update-grub
Sourcing file `/etc/default/grub'
Found linux image: /boot/vmlinuz-6.8.0-31-generic
Found initrd image: /boot/initrd.img-6.8.0-31-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
Adding boot menu entry for UEFI Firmware Settings ...

Unhide GRUB boot menu in nvme0n1p2/boot/grub/grub.cfg

Boot successfully repaired.

Locked-NVram detected. (Ubuntu) Please report this message to boot.repair@gmail.com
Please do not forget to make your UEFI firmware boot on the Ubuntu 24.04 LTS entry (nvme0n1p1/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Ubuntu 24.04 LTS on nvme0n1p2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: WhiskeyLake-U GT2 [UHD Graphics 620] from Intel Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.23.0(1.23) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,0002
Boot0000* Windows Boot Manager    HD(1,GPT,4db84b79-da95-4bb4-b03a-b8e4eec41187,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...C................
Boot0001* UEFI: General UDisk 5.00    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/CDROM(1,0x23c,0x84c0)..BO
Boot0002* UEFI: General UDisk 5.00, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,MBR,0x14eb2669,0x23c,0x2130)..BO

07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/BOOT/bkpbootx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/BOOT/bootx64.efi
39bc76ff6662f4fbe9aa116e4c997b41   nvme0n1p1/BOOT/fbx64.efi
4ba5a5aad43c197e9fb58b76b404d287   nvme0n1p1/BOOT/mmx64.efi
66f69798ad23240e43b7ba0044a914c4   nvme0n1p1/ubuntu/grubx64.efi
4ba5a5aad43c197e9fb58b76b404d287   nvme0n1p1/ubuntu/mmx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/ubuntu/shimx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p2    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    no-grubenv,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    fstab-has-bad-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 8C5BE143-43AE-4DC9-ABD4-8DC25B49B952
           Start       End   Sectors   Size Type
nvme0n1p1    2048   2203647   2201600     1G EFI System
nvme0n1p2 2203648 500115455 497911808 237.4G Linux filesystem
Disk sda: 3.75 GiB, 4026531840 bytes, 7864320 sectors
Disk identifier: 0x14eb2669
     Boot   Start     End Sectors  Size Id Type
sda1  *          0 5138431 5138432  2.5G  0 Empty
sda2           572    9067    8496  4.1M ef EFI (FAT-12/16/32)
sda3       5140480 7864319 2723840  1.3G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:4027MB:scsi:512:512:msdos:General UDisk:;
2:293kB:4643kB:4350kB:::esp;
3:2632MB:4027MB:1395MB:ext4::;
nvme0n1:256GB:nvme:512:512:gpt:KBG40ZNS256G NVMe TOSHIBA 256GB:;
1:1049kB:1128MB:1127MB:fat32::boot, esp;
2:1128MB:256GB:255GB:ext4::;

Free space >10MiB: ______________________________________________________________

sda: 4.43MiB:2510MiB:2506MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda         iso9660  2023-12-23-05-05-55-00                                                    Boot-Repair-Disk 64bit 
&#9500;&#9472;sda1      iso9660  2023-12-23-05-05-55-00               14eb2669-01                          Boot-Repair-Disk 64bit 
&#9500;&#9472;sda2      vfat     8D6C-A9F8                            14eb2669-02                          ESP                    
&#9492;&#9472;sda3      ext4     475f4128-3bf3-4e99-80ca-1d6aefba526c 14eb2669-03                          writable               
nvme0n1                                                                                                               
&#9500;&#9472;nvme0n1p1 vfat     A3EE-D473                            4020244a-d96d-4804-b3fb-2f0e0ffb9ed0                        
&#9492;&#9472;nvme0n1p2 ext4     f68c9a5d-a7af-49d4-8d5d-fb7d1c056e78 6af22809-1150-418f-a826-1a708d78de71                        

Mount points (filtered): _______________________________________________________

                                                            Avail Use% Mounted on
/dev/nvme0n1p1                                                 1G   1% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2                                               212G   4% /mnt/boot-sav/nvme0n1p2
/dev/sda1                                                       0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1                                              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p2                                              ext4            rw,relatime
/dev/sda1                                                   iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid f68c9a5d-a7af-49d4-8d5d-fb7d1c056e78 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p2/boot/grub/grub.cfg (filtered) ====================

Ubuntu   f68c9a5d-a7af-49d4-8d5d-fb7d1c056e78
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p2/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during curtin installation
/dev/disk/by-uuid/f68c9a5d-a7af-49d4-8d5d-fb7d1c056e78 / ext4 defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 during curtin installation
/swap.img    none    swap    sw    0    0
UUID=A3EE-D473  /boot/efi       vfat    defaults      0       1

==================== nvme0n1p2/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
  83.259994507 = 89.399738368   boot/vmlinuz                                   1
  83.259994507 = 89.399738368   boot/vmlinuz-6.8.0-31-generic                  1
  83.259994507 = 89.399738368   boot/vmlinuz.old                               1
 110.675777435 = 118.837211136  boot/initrd.img                                2
 110.675777435 = 118.837211136  boot/initrd.img-6.8.0-31-generic               2
 110.675777435 = 118.837211136  boot/initrd.img.old                            2

=================== nvme0n1p2: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 10:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5 11:36 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4 10:12 40_custom
-rwxr-xr-x 1 root root   215 Apr  4 10:12 41_custom
*******.us ko ()
```

I have not seen any issue on the partition during the installation process but I can check again.

Best regards,
Pierre

---

### Post by oldfred on 2024-09-04
We see a fair amount of these issues, usually from an update, where you still have an ubuntu entry in the UEFI, so system still works.
But you do not have an entry in UEFI. Just an old Window entry.
> modprobe: FATAL: Module efivars not found in directory /lib/modules/5.15.0-76-generic
grub-install: warning: EFI variables cannot be set on this system.


efivars are not in /lib/modules/kernel version and I am not sure they ever were. Saw bug back in 2013.
 
Actually efivars are here:
ls /sys/firmware/efi/efivars
There is no entry in fstab, but my mount shows.
> mount
[FONT=monospace][COLOR=#000000]efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)[/COLOR]
[/FONT]

With either Boot-Repair's advance mode to totally reinstall grub & latest kernel or a full choot you probably need to mount efivars. Be sure to boot in UEFI boot mode to make UEFI repairs.
chroot needs this:
mount -t efivarfs efivarfs /sys/firmware/efi/efivars

Neither of these mention mount of efivars as above:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by pierrelcv on 2024-09-04
Dear oldfred,
Firstly, thank you VERY MUCH for your very quick reply !  I need to recognize that I am a bit (very !) lost... I am quite a new Linux user (First Cup of Ubuntu :)) so your explication are a bit (completely) confusing for me.
How could I totally reinstall grub & latest kernel ? Which options should I use in boot-repair advanced tools ? What is efivars ? Chroot ?

Thank you for your help,
Pierre

---

### Post by oldfred on 2024-09-04
I have never used Advanced mode in Boot-Repair.

But I gather it walks you thru the commands required for a chroot (CHange ROOT) which uses the kernel from the live install, but puts you into the broken system to make repairs. When in chroot you can run other commands & I suggest the mount of the efivars as shown above before the install/reinstall of grub. Best to use current version live installer & ppa from Boot-Repair as Boot-Repair ISO not as often updated.

The links on chroot show the commands to type into a terminal from live installer, you will probably see similar commands when using Boot-Repair. Before Boot-Repair chroot was the only way to do major repairs. Other alternative was reinstall & restore from backup. If new install, reinstall can be quickest solution.

---

### Post by tea for one on 2024-09-05
> **pierrelcv said:**
>  I need to recognize that I am a bit (very !) lost... I am quite a new Linux user (First Cup of Ubuntu :)) so your explication are a bit (completely) confusing for me.
How could I totally reinstall grub & latest kernel ? Which options should I use in boot-repair advanced tools ? What is efivars ? Chroot ?
Yes, it gets complicated very quickly but, hopefully, there will be a path forward
> **pierrelcv said:**
> After that I have tried to install again (I reall thought that it would work !) but no change !!! The installation process is stucked at the same position (see previous screenshots). Argh !!!!
That's very annoying as I think that my case is very simple (no dual boot, no data to save) I just want to install Ubuntu on the entire hard disk... 
Any idea to fix this issue ?
I think that you should start from scratch.

_UEFI Settings_
Reset the settings to default
Disable secure boot 
Disable other security/trust settings if present e.g.TPM, PTT 
Switch to AHCI (your post no. 1)

_Installation_
Boot into a "Try Ubuntu" live session
Open Gparted > Device > Create Partition Table > Select GPT
Close Gparted
Start the installation
Allow the installer to automatically create the partitions
Choose a password without special characters ;)

Any luck?

---

### Post by pierrelcv on 2024-09-05
Dear Tea For One, 
Thank you for your easy reply :). Unfortunately, I followed exactly your guidelines:
- reset the BIOS and disable all security, I had an hope as I found that the old ubuntu entry was removed after that...
- apply the Gparted and remove every partition as you suggested
- launch the installation process

BUT the installation remains blocked exactly at the same point... ARGHH !!!
```

Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Using grub install command: /usr/lib/grub/grub-multi-install
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Grub install cmds:
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: [['efibootmgr', '-v'], ['dpkg-reconfigure', 'grub-efi-amd64'], ['update-grub'], ['/usr/lib/grub/grub-multi-install'], ['efibootmgr', '-v']]
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Running command ['mount', '--bind', '/dev', '/target/dev'] with allowed return codes [0] (capture=False)
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Running command ['mount', '--bind', '/proc', '/target/proc'] with allowed return codes [0] (capture=False)
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Running command ['mount', '--bind', '/run', '/target/run'] with allowed return codes [0] (capture=False)
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Running command ['mount', '--bind', '/sys', '/target/sys'] with allowed return codes [0] (capture=False)
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Running command ['mount', '--bind', '/sys/firmware/efi/efivars', '/target/sys/firmware/efi/efivars'] with allowed return codes [0] (capture=False)
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Running command ['mount', '--bind', '/target/usr/bin/true', '/target/usr/bin/ischroot'] with allowed return codes [0] (capture=False)
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Checking if target_proc (/target/proc) is a mount
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: It is, so unshare will use --mount-proc=/target/proc
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'efibootmgr', '-v'] with allowed return codes [0] (capture=True)
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Checking if target_proc (/target/proc) is a mount
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: It is, so unshare will use --mount-proc=/target/proc
Sep 05 20:58:31 ubuntu subiquity_log.3648[8285]: Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'dpkg-reconfigure', 'grub-efi-amd64'] with allowed return codes [0] (capture=True)
Sep 05 20:58:32 ubuntu subiquity_log.3648[8285]: Checking if target_proc (/target/proc) is a mount
Sep 05 20:58:32 ubuntu subiquity_log.3648[8285]: It is, so unshare will use --mount-proc=/target/proc
Sep 05 20:58:32 ubuntu subiquity_log.3648[8285]: Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'update-grub'] with allowed return codes [0] (capture=True)
```

I really think that restart from scratch is the best idea as the installation process worked perfectly the first time (when I removed/replaced Windows). But I do not know how to do that deeper...

Thank you for your help,
Pierre

---

### Post by tea for one on 2024-09-05
```
Using grub install command: /usr/lib/grub/grub-multi-install
```
I've not seen this before and I'm not sure how it is involved in the regular installation process.

---

### Post by pierrelcv on 2024-09-05
Dear Tea for one, 
Thank you for your reply !
The command was already present in the screenshots of my first post (bottom of the first screenshot)... Basically, I have copy/paste one command line more :)

Thank you !
Pierre

---

### Post by pierrelcv on 2024-09-05
Good evening,
VICTORY! I'm not sure why, but it worked in the end. I'm going to list all the operations I performed without knowing which one was decisive...
1) BIOS reset (Factory & Default)
2) Download Ubuntu 24.04.1 (I had Ubuntu 24.04 until now) and make a new bootable USB key via Rufus (not balenaEtcher like last time)
3) Boot on the new key and delete all disk partitions via Gparted.
4) Launch the installation and successfully boot without the USB key.

Thank you ALL for your help, I'm sorry I can't identify the cause of the problem... The important thing is that it works.

Pierre

Translated with DeepL.com (free version)

---

### Post by tea for one on 2024-09-05
It's nice to hear about success.
I suspect that Rufus was the decisive element.

---

