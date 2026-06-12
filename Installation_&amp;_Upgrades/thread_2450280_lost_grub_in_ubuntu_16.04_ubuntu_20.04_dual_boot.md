---
title: "lost grub in ubuntu 16.04 /ubuntu 20.04 dual boot"
date: 2020-09-10
forum: Installation &amp; Upgrades
---

### Post by bustamanteguevara on 2020-09-10
Hi all, 

I had ubuntu 16.04 in my DELL, and I installed a new partition with ubuntu 20.04, to keep the functionality of the old system until I can fully migrate to 20.04. 

I started the old 16.04 system, and now I cannot come back to the 20.04 one. It is hard to access the grub menu, and when I access it, it doesn't have the option to go to ubuntu 20.04.

Are there any suggestions? 

Things I have tried: 

- go to the boot menu (there is not an option to go to the second partition)
- edit the /etc/default/grub file and "update-grub" after. 

Cheers

---

### Post by CelticWarrior on 2020-09-10
Properly installed, i.e., both Ubuntus installed in the same mode, it just works. It doesn0't matter much who's in control of Grub.
Doing 'sudo update-grub' should have been enough to detect both and give you the expected options in the Grub menu. If it never worked then likely you installed in different modes.

---

### Post by bustamanteguevara on 2020-09-10
Thanks for the reply. 

Grub to both OS used to work before. It unexpectedly stopped working. 

Here is the output of ' sudo update-grub' 

user@user-Latitude-5491:~$ sudo update-grub
[sudo] password for user: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.15.0-117-generic
Found initrd image: /boot/initrd.img-4.15.0-117-generic
Found linux image: /boot/vmlinuz-4.15.0-115-generic
Found initrd image: /boot/initrd.img-4.15.0-115-generic
Found linux image: /boot/vmlinuz-4.15.0-112-generic
Found initrd image: /boot/initrd.img-4.15.0-112-generic
Found linux image: /boot/vmlinuz-4.13.0-1031-oem
Found initrd image: /boot/initrd.img-4.13.0-1031-oem
Found linux image: /boot/vmlinuz-4.13.0-1021-oem
Found initrd image: /boot/initrd.img-4.13.0-1021-oem
Adding boot menu entry for EFI firmware configuration
done
user@user-Latitude-5491:~$

---

