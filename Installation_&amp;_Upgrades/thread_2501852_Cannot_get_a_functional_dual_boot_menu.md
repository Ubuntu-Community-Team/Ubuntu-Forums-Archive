---
title: "Cannot get a functional dual boot menu"
date: 2024-10-23
forum: Installation &amp; Upgrades
---

### Post by alreve on 2024-10-23
I installed Lubuntu on the SSD of my hp, which also has a 1 To hard disk. I also have windows 10 on that SSD. Before, I tried to install Lubuntu 
on the hard disk. 2 versions, both failed to install but Boot Repair can see them. I can delete them if it helps. 

After the succesful install on the SSD, when I rebooted, the hp booted straight into windows. Boot repair didn't help (I ran it with the default settings). 

I made sure secure boot and fast boot were disabled. 

I could boot into Lubuntu Noble Numbat, but to do this I had to repeatedly hit F9 at startup. Then I saw the menu : 
"OS Boot Manager (UEFI) - Windows Boot Manager (SanDisk  SD9 SN8W-128G-1006)"
"OS Boot Manager (UEFI) - ubuntu (SanDisk SD9  SN8W-128G-1006)". 
and I could select Lubuntu with the arrow key.

After quite a lot of fiddling, I discovered /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
From Lubuntu, I renamed it rem_bootmgfw.efi

Now I see grub menu at startup, with the windows option, but the windows option doesn't function. It says it can't find bootmgfw.efi.

So, basically, I have the choice between a functional menu I can only reach by hitting F9 repeatedly or my current setting where 
windows won't boot unless I change back the name of rem_bootmgfw.efi into bootmgfw.efi. 

How can I get a proper boot menu, such as grub, to  take control at startup, please? 

============ Below is the output of Boot Repair ============

Note : The OS#2 (linux): Ubuntu 22.04.5 LTS on sda1 and the OS#3 (linux): Ubuntu 24.04.1 LTS on sda2 are the failed lubuntu installations.

Default settings: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sdb5,
using the following options:  sdb1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 24.04.1 LTS entry (sdb1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)

Note : I've done that, except changing the boot order in my UEFI firmware. Didn't find how to do that. 

User settings: _________________________________________________________________

modprobe: FATAL: Module efivars not found in directory /lib/modules/6.8.0-47-generic
The settings chosen by the user will reinstall the grub-efi of
sdb5,
using the following options:  sdb1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file


/boot/efi added in sdb5/fstab
/dev/sdb5/boot/efi not empty

Unhide GRUB boot menu in sdb5/etc/default/grub

===================== Reinstall the grub-efi of /dev/sdb5 ======================

grub-install --version
grub-install (GRUB) 2.12-1ubuntu7
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.8.0-47-generic
modprobe efivars

