---
title: "[mint] ALERT! /dev/disk/by-uuid/xxxxxxxxx does not exist"
date: 2016-02-17
forum: MINT
---

### Post by rudy8 on 2016-02-17
Hello all, 
I have a fresh install of linux mint 17.3 (based on Trusty). I only added proprietary Nvidia driver 352
My system: 
- intel core i5 6600K Skylake + 16Go DDR4
- Motherboard: Asus Z170
- **SSD pluged in NVMe** (i think the problem is caused by this)
- Linux kernel 3.19
I don't have any sound, and the system is pretty instable. I read it is probably caused by the fact my motherboard and proc are recent and probably not well handled by the kernel and I should upgrade to kernel 4.x

So i tried to install kernel 4.5RC3 with the following commands: 

```
wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc3-wily/linux-headers-4.5.0-040500rc3_4.5.0-040500rc3.201602071930_all.deb

wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc3-wily/linux-headers-4.5.0-040500rc3-generic_4.5.0-040500rc3.201602071930_i386.deb

wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc3-wily/linux-image-4.5.0-040500rc3-generic_4.5.0-040500rc3.201602071930_i386.deb

sudo update-grub

sudo reboot

```
 But at reboot, i have: 
```
ALERT! /dev/disk/by-uuid/xxxxxxxxx does not exist. Dropping to a shell
initramfs:_

```

where xxxxxxx is the UUID of the root partition which is on my SSD in NVMe. 