### Post by CelticWarrior on 2020-09-10
Please try [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not do any repirs at this point. Just "Create a BootInfo summary" and post it here.

---

### Post by bustamanteguevara on 2020-09-11
Here is the report from boot-repair


```
boot-repair-4ppa125                                              [20200911_1943]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/Boot/shimx64.efi /efi/ubuntu/fwupdx64.efi 
                       /efi/ubuntu/fwupx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.7 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1:   Ubuntu 16.04.7 LTS on sda3
OS#2:   Ubuntu 20.04.1 LTS on sda5

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04 LTS, focal, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled.

efibootmgr -v
BootCurrent: 0010
Timeout: 0 seconds
BootOrder: 0006,000F,0007,0009,000A,000B,000C,0010,0011
Boot0000* Windows Boot Manager    HD(3,GPT,d275eaef-ca62-426c-a817-ff069b93e96c,0xafa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................
Boot0001* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0002* USB Storage Device    BBS(USB,USB Storage Device,0x0)..BO
Boot0003* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot0004* Onboard NIC    BBS(Network,IBA CL Slot 00FE v0113,0x0)..BO
Boot0005* UEFI: Micron 1100 SATA 512GB, Partition 1    HD(1,GPT,29e931ac-cfd2-4a40-9f1f-df9ff84c8d69,0x800,0x177000)/File(\EFI\boot\bootx64.efi)..BO
Boot0006* ubuntu    HD(1,GPT,29e931ac-cfd2-4a40-9f1f-df9ff84c8d69,0x800,0x177000)/File(\EFI\ubuntu\shimx64.efi)
Boot0007* Linux Firmware Updater    HD(1,GPT,29e931ac-cfd2-4a40-9f1f-df9ff84c8d69,0x800,0x177000)/File(\EFI\ubuntu\fwupdx64.efi)
Boot0009* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot000A* USB Storage Device    BBS(USB,KingstonDataTraveler 3.0,0x0)..BO
Boot000B* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot000C* Onboard NIC    BBS(Network,IBA CL Slot 00FE v0113,0x0)..BO
Boot000F* UEFI: Micron 1100 SATA 512GB, Partition 1    HD(1,GPT,29e931ac-cfd2-4a40-9f1f-df9ff84c8d69,0x800,0x177000)/File(\EFI\boot\bootx64.efi)..BO
Boot0010* UEFI: KingstonDataTraveler 3.0    PciRoot(0x0)/Pci(0x14,0x0)/USB(16,0)/CDROM(1,0x406eb0,0x7c00)..BO
Boot0011* UEFI: KingstonDataTraveler 3.0, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(16,0)/HD(2,MBR,0x15f006ae,0x406eb0,0x1f00)..BO

bed45d1c9554cea09924d3814cb7c446   sda1/Boot/fbx64.efi
4487628005555bfd4a4c0a47211e0700   sda1/Boot/mmx64.efi
ded965934506efb38a6dcb9ac5b2b79e   sda1/Boot/shimx64.efi
6fe629a8718cc7afb33f6d2a59476ee0   sda1/ubuntu/fwupdx64.efi
82894bcbe4f010664226ba7591372538   sda1/ubuntu/fwupx64.efi
e3ea9d4e5e486bf6ec48c0236883d0e0   sda1/ubuntu/grubx64.efi
4487628005555bfd4a4c0a47211e0700   sda1/ubuntu/mmx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sda1/ubuntu/shimx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sda1/Boot/BOOTX64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda3    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda5    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: 6A347033-C241-4104-A308-FDF2766A4587
          Start        End   Sectors   Size Type
sda1       2048    1538047   1536000   750M EFI System
sda2    1538048   12023807  10485760     5G Microsoft reserved
sda3   12023808  536230364 524206557   250G Linux filesystem
sda4  933939200 1000214527  66275328  31.6G Linux swap
sda5  536231936  933939199 397707264 189.7G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 14.42 GiB, 15472047104 bytes, 30218842 sectors
Disk identifier: 0x15f006ae
      Boot   Start      End  Sectors  Size Id Type
sdb1  *          0  5303231  5303232  2.5G  0 Empty
sdb2       4222640  4230575     7936  3.9M ef EFI (FAT-12/16/32)
sdb3       5304320 30218841 24914522 11.9G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:512GB:scsi:512:4096:gpt:ATA Micron 1100 SATA:;
1:1049kB:787MB:786MB:fat32:EFI system partition:boot, esp;
2:787MB:6156MB:5369MB:fat32:Basic data partition:msftres;
3:6156MB:275GB:268GB:ext4::;
5:275GB:478GB:204GB:ext4::;
4:478GB:512GB:33.9GB:linux-swap(v1)::swap;
sdb:15.5GB:scsi:512:512:unknown:Kingston DataTraveler 3.0:;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9500;&#9472;sda1 vfat     1048-EE0A                            29e931ac-cfd2-4a40-9f1f-df9ff84c8d69 ESP                    EFI system partition
&#9500;&#9472;sda2 vfat     8E78-7D4C                            58c70def-1118-420f-915f-85546cf6632f OS                     Basic data partition
&#9500;&#9472;sda3 ext4     2083dfcd-b404-4264-b3c2-8e179c696b02 276c7c0a-65ea-4b4d-a29f-fc9b1e3bd81d UBUNTU                 
&#9500;&#9472;sda4 swap     c95332f5-8a37-4f30-b441-7886254198c7 29e7351c-f141-48d2-9125-7a7912b68b85                        
&#9492;&#9472;sda5 ext4     2bbfd9a9-ac33-48b6-bef5-fe7f057f0db0 8d2c72b1-4bbb-4ef0-9de0-e0ae7dc32dd3                        
sdb    iso9660  2020-04-23-07-51-42-00                                                    Ubuntu 20.04 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2020-04-23-07-51-42-00               15f006ae-01                          Ubuntu 20.04 LTS amd64 
&#9500;&#9472;sdb2 vfat     1AC3-20ED                            15f006ae-02                                                 
&#9492;&#9472;sdb3 ext4     4365d8bd-7a30-4492-aa91-aab687236250 15f006ae-03                          writable               

df (filtered): _________________________________________________________________

                                                          Avail Use% Mounted on
disk/by-label/writable[/install-logs-2020-09-11.0/crash]    11G   0% /var/crash
disk/by-label/writable[/install-logs-2020-09-11.0/log]      11G   0% /var/log
sda1                                                     701.1M   6% /mnt/boot-sav/sda1
sda3                                                      38.7G  79% /mnt/boot-sav/sda3
sda5                                                     118.2G  31% /mnt/boot-sav/sda5
sdb1                                                          0 100% /cdrom

Mount options: __________________________________________________________________

disk/by-label/writable[/install-logs-2020-09-11.0/crash] rw,relatime
disk/by-label/writable[/install-logs-2020-09-11.0/log]   rw,relatime
sda1                                                     rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda3                                                     rw,relatime
sda5                                                     rw,relatime
sdb1                                                     ro,noatime,nojoliet,check=s,map=n,blocksize=2048

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 2083dfcd-b404-4264-b3c2-8e179c696b02 root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Install Complete, remove media and reboot.
Dell Recovery
Dell Recovery (safe graphics mode)

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

====================== sda3/boot/grub/grub.cfg (filtered) ======================

Ubuntu   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.15.0-117-generic   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.15.0-117-generic (upstart)   gnulinux-4.15.0-117-generic-init-upstart-2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.15.0-115-generic   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.15.0-115-generic (upstart)   gnulinux-4.15.0-115-generic-init-upstart-2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.13.0-1031-oem   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.13.0-1031-oem (upstart)   gnulinux-4.13.0-1031-oem-init-upstart-2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.13.0-1021-oem   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.13.0-1021-oem (upstart)   gnulinux-4.13.0-1021-oem-init-upstart-2083dfcd-b404-4264-b3c2-8e179c696b02
### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###
Restore OS to factory state

========================== sda3/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=2083dfcd-b404-4264-b3c2-8e179c696b02 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=1048-EE0A  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda4 during installation
UUID=c95332f5-8a37-4f30-b441-7886254198c7 none            swap    sw              0       0

======================= sda3/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true

==================== sda3: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  49.243183136 = 52.874465280   boot/grub/grub.cfg                             1
   8.885910034 = 9.541173248    boot/vmlinuz-4.13.0-1021-oem                   1
   8.896831512 = 9.552900096    boot/vmlinuz-4.13.0-1021-oem.efi.signed        1
   9.615585327 = 10.324656128   boot/vmlinuz-4.13.0-1031-oem                   1
   9.685901642 = 10.400157696   boot/vmlinuz-4.13.0-1031-oem.efi.signed        1
 135.777629852 = 145.790119936  boot/vmlinuz-4.15.0-115-generic                1
 191.463584900 = 205.582458880  boot/vmlinuz-4.15.0-117-generic                1
 191.463584900 = 205.582458880  vmlinuz                                        1
 135.777629852 = 145.790119936  vmlinuz.old                                    1
 177.199264526 = 190.266261504  boot/initrd.img-4.13.0-1021-oem                3
 175.174263000 = 188.091932672  boot/initrd.img-4.13.0-1031-oem                2
 188.209938049 = 202.088882176  boot/initrd.img-4.15.0-115-generic             6
 156.389625549 = 167.922081792  boot/initrd.img-4.15.0-117-generic             5
 156.389625549 = 167.922081792  initrd.img                                     5
 188.209938049 = 202.088882176  initrd.img.old                                 6

===================== sda3: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 12627 Aug 25 08:24 10_linux
-rwxr-xr-x 1 root root 11082 Oct 12  2017 20_linux_xen
-rwxr-xr-x 1 root root 11692 Oct 12  2017 30_os-prober
-rwxr-xr-x 1 root root  1418 Oct 12  2017 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 12  2017 40_custom
-rwxr-xr-x 1 root root   216 Oct 12  2017 41_custom
-rwxr-xr-x 1 root root  1245 Jan 17  2019 99_dell_recovery

======================= sda3/etc/grub.d/99_dell_recovery =======================

#!/bin/bash -e
source /usr/lib/grub/grub-mkconfig_lib
cat << EOF
menuentry "Restore OS to factory state" {
        search --no-floppy --hint '(hd0,gpt2)' --set --fs-uuid 8E78-7D4C
        set uuid_options="uuid=8E78-7D4C"
        if [ -s /factory/common.cfg ]; then
            source /factory/common.cfg
        else
            set options="boot=casper automatic-ubiquity noprompt quiet splash nomodeset"
        fi
        if [ -s /factory/post-rts-gfx.cfg ]; then
            source /factory/post-rts-gfx.cfg
        fi
        if [ -s /factory/post-rts-wlan.cfg ]; then
            source /factory/post-rts-wlan.cfg
        fi
        #Support starting from a loopback mount (Only support ubuntu.iso for filename)
        if [ -f /ubuntu.iso ]; then
            loopback loop /ubuntu.iso
            set root=(loop)
            set options="\$options iso-scan/filename=/ubuntu.iso"
        fi
        if [ -n "\${lang}" ]; then
            set options="\$options locale=\$lang"
        fi
        if [ -s /factory/dual_enable ]; then
            set options="\$options dell-recovery/dual_boot=true"
        fi 
        linux   /casper/vmlinuz.efi dell-recovery/recovery_type=hdd \$uuid_options \$options
    initrd    /casper/initrd.lz
}
EOF

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   2bbfd9a9-ac33-48b6-bef5-fe7f057f0db0
Ubuntu, with Linux 5.4.0-47-generic   2bbfd9a9-ac33-48b6-bef5-fe7f057f0db0
Ubuntu, with Linux 5.4.0-45-generic   2bbfd9a9-ac33-48b6-bef5-fe7f057f0db0
Ubuntu, with Linux 5.4.0-42-generic   2bbfd9a9-ac33-48b6-bef5-fe7f057f0db0
Ubuntu 16.04.6 LTS (16.04) (on sda3)   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu (on sda3)   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.15.0-112-generic (on sda3)   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.15.0-112-generic (upstart) (on sda3)   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.15.0-107-generic (on sda3)   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.15.0-107-generic (upstart) (on sda3)   2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.13.0-1031-oem (on sda3)   efi.signed--2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.13.0-1031-oem (upstart) (on sda3)   efi.signed--2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.13.0-1021-oem (on sda3)   efi.signed--2083dfcd-b404-4264-b3c2-8e179c696b02
Ubuntu, with Linux 4.13.0-1021-oem (upstart) (on sda3)   efi.signed--2083dfcd-b404-4264-b3c2-8e179c696b02
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=2bbfd9a9-ac33-48b6-bef5-fe7f057f0db0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=1048-EE0A  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 335.926757812 = 360.698609664  boot/grub/grub.cfg                             3
 290.737430573 = 312.176939008  boot/vmlinuz                                   1
 399.948360443 = 429.441282048  boot/vmlinuz-5.4.0-42-generic                  1
 280.940555573 = 301.657624576  boot/vmlinuz-5.4.0-45-generic                  1
 290.737430573 = 312.176939008  boot/vmlinuz-5.4.0-47-generic                  1
 280.940555573 = 301.657624576  boot/vmlinuz.old                               1
 433.775131226 = 465.762500608  boot/initrd.img                                3
 291.452377319 = 312.944607232  boot/initrd.img-5.4.0-42-generic               4
 291.421138763 = 312.911065088  boot/initrd.img-5.4.0-45-generic               2
 433.775131226 = 465.762500608  boot/initrd.img-5.4.0-47-generic               3
 291.421138763 = 312.911065088  boot/initrd.img.old                            2

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 17622 Aug 17 14:04 10_linux
-rwxr-xr-x 1 root root 42359 Aug 17 14:04 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Apr 15 11:31 20_linux_xen
-rwxr-xr-x 1 root root 12059 Apr 15 11:31 30_os-prober
-rwxr-xr-x 1 root root  1424 Apr 15 11:31 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 15 11:31 40_custom
-rwxr-xr-x 1 root root   216 Apr 15 11:31 41_custom


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  c4 20 40 00 00 00 00 00  ae 06 f0 15 00 00 80 00  |. @.............|
000001c0  01 00 00 a1 e0 fe 00 00  00 00 c0 eb 50 00 00 fe  |............P...|
000001d0  ff ff ef fe ff ff b0 6e  40 00 00 1f 00 00 00 2d  |.......n@......-|
000001e0  64 4a 83 09 ca 59 00 f0  50 00 5a 2a 7c 01 00 00  |dJ...Y..P.Z*|...|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
sda3,
using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s  use-standard-efi-file    

Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 16.04.7 LTS entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !
```

---

### Post by bustamanteguevara on 2020-09-11
I just asked boot-repair to perform the sugested repair and it worked. The grub is fixed.

---

