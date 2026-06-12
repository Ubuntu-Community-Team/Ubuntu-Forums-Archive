---
title: "boot-repair modprobe: FATAL: Module efivars not found in directory"
date: 2024-01-12
forum: Installation &amp; Upgrades
---

### Post by raindayqb on 2024-01-12
Update:

Despite trying several methods to resolve the NVRAM locked issue, I was unable to fix it even after purchasing a new SSD and installing Ubuntu on it. The error persisted. 
However, I discovered that I could still boot into Ubuntu via the BIOS boot menu. As you may know, Ubuntu was installed but GRUB did not work due to the NVRAM locked issue. 
I followed the accepted answer in this post and it worked like a charm. Before starting the process, I needed to move Ubuntu to the top of the BIOS boot order.[URL="https://askubuntu.com/questions/1425637/how-can-i-add-windows-11-to-grub-menu"]

dual boot - How can I add Windows 11 to grub menu? - Ask Ubuntu[/URL]

==========================================

Hello guys,


I'm trying to install dual-boot Ubuntu with Windows 11. I've been feeling totally hopeless for the last 2 days.


I've disable fastboot in Windows 11, secure boot in MSI BIOS, my USB boot is in GPT. But I still got FATAL error with grub-install. Then I tried to use boot-repair without success.


If anyone has any suggestions or ideas on how to overcome this obstacle, please help.


Thank you in advance!