Here is my  /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=ccdddc75-bd25-4fb6-98c2-55da313f529f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p2 during installation
UUID=6A65-4C30  /boot/efi       vfat    defaults        0       1
# /donnees was on /dev/sda1 during installation
UUID=3b9da9ae-e7c5-406f-8585-e55b2d596e00 /donnees        ext4    defaults        0       2
# /home was on /dev/nvme0n1p7 during installation
UUID=d7bf0dee-e5ea-4dad-b4fc-84a2ebcf9ca0 /home           ext4    defaults        0       2
# swap was on /dev/nvme0n1p6 during installation
UUID=87a672a0-cba9-47b2-b7fc-45116a1c4eac none            swap    sw              0       0
```

Here is boot information with the script boot-info:

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]  
 
    ============================= Boot Info Summary: ===============================
  
     => No boot loader is installed in the MBR of /dev/sda.
      => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
  
    sda1: __________________________________________________________________________
  
        File system:       ext4
         Boot sector type:  -
         Boot sector info: 
         Operating System:  
         Boot files:        
  
    sdb1: __________________________________________________________________________
  
        File system:       vfat
         Boot sector type:  SYSLINUX 4.05 20140113
         Boot sector info:  Syslinux looks at sector 3494018 of /dev/sdb1 for its 
                            second stage. SYSLINUX is installed in the  directory. 
                            No errors found in the Boot Parameter Block.
         Operating System:  
         Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                            /EFI/BOOT/grubx64.efi /ldlinux.sys
  
    ============================ Drive/Partition Info: =============================
  
    Drive: sda _____________________________________________________________________
  
    Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
     255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
     Units = sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT
  
 
    GUID Partition Table detected.
  
    Partition    Start Sector    End Sector  # of Sectors System
     /dev/sda1           2,048 2,639,306,751 2,639,304,704 Data partition (Linux)
  
    Drive: sdb _____________________________________________________________________
  
    Disk /dev/sdb: 16.0 GB, 16025444352 bytes
     255 heads, 63 sectors/track, 1948 cylinders, total 31299696 sectors
     Units = sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sdb1    *          2,048    31,293,439    31,291,392   b W95 FAT32
  
 
    "blkid" output: ________________________________________________________________
  
    Device           UUID                                   TYPE       LABEL
  
    /dev/nvme0n1p1   8A88649088647C97                       ntfs       Récupération
     /dev/nvme0n1p2   6A65-4C30                              vfat       
     /dev/nvme0n1p4   D44A75DA4A75BA36                       ntfs       
     /dev/nvme0n1p5   ccdddc75-bd25-4fb6-98c2-55da313f529f   ext4       racine_linux
     /dev/nvme0n1p6   87a672a0-cba9-47b2-b7fc-45116a1c4eac   swap       
     /dev/nvme0n1p7   d7bf0dee-e5ea-4dad-b4fc-84a2ebcf9ca0   ext4       
     /dev/sda1        3b9da9ae-e7c5-406f-8585-e55b2d596e00   ext4       
     /dev/sdb1        64D6-D65D                              vfat       Clé USB
  
    ========================= "ls -l /dev/disk/by-id" output: ======================
  
    total 0
     lrwxrwxrwx 1 root root  9 Feb 17 07:25 ata-WDC_WD30EZRX-00SPEB0_WD-WCC4E3DXPHEX -> ../../sda
     lrwxrwxrwx 1 root root 10 Feb 16 07:44 ata-WDC_WD30EZRX-00SPEB0_WD-WCC4E3DXPHEX-part1 -> ../../sda1
     lrwxrwxrwx 1 root root  9 Feb 17 07:25 usb-SanDisk_USB_Ultra_VC0001150420154030000332-0:0 -> ../../sdb
     lrwxrwxrwx 1 root root 10 Feb 16 07:44 usb-SanDisk_USB_Ultra_VC0001150420154030000332-0:0-part1 -> ../../sdb1
     lrwxrwxrwx 1 root root  9 Feb 17 07:25 wwn-0x50014ee260fc2db4 -> ../../sda
     lrwxrwxrwx 1 root root 10 Feb 16 07:44 wwn-0x50014ee260fc2db4-part1 -> ../../sda1
  
    ================================ Mount points: =================================
  
    Device           Mount_Point              Type       Options
  
    /dev/nvme0n1p2   /boot/efi                vfat       (rw)
     /dev/nvme0n1p5   /                        ext4       (rw,errors=remount-ro)
     /dev/nvme0n1p7   /home                    ext4       (rw)
     /dev/sda1        /donnees                 ext4       (rw)
  
 
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
  
    menuentry "Start Linux Mint 17.3 KDE 64-bit" {
         set gfxpayload=keep
         linux    /casper/vmlinuz  file=/cdrom/preseed/linuxmint.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
         initrd    /casper/initrd.lz
     }
     menuentry "Start Linux Mint 17.3 KDE 64-bit (compatibility mode)" {
         linux    /casper/vmlinuz  file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa iso-scan/filename=${iso_path} ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll --
         initrd    /casper/initrd.lz
     }
     menuentry "Check the integrity of the medium" {
         linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
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
     append initrd=/ubninit file=/cdrom/preseed/linuxmint.seed boot=casper quiet splash --
  
    label ubnentry0
     menu label Start Linux Mint
     kernel /casper/vmlinuz
     append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper  quiet splash --
  
    label ubnentry1
     menu label Start in compatibility mode
     kernel /casper/vmlinuz
     append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa nomodeset b43.blacklist=yes  ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll --
  
    label ubnentry2
     menu label Integrity check
     kernel /casper/vmlinuz
     append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --
  
    label ubnentry3
     menu label Memory test
     kernel /casper/memtest
     append initrd=/ubninit 
  
    label ubnentry4
     menu label Boot from local drive
     kernel /ubnkern
     append initrd=/ubninit hd0
  
    label ubnentry5
     menu label Start Linux Mint 17.3 KDE 64-bit
     kernel /casper/vmlinuz
     append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
  
    label ubnentry6
     menu label Start Linux Mint 17.3 KDE 64-bit (compatibility mode)
     kernel /casper/vmlinuz
     append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa iso-scan/filename=${iso_path} ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll --
  
    label ubnentry7
     menu label Check the integrity of the medium
     kernel /casper/vmlinuz
     append initrd=/casper/initrd.lz boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
  
    --------------------------------------------------------------------------------
  
    ============== sdb1: Version of COM32(R) files used by Syslinux: ===============
  
     menu.c32                           :  COM32R module (v4.xx)
  
    =============================== StdErr Messages: ===============================
  
    File descriptor 8 (/proc/27131/mounts) leaked on lvs invocation. Parent PID 5482: bash
     File descriptor 63 (pipe:[374602]) leaked on lvs invocation. Parent PID 5482: bash
       No volume groups found
  
    ADDITIONAL INFORMATION :
     =================== log of boot-info 2016-02-17__07h25 ===================
     boot-info version : 4ppa35
     boot-sav version : 4ppa35
     glade2script version : 3.2.2~ppa47~saucy
     boot-sav-extra version :
     File descriptor 8 (/proc/27131/mounts) leaked on lvs invocation. Parent PID 28721: /bin/sh
     No volume groups found
     boot-info is executed in installed-session (Linux Mint 17.3 Rosa, rosa, LinuxMint, x86_64)
     CPU op-mode(s):        32-bit, 64-bit
     BOOT_IMAGE=/boot/vmlinuz-3.19.0-32-generic root=UUID=ccdddc75-bd25-4fb6-98c2-55da313f529f ro quiet splash vt.handoff=7
  
    WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util fdisk doesn't support GPT. Use GNU Parted.
  
 
    WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
  
 
    =================== os-prober:
     /dev/disk/by-uuid/ccdddc75-bd25-4fb6-98c2-55da313f529f:L'OS actuellement utilisé - Linux Mint 17.3 Rosa CurrentSession:linux
     /dev/nvme0n1p2@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
  
    =================== blkid:
     /dev/nvme0n1p1: LABEL="RM-CM-)cupM-CM-)ration" UUID="8A88649088647C97" TYPE="ntfs"
     /dev/nvme0n1p2: UUID="6A65-4C30" TYPE="vfat"
     /dev/nvme0n1p4: UUID="D44A75DA4A75BA36" TYPE="ntfs"
     /dev/nvme0n1p5: LABEL="racine_linux" UUID="ccdddc75-bd25-4fb6-98c2-55da313f529f" TYPE="ext4"
     /dev/nvme0n1p6: UUID="87a672a0-cba9-47b2-b7fc-45116a1c4eac" TYPE="swap"
     /dev/nvme0n1p7: UUID="d7bf0dee-e5ea-4dad-b4fc-84a2ebcf9ca0" TYPE="ext4"
     /dev/sda1: UUID="3b9da9ae-e7c5-406f-8585-e55b2d596e00" TYPE="ext4"
     /dev/sdb1: LABEL="ClM-CM-) USB" UUID="64D6-D65D" TYPE="vfat"
  
    disk/by-uuid/ccdddc75-bd25-4fb6-98c2-55da313f529f (sda) has unknown type. Veuillez indiquer ce message à boot.repair@gmail.com

  
    2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.
  
    Windows not detected by os-prober on nvme0n1p4.
     Linux not detected by os-prober on nvme0n1p5. Veuillez indiquer ce message à boot.repair@gmail.com

  
    Attention : identifiant de table de partitions GPT (GUID) détecté sur « /dev/nvme0n1 ». L'utilitaire sfdisk ne prend pas GPT en charge. Utilisez GNU Parted.

  
 
    Attention : identifiant de table de partitions GPT (GUID) détecté sur « /dev/sda ». L'utilitaire sfdisk ne prend pas GPT en charge. Utilisez GNU Parted.
  
 
    WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util fdisk doesn't support GPT. Use GNU Parted.
  
 
    WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
  
    Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
     Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi

  
    =================== //etc/grub.d/ :
     drwxr-xr-x  2 root     root       4096 févr. 16 07:44 grub.d
     total 80
     -rwxr-xr-x 1 root root  9791 déc.  17 16:00 00_header
     -rwxr-xr-x 1 root root  6058 mai   13  2015 05_debian_theme
     -rwxr-xr-x 1 root root  1180 oct.  25  2014 06_mint_theme
     -rwxr-xr-x 1 root root 11615 févr. 16 07:44 10_linux
     -rwxr-xr-x 1 root root 10412 juin  26  2015 20_linux_xen
     -rwxr-xr-x 1 root root  1992 mars  12  2014 20_memtest86+
     -rwxr-xr-x 1 root root 11692 juin  26  2015 30_os-prober
     -rwxr-xr-x 1 root root  1416 juin  26  2015 30_uefi-firmware
     -rwxr-xr-x 1 root root   214 juin  26  2015 40_custom
     -rwxr-xr-x 1 root root   216 juin  26  2015 41_custom
     -rw-r--r-- 1 root root   483 juin  26  2015 README
  
 
 
 
    =================== //etc/default/grub :
  
    # If you change this file, run 'update-grub' afterwards to update
     # /boot/grub/grub.cfg.
     # For full documentation of the options in this file, see:
     #   info -f grub -n 'Simple configuration'
  
    GRUB_DEFAULT=0
     #GRUB_HIDDEN_TIMEOUT=0
     GRUB_HIDDEN_TIMEOUT_QUIET=true
     GRUB_TIMEOUT=10
     GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
     GRUB_CMDLINE_LINUX=""
  
    # Uncomment to enable BadRAM filtering, modify to suit your needs
     # This works with Linux (no patch required) and with any kernel that obtains
     # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
     #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
  
    # Uncomment to disable graphical terminal (grub-pc only)
     #GRUB_TERMINAL=console
  
    # The resolution used on graphical terminal
     # note that you can use only modes which your graphic card supports via VBE
     # you can see them in real GRUB with the command `vbeinfo'
     #GRUB_GFXMODE=640x480
  
    # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
     #GRUB_DISABLE_LINUX_UUID=true
  
    # Uncomment to disable generation of recovery mode menu entries
     #GRUB_DISABLE_RECOVERY="true"
  
    # Uncomment to get a beep at grub start
     #GRUB_INIT_TUNE="480 440 1"
  
 
 
    /boot/efi detected in the fstab of nvme0n1p5: UUID=6A65-4C30   (nvme0n1p2)
     =================== No kernel in /mnt/boot-sav/sdb1/boot:
     grub
  
 
 
    =================== efibootmgr -v
     BootCurrent: 0002
     Timeout: 1 seconds
     BootOrder: 0002,0001,0003,0004,0000
     Boot0000* Windows Boot Manager    HD(2,e1800,31800,770b20e8-445d-4eca-8ea1-f90640a7687d)File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
     Boot0001* Hard Drive    BIOS(2,0,00)..GO..NO........o.W.D.C. .W.D.3.0.E.Z.R.X.-.0.0.S.P.E.B.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.4.C.3.E.X.D.H.P.X.E........BO..NO..........N.1.-.S.a.m.s.u.n.g. .S.S.D. .9.5.0. .P.R.O. .2.5.6.G.B....................A........................1.N........>.;.....................N..Gd-.;.A..MQ..L.N.1.-.S.a.m.s.u.n.g. .S.S.D. .9.5.0. .P.R.O. .2.5.6.G.B........BO
     Boot0002* ubuntu    HD(2,e1800,31800,770b20e8-445d-4eca-8ea1-f90640a7687d)File(EFIUBUNTUSHIMX64.EFI)
     Boot0003* UEFI: SanDisk USB Ultra 1100, Partition 1    ACPI(a0341d0,0)PCI(14,0)USB(2,0)HD(1,800,1dd7800,0003c18d)..BO
     Boot0004* USB    BIOS(2,0,00)..GO..NO........s.S.a.n.D.i.s.k. .U.S.B. .U.l.t.r.a. .1.1.0.0....................A.......................F..Gd-.;.A..MQ..L.V.C.0.0.0.1.1.5.0.4.2.0.1.5.4.0.3.0.0.0.0.3.3.2........BO
  
    =================== UEFI/Legacy mode:
     BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
     SecureBoot enabled.
  
 
    =================== PARTITIONS & DISKS:
     nvme0n1p1    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/nvme0n1p1.
     nvme0n1p2    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot/efi.
     nvme0n1p4    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1p4.
     nvme0n1p5    : nvme0n1,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /.
     nvme0n1p7    : nvme0n1,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.
     sda1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /donnees.
     sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.
  
    nvme0n1    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
     sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
     sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     liveusb,    no-os,    2048 sectors * 512 bytes
  
 
    =================== parted -l:
  
    Model: ATA WDC WD30EZRX-00S (scsi)
     Disk /dev/sda: 3001GB
     Sector size (logical/physical): 512B/4096B
     Partition Table: gpt
  
    Number  Start   End     Size    File system  Name  Flags
     1      1049kB  3001GB  3001GB  ext4
  
 
    Model: SanDisk USB Ultra (scsi)
     Disk /dev/sdb: 16.0GB
     Sector size (logical/physical): 512B/512B
     Partition Table: msdos
  
    Number  Start   End     Size    Type     File system  Flags
     1      1049kB  16.0GB  16.0GB  primary  fat32        boot
  
 
    Model: Unknown (unknown)
     Disk /dev/nvme0n1: 256GB
     Sector size (logical/physical): 512B/512B
     Partition Table: gpt
  
    Number  Start   End    Size    File system     Name                          Flags
     1      1049kB  473MB  472MB   ntfs            Basic data partition          hidden, diag
     2      473MB   577MB  104MB   fat32           EFI system partition          boot
     3      577MB   593MB  16.8MB                  Microsoft reserved partition  msftres
     4      593MB   105GB  104GB   ntfs            Basic data partition          msftdata
     5      105GB   120GB  15.0GB  ext4
     6      120GB   130GB  10.0GB  linux-swap(v1)
     7      130GB   256GB  126GB   ext4
  
    =================== parted -lm:
  
    BYT;
     /dev/sda:3001GB:scsi:512:4096:gpt:ATA WDC WD30EZRX-00S;
     1:1049kB:3001GB:3001GB:ext4::;
  
    BYT;
     /dev/sdb:16.0GB:scsi:512:512:msdos:SanDisk USB Ultra;
     1:1049kB:16.0GB:16.0GB:fat32::boot;
  
    BYT;
     /dev/nvme0n1:256GB:unknown:512:512:gpt:Unknown;
     1:1049kB:473MB:472MB:ntfs:Basic data partition:hidden, diag;
     2:473MB:577MB:104MB:fat32:EFI system partition:boot;
     3:577MB:593MB:16.8MB::Microsoft reserved partition:msftres;
     4:593MB:105GB:104GB:ntfs:Basic data partition:msftdata;
     5:105GB:120GB:15.0GB:ext4::;
     6:120GB:130GB:10.0GB:linux-swap(v1)::;
     7:130GB:256GB:126GB:ext4::;
  
    =================== lsblk:
     KNAME     TYPE FSTYPE    SIZE LABEL
     sda       disk           2,7T
     sda1      part ext4      2,7T
     sdb       disk iso9660  14,9G Linux Mint 17.2 Cinnamon 64-bit
     sdb1      part vfat     14,9G Clé USB
     nvme0n1   disk         238,5G
     nvme0n1p1 part ntfs      450M Récupération
     nvme0n1p2 part vfat       99M
     nvme0n1p3 part            16M
     nvme0n1p4 part ntfs     97,1G
     nvme0n1p5 part ext4       14G racine_linux
     nvme0n1p6 part swap      9,3G
     nvme0n1p7 part ext4    117,5G
  
    KNAME     ROTA RO RM STATE   MOUNTPOINT
     sda          1  0  0 running
     sda1         1  0  0         /donnees
     sdb          1  0  1 running
     sdb1         1  0  1         /mnt/boot-sav/sdb1
     nvme0n1      0  0  0
     nvme0n1p1    0  0  0         /mnt/boot-sav/nvme0n1p1
     nvme0n1p2    0  0  0         /boot/efi
     nvme0n1p3    0  0  0
     nvme0n1p4    0  0  0         /mnt/boot-sav/nvme0n1p4
     nvme0n1p5    0  0  0         /
     nvme0n1p6    0  0  0         [SWAP]
     nvme0n1p7    0  0  0         /home
  
 
    =================== mount:
     /dev/nvme0n1p5 on / type ext4 (rw,errors=remount-ro)
     proc on /proc type proc (rw,noexec,nosuid,nodev)
     sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
     none on /sys/fs/cgroup type tmpfs (rw)
     none on /sys/fs/fuse/connections type fusectl (rw)
     none on /sys/kernel/debug type debugfs (rw)
     none on /sys/kernel/security type securityfs (rw)
     none on /sys/firmware/efi/efivars type efivarfs (rw)
     udev on /dev type devtmpfs (rw,mode=0755)
     devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
     tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
     none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
     none on /run/shm type tmpfs (rw,nosuid,nodev)
     none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
     none on /sys/fs/pstore type pstore (rw)
     /dev/nvme0n1p7 on /home type ext4 (rw)
     /dev/nvme0n1p2 on /boot/efi type vfat (rw)
     /dev/sda1 on /donnees type ext4 (rw)
     systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
     /dev/nvme0n1p1 on /mnt/boot-sav/nvme0n1p1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
     /dev/nvme0n1p4 on /mnt/boot-sav/nvme0n1p4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
     /dev/sdb1 on /mnt/boot-sav/sdb1 type vfat (rw)
  
 
    =================== ls:
     /sys/block/nvme0n1 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight mq nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 nvme0n1p6 nvme0n1p7 power queue range removable ro size slaves stat subsystem trace uevent
     /sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
     /sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
     /dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 input kmsg log mapper mcelog mem memory_bandwidth net network_latency network_throughput null nvidia0 nvidiactl nvme0 nvme0n1 nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 nvme0n1p6 nvme0n1p7 port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb vfio vga_arbiter vhci vhost-net zero
     ls /dev/mapper:  control
  
    =================== hexdump -n512 -C /dev/nvme0n1p1
     00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
     00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
     00000020  00 00 00 00 80 00 80 00  ff 0f 0e 00 00 00 00 00  |................|
     00000030  00 96 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
     00000040  f6 00 00 00 01 00 00 00  97 7c 64 88 90 64 88 8a  |.........|d..d..|
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
  
    =================== hexdump -n512 -C /dev/nvme0n1p2
     00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 0e 1a  |.X.MSDOS5.0.....|
     00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 18 0e 00  |........?.......|
     00000020  00 18 03 00 f9 02 00 00  00 00 00 00 02 00 00 00  |................|
     00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
     00000040  80 01 29 30 4c 65 6a 4e  4f 20 4e 41 4d 45 20 20  |..)0LejNO NAME  |
     00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
     00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
     00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
     00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
     00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
     000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
     000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
     000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
     000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
     000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
     000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
     00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
     00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
     00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
     00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
     00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
     00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
     00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
     00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
     00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
     *
     000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
     000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
     000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
     000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
     000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
     000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
     00000200
  
    =================== hexdump -n512 -C /dev/nvme0n1p4
     00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
     00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b0 11 00  |........?.......|
     00000020  00 00 00 00 80 00 80 00  ff 4f 23 0c 00 00 00 00  |.........O#.....|
     00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
     00000040  f6 00 00 00 01 00 00 00  36 ba 75 4a da 75 4a d4  |........6.uJ.uJ.|
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
     ls sdb1/efi: /BOOT/grubx64.efi /BOOT/BOOTx64.EFI
     ls sdb1: boot
     casper
     dists
     EFI
     isolinux
     ldlinux.sys
     MD5SUMS
     menu.c32
     pool
     preseed
     README.diskdefines
     syslinux.cfg
     System Volume Information
     ubnfilel.txt
     ubninit
     ubnkern
     ubnpathl.txt  . Veuillez indiquer ce message à boot.repair@gmail.com
     ls /boot/efi/efi : Boot
     Microsoft
     ubuntu
     Error efitmp. Veuillez indiquer ce message à boot.repair@gmail.com
  
    =================== hexdump -n512 -C /dev/sdb1
     00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 20 00  |.X.SYSLINUX... .|
     00000010  02 00 00 00 00 f8 00 00  20 00 40 00 00 08 00 00  |........ .@.....|
     00000020  00 78 dd 01 a1 3b 00 00  00 00 00 00 02 00 00 00  |.x...;..........|
     00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
     00000040  80 01 29 5d d6 d6 64 43  6c c3 a9 20 55 53 42 20  |..)]..dCl.. USB |
     00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
     00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
     00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
     00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
     00000090  88 4d f8 50 50 50 50 cd  13 eb 62 8b 55 aa 8b 75  |.M.PPPP...b.U..u|
     000000a0  a8 c1 ee 04 01 f2 83 fa  4f 76 31 81 fa b2 07 73  |........Ov1....s|
     000000b0  2b f6 45 b4 7f 75 25 38  4d b8 74 20 66 3d 21 47  |+.E..u%8M.t f=!G|
     000000c0  50 54 75 10 80 7d b8 ed  75 0a 66 ff 75 ec 66 ff  |PTu..}..u.f.u.f.|
     000000d0  75 e8 eb 0f 51 51 66 ff  75 bc eb 07 51 51 66 ff  |u...QQf.u...QQf.|
     000000e0  36 1c 7c b4 08 e8 e9 00  72 13 20 e4 75 0f c1 ea  |6.|.....r. .u...|
     000000f0  08 42 89 16 1a 7c 83 e1  3f 89 0e 18 7c fb bb aa  |.B...|..?...|...|
     00000100  55 b4 41 e8 cb 00 72 10  81 fb 55 aa 75 0a f6 c1  |U.A...r...U.u...|
     00000110  01 74 05 c6 06 46 7d 00  66 b8 82 50 35 00 66 ba  |.t...F}.f..P5.f.|
     00000120  00 00 00 00 bb 00 80 e8  0e 00 66 81 3e 1c 80 8a  |..........f.>...|
     00000130  99 61 6c 75 74 e9 f8 02  66 03 06 60 7b 66 13 16  |.alut...f..`{f..|
     00000140  64 7b b9 10 00 eb 2b 66  52 66 50 06 53 6a 01 6a  |d{....+fRfP.Sj.j|
     00000150  10 89 e6 66 60 b4 42 e8  77 00 66 61 8d 64 10 72  |...f`.B.w.fa.d.r|
     00000160  01 c3 66 60 31 c0 e8 68  00 66 61 e2 da c6 06 46  |..f`1..h.fa....F|
     00000170  7d 2b 66 60 66 0f b7 36  18 7c 66 0f b7 3e 1a 7c  |}+f`f..6.|f..>.||
     00000180  66 f7 f6 31 c9 87 ca 66  f7 f7 66 3d ff 03 00 00  |f..1...f..f=....|
     00000190  77 17 c0 e4 06 41 08 e1  88 c5 88 d6 b8 01 02 e8  |w....A..........|
     000001a0  2f 00 66 61 72 01 c3 e2  c9 31 f6 8e d6 bc 68 7b  |/.far....1....h{|
     000001b0  8e de 66 8f 06 78 00 be  da 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
     000001c0  0e bb 07 00 cd 10 eb f2  31 c0 cd 16 cd 19 f4 eb  |........1.......|
     000001d0  fd 8a 16 74 7b 06 cd 13  07 c3 42 6f 6f 74 20 65  |...t{.....Boot e|
     000001e0  72 72 6f 72 0d 0a 00 00  00 00 00 00 00 00 00 00  |rror............|
     000001f0  00 00 00 00 00 00 00 00  fe 02 b2 3e 18 37 55 aa  |...........>.7U.|
     00000200
  
    WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util fdisk doesn't support GPT. Use GNU Parted.
  
 
    WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
  
 
    =================== df -Th:
  
    Filesystem     Type      Size  Used Avail Use% Mounted on
     udev           devtmpfs  7.8G   12K  7.8G   1% /dev
     tmpfs          tmpfs     1.6G  1.8M  1.6G   1% /run
     /dev/nvme0n1p5 ext4       14G  7.2G  5.8G  56% /
     none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
     none           tmpfs     5.0M     0  5.0M   0% /run/lock
     none           tmpfs     7.8G  1.3M  7.8G   1% /run/shm
     none           tmpfs     100M   20K  100M   1% /run/user
     /dev/nvme0n1p7 ext4      116G  917M  109G   1% /home
     /dev/nvme0n1p2 vfat       95M   30M   66M  31% /boot/efi
     /dev/sda1      ext4      2.7T  455G  2.2T  18% /donnees
     /dev/nvme0n1p1 fuseblk   450M  299M  152M  67% /mnt/boot-sav/nvme0n1p1
     /dev/nvme0n1p4 fuseblk    98G   61G   37G  63% /mnt/boot-sav/nvme0n1p4
     /dev/sdb1      vfat       15G  1.7G   14G  12% /mnt/boot-sav/sdb1
  
    =================== fdisk -l:
  
    Disk /dev/nvme0n1: 256.1 GB, 256060514304 bytes
     255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
     Units = sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
     Disk identifier: 0x00000000
  
    Device Boot      Start         End      Blocks   Id  System
     /dev/nvme0n1p1               1   500118191   250059095+  ee  GPT
  
    Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
     255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
     Units = sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
     Disk identifier: 0x00000000
  
    Device Boot      Start         End      Blocks   Id  System
     /dev/sda1               1  4294967295  2147483647+  ee  GPT
     Partition 1 does not start on physical sector boundary.
  
    Disk /dev/sdb: 16.0 GB, 16025444352 bytes
     255 heads, 63 sectors/track, 1948 cylinders, total 31299696 sectors
     Units = sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
     Disk identifier: 0x0003c18d
  
    Device Boot      Start         End      Blocks   Id  System
     /dev/sdb1   *        2048    31293439    15645696    b  W95 FAT32
  
 
 
 
    =================== Suggested repair
     The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of nvme0n1p5, using the following options:        nvme0n1p2/boot/efi,
     Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file
  
 
    =================== Blockers in case of suggested repair
     Veuillez utiliser ce logiciel dans une session-live (live-CD ou live-USB). Cela vous permettra d'utiliser cette fonctionnalité.
  
 
    =================== Advice in case of suggested repair
     Veuillez désactiver SecureBoot dans le BIOS. Puis réessayez.Voulez-vous continuer ?
  
 
    =================== Final advice in case of suggested repair
     N'oubliez pas de régler votre BIOS pour qu'il amorce sur le disque nvme0n1 (256GB) !
  
    Les fichiers de démarrage de [Linux] sont loin du début du disque. Votre BIOS pourrait ne pas les détecter. Vous voudrez peut-être re-essayer après avoir créé une partition /boot (EXT4, >200MB, en début de disque). Cela peut être réalisé via des outils tels que gParted. Puis sélectionnez cette partition via l'option [Partition /boot séparée :] de [Boot-Repair]. (http://doc.ubuntu-fr.org/tutoriel/partition_boot)
  
    Si votre ordinateur redémarre directement sur Windows, essayez de changer l'ordre de démarrage dans votre BIOS.
     Si votre BIOS ne permet pas de changer l'ordre de démarrage, changez l'entrée de démarrage par défaut de l'amorceur Windows.
     Par exemple, vous pouvez démarrer Windows, puis saisir la commande suivante dans une invite de commande en mode administrateur :
     bcdedit /set {bootmgr} path \EFI\...\grub*.efi
  
 
    =================== User settings

```

If you have some idea :)

---

### Post by QIII on 2016-02-17
*Moved to **MINT***

---