efibootmgr -v (filtered) before grub install
BootCurrent: 0005
Timeout: 20 seconds
BootOrder: 0000,3000,0005,2001,2002,2004,0003,0002
Boot0000* Windows Boot Manager    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* Windows Boot Manager    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(EFIubuntugrubx64.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000061000100000010000000040000007fff0400
Boot0002* Internal Hard Drive - ST1000LM035-1RK172    BBS(HD,Internal Hard Drive - ST1000LM035-1RK172,0x500)feff05000000000000000000000001062d0052e602000005190052e6410052e6000000020000000000000000000000000000000000000000000000000000000000d887c9ae110002010c00d041030a0000000001010600020801010600000003120a000000000000007fff0400
Boot0003* Internal Hard Drive - SanDisk SD9SN8W-128G-1006    BBS(HD,Internal Hard Drive - SanDisk SD9SN8W-128G-1006,0x500)feff05000000000000000000000001062d0059e602000005190059e6410059e6000000120000000000000000000000000000000000000000000000000000000000088ec9ae120002010c00d041030a0000000001010600020801010600000003120a000100000000007fff0400
Boot0005* ubuntu    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC

uname -r
6.8.0-47-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sdb1
mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.efi
cp /boot/efi/efi/ubuntu/grubx64.efi /boot/efi/EFI/Boot/bootx64.efi

grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.

efibootmgr -v (filtered) after grub install
BootCurrent: 0005
Timeout: 20 seconds
BootOrder: 0005,0000,3000,2001,2002,2004,0003,0002
Boot0000* Windows Boot Manager    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* Windows Boot Manager    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(EFIubuntugrubx64.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000061000100000010000000040000007fff0400
Boot0002* Internal Hard Drive - ST1000LM035-1RK172    BBS(HD,Internal Hard Drive - ST1000LM035-1RK172,0x500)feff05000000000000000000000001062d0052e602000005190052e6410052e6000000020000000000000000000000000000000000000000000000000000000000d887c9ae110002010c00d041030a0000000001010600020801010600000003120a000000000000007fff0400
Boot0003* Internal Hard Drive - SanDisk SD9SN8W-128G-1006    BBS(HD,Internal Hard Drive - SanDisk SD9SN8W-128G-1006,0x500)feff05000000000000000000000001062d0059e602000005190059e6410059e6000000120000000000000000000000000000000000000000000000000000000000088ec9ae120002010c00d041030a0000000001010600020801010600000003120a000100000000007fff0400
Boot0005* Ubuntu    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC

update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/lubuntu-grub-theme.cfg'
Found theme: /usr/share/grub/themes/lubuntu-grub-theme/theme.txt
Found linux image: /boot/vmlinuz-6.8.0-47-generic
Found initrd image: /boot/initrd.img-6.8.0-47-generic
Found linux image: /boot/vmlinuz-6.8.0-40-generic
Found initrd image: /boot/initrd.img-6.8.0-40-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Found Ubuntu 22.04.5 LTS (22.04) on /dev/sda1
Found Ubuntu 24.04.1 LTS (24.04) on /dev/sda2
Found Windows Boot Manager on /dev/sdb1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...

Unhide GRUB boot menu in sdb5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 24.04.1 LTS entry (sdb1/efi/ubuntu/grubx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 22.04.5 LTS
    Boot files:        /etc/fstab /etc/default/grub

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg
                       /efi/Microsoft/Boot/bootmgfw.efi
                       /efi/Microsoft/Boot/bootmgr.efi
                       /efi/Microsoft/Boot/SecureBootRecovery.efi

sdb2: __________________________________________________________________________

    File system:
    Boot sector type:  -
    Boot sector info:

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


================================ 4 OS detected =================================

OS#1 (linux):   The OS now in use - Ubuntu 24.04.1 LTS on sdb5
OS#2 (linux):   Ubuntu 22.04.5 LTS on sda1
OS#3 (linux):   Ubuntu 24.04.1 LTS on sda2
OS#4 (windows):   Windows 10 or 11 on sdb3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Picasso/Raven 2 [Radeon Vega Series / Radeon Vega Mobile Series] from Advanced Micro Devices, Inc. [AMD/ATI]
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.8.0-47-generic root=UUID=e473ae63-8a11-4c2d-bd34-b23b26bc9c0a ro quiet splash vt.handoff=7
df -Th / : /dev/sdb5      ext4   59G  8.7G   47G  16% /

===================================== UEFI =====================================

BIOS/UEFI firmware: F.13(15.13) from Insyde
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0005
Timeout: 20 seconds
BootOrder: 0005,0000,3000,2001,2002,2004,0003,0002
Boot0000* Windows Boot Manager    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* Windows Boot Manager    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000061000100000010000000040000007fff0400
Boot0002* Internal Hard Drive - ST1000LM035-1RK172    BBS(HD,Internal Hard Drive - ST1000LM035-1RK172,0x500)feff05000000000000000000000001062d0052e602000005190052e6410052e6000000020000000000000000000000000000000000000000000000000000000000d887c9ae110002010c00d041030a0000000001010600020801010600000003120a000000000000007fff0400
Boot0003* Internal Hard Drive - SanDisk SD9SN8W-128G-1006    BBS(HD,Internal Hard Drive - SanDisk SD9SN8W-128G-1006,0x500)feff05000000000000000000000001062d0059e602000005190059e6410059e6000000120000000000000000000000000000000000000000000000000000000000088ec9ae120002010c00d041030a0000000001010600020801010600000003120a000100000000007fff0400
Boot0005* Ubuntu    HD(1,GPT,1695ed28-bfe9-4fc4-b2c2-bb0e33413587,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sdb    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sda    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sdb5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    no-grubenv,    update-grub,    end-after-100GB
sda1    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    no-grubenv,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sdb5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
sdb4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs
sdb3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sdb1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
sda2    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
sda1    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4

Partitions info (3/3): _________________________________________________________

sdb5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdb
sdb4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda1    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: E2203556-7D3B-43BA-827A-A667A7BEDB87
         Start        End   Sectors   Size Type
sda1  977069282 1953520064 976450783 465.6G Linux filesystem
sda2     618496  977069280 976450785 465.6G EFI System
Partition table entries are not in disk order.
Disk sdb: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk identifier: 9EDAE009-C871-4072-88DA-061A32150D06
         Start       End   Sectors  Size Type
sdb1       2048    206847    204800  100M EFI System
sdb2     206848    239615     32768   16M Microsoft reserved
sdb3     239616 124617393 124377778 59.3G Microsoft basic data
sdb4  248995840 250066943   1071104  523M Windows recovery environment
sdb5  124617395 248995169 124377775 59.3G Linux filesystem
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM035-1RK1:;
2:317MB:500GB:500GB:ext4:lubuntu_2404:boot, esp;
1:500GB:1000GB:500GB:ext4:root:;
sdb:128GB:scsi:512:4096:gpt:ATA SanDisk SD9SN8W-:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp, no_automount;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres, no_automount;
3:123MB:63.8GB:63.7GB:ntfs:Basic data partition:msftdata;
5:63.8GB:127GB:63.7GB:ext4:root:;
4:127GB:128GB:548MB:ntfs::hidden, diag, no_automount;

Free space >10MiB: ______________________________________________________________

sda: 0.02MiB:302MiB:302MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda
&#9500;&#9472;sda1 ext4     940bd12b-0dc1-46ed-87fe-bfdb0eb9715a 0743ba8e-41a2-2348-a1b6-bd267db8e265       root
&#9492;&#9472;sda2 ext4     2004cf58-df38-4ee0-9743-de134566f377 0a31c475-0ebc-43de-ae7e-da3195c5c047       lubuntu_2404
sdb
&#9500;&#9472;sdb1 vfat     98FB-4A13                            1695ed28-bfe9-4fc4-b2c2-bb0e33413587       EFI system partition
&#9500;&#9472;sdb2                                               c060020c-f85c-4909-9707-34ddafa37d15       Microsoft reserved partition
&#9500;&#9472;sdb3 ntfs     E4DC0031DC000092                     e349bdfd-ec73-4acd-b521-94648fac4d18 SSD   Basic data partition
&#9500;&#9472;sdb4 ntfs     3CF02F0CF02ECC48                     d339b6c4-239c-4c12-9299-291012434792
&#9492;&#9472;sdb5 ext4     e473ae63-8a11-4c2d-bd34-b23b26bc9c0a c4d15a4d-60f5-b043-b259-8d25ca8ef7a1       root

Mount points (filtered): _______________________________________________________

                        Avail Use% Mounted on
/dev/sda1                427G   2% /mnt/boot-sav/sda1
/dev/sda2              425.9G   2% /mnt/boot-sav/sda2
/dev/sdb3               21.1G  64% /mnt/boot-sav/sdb3
/dev/sdb4               88.7M  83% /mnt/boot-sav/sdb4
/dev/sdb5               46.5G  15% /
efivarfs                81.8K  46% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/sda1              ext4            rw,relatime
/dev/sda2              ext4            rw,relatime
/dev/sdb3              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb4              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb5              ext4            rw,relatime,discard

========================== sda1/etc/fstab (filtered) ===========================

# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=2004cf58-df38-4ee0-9743-de134566f377 /boot/efi      ext4    umask=0077 0 2
UUID=940bd12b-0dc1-46ed-87fe-bfdb0eb9715a /              ext4    defaults   0 1
/swapfile                                 swap           swap    defaults   0 0

======================= sda1/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 469.502778053 = 504.124769280  boot/vmlinuz                                   1
 469.502778053 = 504.124769280  boot/vmlinuz-6.8.0-40-generic                  1
 469.502778053 = 504.124769280  boot/vmlinuz.old                               1
 470.352887154 = 505.037566976  boot/initrd.img                                1
 470.352887154 = 505.037566976  boot/initrd.img-6.8.0-40-generic               1
 470.352887154 = 505.037566976  boot/initrd.img.old                            1

===================== sda1: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

========================== sda2/etc/fstab (filtered) ===========================

# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=2004cf58-df38-4ee0-9743-de134566f377 /              ext4    defaults   0 1
/swapfile                                 swap           swap    defaults   0 0

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   4.411827087 = 4.737163264    boot/vmlinuz                                   1
   3.941654205 = 4.232318976    boot/vmlinuz-6.8.0-41-generic                  1
   4.411827087 = 4.737163264    boot/vmlinuz-6.8.0-47-generic                  1
   3.941654205 = 4.232318976    boot/vmlinuz.old                               1
   5.718132019 = 6.139797504    boot/initrd.img                                2
   4.046760559 = 4.345176064    boot/initrd.img-6.8.0-41-generic               1
   5.718132019 = 6.139797504    boot/initrd.img-6.8.0-47-generic               2
   4.046760559 = 4.345176064    boot/initrd.img.old                            1

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5  2024 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4  2024 40_custom
-rwxr-xr-x 1 root root   215 Apr  4  2024 41_custom

===================== sdb1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid e473ae63-8a11-4c2d-bd34-b23b26bc9c0a root hd1,gpt5
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sdb5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   e473ae63-8a11-4c2d-bd34-b23b26bc9c0a
Ubuntu 22.04.5 LTS (22.04) (on sda1)   940bd12b-0dc1-46ed-87fe-bfdb0eb9715a
Ubuntu 24.04.1 LTS (24.04) (on sda2)   2004cf58-df38-4ee0-9743-de134566f377
Windows Boot Manager (on sdb1)   osprober-efi-98FB-4A13
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sdb5/etc/fstab (filtered) ===========================

# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=e473ae63-8a11-4c2d-bd34-b23b26bc9c0a /              ext4    defaults,discard 0 1
/swapfile                                 swap           swap    defaults   0 0
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0
UUID=98FB-4A13  /boot/efi       vfat    defaults      0       1

======================= sdb5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sdb5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  75.301396847 = 80.854259200   boot/grub/grub.cfg                             1
  62.162694454 = 66.746684928   boot/vmlinuz                                   1
  65.865808010 = 70.722872832   boot/vmlinuz-6.8.0-40-generic                  2
  62.162694454 = 66.746684928   boot/vmlinuz-6.8.0-47-generic                  1
  65.865808010 = 70.722872832   boot/vmlinuz.old                               2
  76.000993252 = 81.605445120   boot/initrd.img                                1
  76.071313381 = 81.680950784   boot/initrd.img-6.8.0-40-generic               2
  76.000993252 = 81.605445120   boot/initrd.img-6.8.0-47-generic               1
  76.071313381 = 81.680950784   boot/initrd.img.old                            2

===================== sdb5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Aug 21 20:39 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

---

### Post by tea for one on 2024-10-23
> **alreve said:**
> After quite a lot of fiddling, I discovered /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
From Lubuntu, I renamed it rem_bootmgfw.efi
Now I see grub menu at startup, with the windows option, but the windows option doesn't function. It says it can't find bootmgfw.efi.
So, basically, I have the choice between a functional menu I can only reach by hitting F9 repeatedly or my current setting where 
windows won't boot unless I change back the name of rem_bootmgfw.efi into bootmgfw.efi.
First task is to change it back to the original to allow Windows to boot normally.
> **alreve said:**
> How can I get a proper boot menu, such as grub, to  take control at startup, please? 
Before we go any further, where do you wish Lubuntu 24.04 to be installed?
I imagine it will be on sda because Windows is already on sdb (the smaller 128GB disk)?

---

### Post by yancek on 2024-10-23
Both of your drives are GPT so if you wanted a Legacy install on sda, you would need to create a bios_boot partition on the drive on which to put the core.img file then install Grub code to the MBR of that drive.  Boot repair shows you did not do this.

You have an install of Ubuntu on sdb5 with the grub efi files on an EFI partition of that drive.  The reason you can't boot windows is because you renamed the windows boot file and you need to change it back to the correct name as mentioned above.  After doing that run sudo update-grub to get a new correct menu.  Tapping the F9 key is the standard method of accessing one time options on many HP computers 

If you want Ubuntu on the other drive, post back so someone can make suggestions.

---