```

boot-repair-4ppa2056                                              [20230926_1454]


============================= Boot Repair Summary ==============================










modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
ls: cannot access '/sys/firmware/efi/vars': No such file or directory


Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p5,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file




Mount nvme0n1p1 on /mnt/boot-sav/nvme0n1p5/boot/efi
No nvme0n1p5/boot/efi/efi/ ubuntu/mint folder


Unhide GRUB boot menu in nvme0n1p5/etc/default/grub


===================== Reinstall the grub-efi of nvme0n1p5 ======================


chroot /mnt/boot-sav/nvme0n1p5 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
chroot /mnt/boot-sav/nvme0n1p5 modprobe efivars


chroot /mnt/boot-sav/nvme0n1p5 efibootmgr -v before grub install
EFI variables are not supported on this system.




chroot /mnt/boot-sav/nvme0n1p5 uname -r
6.2.0-26-generic


chroot /mnt/boot-sav/nvme0n1p5 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: error: unknown filesystem.
Exit code: 1
Error: no grub*.efi generated for Ubuntu 22.04.3 LTS. Please report this message to boot.repair@gmail.com


chroot /mnt/boot-sav/nvme0n1p5 /sbin/grub-install --efi-directory=/boot/efi --target=x86_64-efi --recheck
Installing for x86_64-efi platform.
/sbin/grub-install: error: unknown filesystem.


chroot /mnt/boot-sav/nvme0n1p5 /sbin/grub-install --efi-directory=/boot/efi --target=x86_64-efi --no-nvram
Installing for x86_64-efi platform.
/sbin/grub-install: error: unknown filesystem.
--no-nvram exit code: 1 Please report this message to boot.repair@gmail.com


chroot /mnt/boot-sav/nvme0n1p5 efibootmgr -v after grub install
EFI variables are not supported on this system.


Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com


chroot /mnt/boot-sav/nvme0n1p5 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
/usr/sbin/grub-probe: error: unknown filesystem.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
/usr/sbin/grub-probe: error: unknown filesystem.


Unhide GRUB boot menu in nvme0n1p5/boot/grub/grub.cfg


An error occurred during the repair.
Error detected in grub_mkconfig. Please report this message to boot.repair@gmail.com


Locked-NVram detected.




============================ Boot Info After Repair ============================


 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No known boot loader is installed in the MBR of /dev/sda.


nvme0n1p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  According to the info in the boot sector, nvme0n1p1 
                       starts at sector 61442048. But according to the info 
                       from fdisk, nvme0n1p1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


nvme0n1p2: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme0n1p3: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe


nvme0n1p4: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


nvme0n1p5: _____________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


nvme0n1p6: _____________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi




================================ 2 OS detected =================================


OS#1:   Ubuntu 22.04.3 LTS on nvme0n1p5
OS#2:   Windows 8 or 10 on nvme0n1p3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Navi 23 [Radeon RX 6600/6600 XT/6600M] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 2.F0(5.17) from American Megatrends International, LLC.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* Windows Boot Manager    HD(1,GPT,feb8c932-53bf-41e7-953d-5f1810b6c6ae,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* UEFI: KingstonDataTraveler 2.0PMAP, Partition 1    PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/USB(10,0)/USB(2,0)/HD(1,GPT,f5044010-6f30-4804-bd98-9e0ebc070c2c,0x800,0x1d13310)..BO


7c8dc272a3781364b96a42492133f037   nvme0n1p1/Boot/bootx64.efi
7c8dc272a3781364b96a42492133f037   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
99c9de136b720b86e6184d40e4bfcbbb   nvme0n1p1/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    no-grubenv,    update-grub,    farbios
nvme0n1p6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios


Partitions info (2/3): _________________________________________________________


nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p6    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1


fdisk -l (filtered): ___________________________________________________________


Disk nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 962FA8FD-A196-4DBC-B09C-749EC1116959
               Start        End    Sectors   Size Type
nvme0n1p1       2048     206847     204800   100M EFI System
nvme0n1p2     206848     239615      32768    16M Microsoft reserved
nvme0n1p3     239616 1680982015 1680742400 801.4G Microsoft basic data
nvme0n1p4 1952141312 1953521663    1380352   674M Windows recovery environment
nvme0n1p5 1680982016 1780981759   99999744  47.7G Linux filesystem
nvme0n1p6 1780981760 1952141311  171159552  81.6G Linux filesystem
Partition table entries are not in disk order.
Disk sda: 14.54 GiB, 15610576896 bytes, 30489408 sectors
Disk identifier: 63A73801-89C2-444B-BD79-80F95861FBC5
      Start      End  Sectors  Size Type
sda1   2048 30489359 30487312 14.5G Microsoft basic data


parted -lm (filtered): _________________________________________________________


sda:15.6GB:scsi:512:512:gpt:Kingston DataTraveler 2.0:;
1:1049kB:15.6GB:15.6GB:fat32:Main Data Partition:msftdata;
nvme0n1:1000GB:nvme:512:512:gpt:WD Blue SN570 1TB:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:861GB:861GB:ntfs:Basic data partition:msftdata;
5:861GB:912GB:51.2GB:ext4::;
6:912GB:999GB:87.6GB:ext4::;
4:999GB:1000GB:707MB:ntfs::hidden, diag;


blkid (filtered): ______________________________________________________________


NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9492;&#9472;sda1      vfat     AAFF-19FC                            f5044010-6f30-4804-bd98-9e0ebc070c2c UBUNTU 22_0 Main Data Partition
nvme0n1                                                                                                    
&#9500;&#9472;nvme0n1p1 vfat     A048-5070                            feb8c932-53bf-41e7-953d-5f1810b6c6ae             EFI system partition
&#9500;&#9472;nvme0n1p2                                               bc4dbf91-970f-48b5-b8e9-d8c805cd278d             Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     5E68494668491E61                     44d227c1-073f-47bf-8c90-499d92c93aae             Basic data partition
&#9500;&#9472;nvme0n1p4 ntfs     6E246CB5246C81C7                     321b2b19-f741-4558-996f-13900b8dff98             
&#9500;&#9472;nvme0n1p5 ext4     beb3f710-e41d-4035-b7e1-202eb658b12e fcf1d890-2393-4d29-8aa0-9837c596cead             
&#9492;&#9472;nvme0n1p6 ext4     00ee367b-7366-4bc3-b1d0-d2a39ef7c446 773417a7-74dd-43ed-a78e-4a6ed0741195             


Mount points (filtered): _______________________________________________________


                           Avail Use% Mounted on
/dev/nvme0n1p1             64.8M  33% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3            646.5G  19% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4             89.2M  87% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5             35.9G  18% /mnt/boot-sav/nvme0n1p5
/dev/nvme0n1p6             75.7G   0% /mnt/boot-sav/nvme0n1p6
/dev/sda1                   9.8G  32% /cdrom


Mount options (filtered): ______________________________________________________




=================== nvme0n1p5/boot/grub/grub.cfg (filtered) ====================


Ubuntu   beb3f710-e41d-4035-b7e1-202eb658b12e
Ubuntu, with Linux 6.2.0-26-generic   beb3f710-e41d-4035-b7e1-202eb658b12e
Windows Boot Manager (on nvme0n1p1)   osprober-efi-nvme0n1p1
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


======================== nvme0n1p5/etc/fstab (filtered) ========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=beb3f710-e41d-4035-b7e1-202eb658b12e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=A048-5070  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p6 during installation
UUID=00ee367b-7366-4bc3-b1d0-d2a39ef7c446 /home           ext4    defaults        0       2


==================== nvme0n1p5/etc/default/grub (filtered) =====================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


================= nvme0n1p5: Location of files loaded by Grub ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 832.520633698 = 893.912223744  boot/vmlinuz                                   1
 832.520633698 = 893.912223744  boot/vmlinuz-6.2.0-26-generic                  1
 822.130168915 = 882.755547136  boot/initrd.img                                1
 822.130168915 = 882.755547136  boot/initrd.img-6.2.0-26-generic               1
 822.130168915 = 882.755547136  boot/initrd.img.old                            1


=================== nvme0n1p5: ls -l /etc/grub.d/ (filtered) ===================


-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17 05:35 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom


====================== sda1/boot/grub/grub.cfg (filtered) ======================


Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


==================== sda1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

```

---

### Post by oldfred on 2024-01-12
Is install Mint or Ubuntu?
> No nvme0n1p5/boot/efi/efi/ ubuntu/mint folder

You then show no efivars and Locked NVRAM issues.

What brand/model system.
We have seen multiple systems with NVRAM issues and no clear solution.

Locked NVram
[https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up](https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up) & 
[https://ubuntuforums.org/showthread.php?t=2491460](https://ubuntuforums.org/showthread.php?t=2491460)  &
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)
Locked NVRAM - turning on Secure boot & reset UEFI Dell XPS 9530
[https://ubuntuforums.org/showthread.php?t=2490359](https://ubuntuforums.org/showthread.php?t=2490359)
Locked UEFI/BIOS setting: Lenovo UEFI screen
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
add "--no-nvram" to the "grub-install" command 
[https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0](https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0)

---

### Post by raindayqb on 2024-01-29
Hello @oldfred, 
Thank you for your response. I have updated my post with the solution that worked for me. 
I hope this helps other people who are facing the same issue :)
Have a nice day!

---

