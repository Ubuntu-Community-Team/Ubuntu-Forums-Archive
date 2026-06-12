---
title: "After Ubuntu 20.04 installed, Windows does boot but not from Grub [closed]"
date: 2022-03-17
forum: Installation &amp; Upgrades
---

### Post by boubflo on 2022-03-17
I have installed Ubuntu 20.04 desktop on a Acer TravelMate TMB118  laptop alongside an existing Windows 10 install. After installation, booting the computer allow grub to boot Linux  without problem, but every time I choose booting Windows from the grub  menu, Windows does not boot and the computer just freeze.


 Going to the BIOS to make Windows boot first results in Windows booting without problems.

 
I tried "update-grub", repairing Windows boot with a live USB,  installing boot-repair on Linux, but still nothing changed. I have prepared several identical laptops with Windows/Ubuntu 20.04 dual  boot without having this problem before, so I just don't understand  what's going on this time.

 
Here is the content of the boot-repair log after scan :

 ```
boot-repair-4ppa200                                              [20220317_0854]

============================== Boot Info Summary ===============================

 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi /bootmgr

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


================================ 2 OS detected =================================

OS#1:   L'OS actuellement utilisé - Ubuntu 20.04.4 LTS CurrentSession on sda5
OS#2:   Windows 10 or 11 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: UHD Graphics 605 from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.13.0-35-generic root=UUID=0c46e8ff-f013-4229-a77f-797f9ef428d7 ro quiet splash vt.handoff=7
df -Th / : /dev/sda5        ext4   144G     10G  126G   8% /

===================================== UEFI =====================================

BIOS/UEFI firmware: V1.22(1.22) from Insyde Corp.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot enabled but mokutil says: SecureBoot enabled - Veuillez indiquer ce message à boot.repair@gmail.com.
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0000,0001,2001,2002,2003
Boot0000* Windows Boot Manager  HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...1................
Boot0001* Ubuntu    PciRoot(0x0)/Pci(0x12,0x0)/Sata(0,0,0)/HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)A01 ..
Boot0002* ubuntu    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM RC
Boot2003* EFI Network   RC


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda : is-GPT,   no-BIOSboot,    has---ESP,  not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,   grub2,  grub-install,   grubenv-ok, update-grub,    farbios
sda1    : no-os,    32, nopakmgr,   no-docgrub, nogrub, nogrubinstall,  no-grubenv, noupdategrub,   not-far
sda3    : is-os,    32, nopakmgr,   no-docgrub, nogrub, nogrubinstall,  no-grubenv, noupdategrub,   farbios
sda4    : no-os,    32, nopakmgr,   no-docgrub, nogrub, nogrubinstall,  no-grubenv, noupdategrub,   farbios

Partitions info (2/3): _________________________________________________________

sda5    : isnotESP, fstab-has-goodEFI,  no-nt,  no-winload, no-recov-nor-hid,   no-bmgr,    notwinboot
sda1    : is---ESP, part-has-no-fstab,  no-nt,  no-winload, no-recov-nor-hid,   bootmgr,    notwinboot
sda3    : isnotESP, part-has-no-fstab,  no-nt,  haswinload, no-recov-nor-hid,   bootmgr,    notwinboot
sda4    : isnotESP, part-has-no-fstab,  no-nt,  no-winload, recovery-or-hidden, no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda5    : not--sepboot, with-boot,  fstab-without-boot, not-sep-usr,    with--usr,  fstab-without-usr,  std-grub.d, sda
sda1    : not--sepboot, no---boot,  part-has-no-fstab,  not-sep-usr,    no---usr,   part-has-no-fstab,  no--grub.d, sda
sda3    : not--sepboot, no---boot,  part-has-no-fstab,  not-sep-usr,    no---usr,   part-has-no-fstab,  no--grub.d, sda
sda4    : not--sepboot, no---boot,  part-has-no-fstab,  not-sep-usr,    no---usr,   part-has-no-fstab,  no--grub.d, sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 626B8912-44DE-4AAC-83A0-08661DBB593C
          Start       End   Sectors   Size Type
sda1       2048    206847    204800   100M EFI System
sda2     206848    239615     32768    16M Microsoft reserved
sda3     239616 668520480 668280865 318.7G Microsoft basic data
sda4  975722496 976771071   1048576   512M Windows recovery environment
sda5  668522496 975722495 307200000 146.5G Linux filesystem
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:gpt:ATA CT500MX500SSD1:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:342GB:342GB:ntfs:Basic data partition:msftdata;
5:342GB:500GB:157GB:ext4::;
4:500GB:500GB:537MB:ntfs::hidden, diag;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                             
&#9500;&#9472;sda1 vfat     A61A-FBBB                            93160ae9-fe7f-4e90-84bc-3416eb250e06       EFI system partition
&#9500;&#9472;sda2                                               14461110-4e8b-4223-a507-4c5a78efc582       Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     D62A1C0B2A1BE6F1                     75e20abe-b526-425c-92c1-1f015bc634f2       Basic data partition
&#9500;&#9472;sda4 ntfs     26D0042BD00403B1                     6633297f-497f-4f32-bac9-d23be151ab90       
&#9492;&#9472;sda5 ext4     0c46e8ff-f013-4229-a77f-797f9ef428d7 72e838ac-7495-4265-97e6-629958e3d9a5       

Mount points (filtered): _______________________________________________________

                        Avail Use% Mounted on
/dev/sda3              298.4G   6% /mnt/boot-sav/sda3
/dev/sda4                 88M  83% /mnt/boot-sav/sda4
/dev/sda5              125.9G   7% /

Mount options (filtered): ______________________________________________________

/dev/sda3              fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4              fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5              ext4            rw,relatime,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 0c46e8ff-f013-4229-a77f-797f9ef428d7 root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   0c46e8ff-f013-4229-a77f-797f9ef428d7
Ubuntu, avec Linux 5.13.0-35-generic   0c46e8ff-f013-4229-a77f-797f9ef428d7
Ubuntu, avec Linux 5.8.0-43-generic   0c46e8ff-f013-4229-a77f-797f9ef428d7
Windows Boot Manager (sur sda1)   osprober-efi-A61A-FBBB
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=0c46e8ff-f013-4229-a77f-797f9ef428d7 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=A61A-FBBB  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 347,157329559 = 372,757344256  boot/grub/grub.cfg                             2
 464,535839081 = 498,791559168  boot/vmlinuz                                   1
 464,535839081 = 498,791559168  boot/vmlinuz-5.13.0-35-generic                 1
 323,495113373 = 347,350233088  boot/vmlinuz-5.8.0-43-generic                  2
 323,495113373 = 347,350233088  boot/vmlinuz.old                               2
 326,604488373 = 350,688899072  boot/initrd.img                                4
 326,604488373 = 350,688899072  boot/initrd.img-5.13.0-35-generic              4
 326,279045105 = 350,339457024  boot/initrd.img-5.8.0-43-generic               2
 326,279045105 = 350,339457024  boot/initrd.img.old                            2

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18151 Aug 12  2021 10_linux
-rwxr-xr-x 1 root root 42359 Jan 13  2021 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Jan 13  2021 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jan 13  2021 30_os-prober
-rwxr-xr-x 1 root root  1424 Jan 13  2021 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21 04:06 35_fwupd
-rwxr-xr-x 1 root root   214 Jan 13  2021 40_custom
-rwxr-xr-x 1 root root   216 Jan 13  2021 41_custom

=========================== sda5/etc/grub.d/35_fwupd ===========================

#! /bin/sh
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      . /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
    chainloader ${EFI_PATH}
}
EOF
      fi
fi



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
sda5,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

 Please use this software in a live-session (live-CD or live-USB). This will enable this feature.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the L'OS actuellement utilisé - Ubuntu 20.04.4 LTS CurrentSession entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\shim****.efi (**** will be updated in the final message)

``` 

Thanks in advance for your help !

---

### Post by tea for one on 2022-03-17
> BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.13.0-35-generic root=UUID=0c46e8ff-f013-4229-a77f-797f9ef428d7 ro quiet splash vt.handoff=7
df -Th / : /dev/sda5        ext4   144G     10G  126G   8% /
> Blockers in case of suggested repair: __________________________________________

 Please use this software in a live-session (live-CD or live-USB). This will enable this feature.

It looks like you need to use the boot-repair utility in a [COLOR="#0000FF"]live[/COLOR] session rather than from your installed Ubuntu 20.04 on sda5
The line numbers are missing from the report so it is difficult to show you the position of the text quoted above.

---

### Post by boubflo on 2022-03-17
Hello,

I tried boot-repair again within a live session :

```
boot-repair-4ppa200                                              [20220317_1051]

============================= Boot Repair Summary ==============================






Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda5,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file


Mount sda1 on /mnt/boot-sav/sda5/boot/efi

Unhide GRUB boot menu in sda5/etc/default/grub

================= Reinstall the grub-efi-amd64-signed of sda5 ==================

chroot /mnt/boot-sav/sda5 grub-install --version
grub-install (GRUB) 2.04-1ubuntu26.13
chroot /mnt/boot-sav/sda5 modprobe efivars

chroot /mnt/boot-sav/sda5 efibootmgr -v before grub install
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,0002,0000,0001,2001,2002,2003
Boot0000* Windows Boot Manager    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...1................
Boot0001* Ubuntu    PciRoot(0x0)/Pci(0x12,0x0)/Sata(0,0,0)/HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(EFIubuntushimx64.efi)A01 ..
Boot0002* ubuntu    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(EFIubuntushimx64.efi)
Boot0003* Linpus lite    HD(1,MBR,0x38b1c112,0x6a4,0x1f40)/File(EFIBootgrubx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

chroot /mnt/boot-sav/sda5 uname -r
5.8.0-43-generic

chroot /mnt/boot-sav/sda5 grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda5/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda5/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda5/boot/efi/efi/ubuntu/shimx64.efi /mnt/boot-sav/sda5/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/sda5/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda5/boot/efi/EFI/Boot/

chroot /mnt/boot-sav/sda5 grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.

chroot /mnt/boot-sav/sda5 efibootmgr -v after grub install
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,0003,0000,2001,2002,2003
Boot0000* Windows Boot Manager    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...1................
Boot0001* ubuntu    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(EFIubuntushimx64.efi)
Boot0003* Linpus lite    HD(1,MBR,0x38b1c112,0x6a4,0x1f40)/File(EFIBootgrubx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

chroot /mnt/boot-sav/sda5 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.13.0-35-generic
Found initrd image: /boot/initrd.img-5.13.0-35-generic
Found linux image: /boot/vmlinuz-5.8.0-43-generic
Found initrd image: /boot/initrd.img-5.8.0-43-generic
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings

Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Le démarrage de l'ordinateur a été correctement réparé.

Vous pouvez maintenant redémarrer votre ordinateur.
N'oubliez pas de faire démarrer votre firmware UEFI sur l'entrée Ubuntu 20.04.4 LTS (fichier sda1/efi/ubuntu/shimx64.efi) !
Si votre ordinateur redémarre directement dans Windows, essayez de changer l'ordre de démarrage dans votre firmware UEFI.
Si votre firmware UEFI ne permet pas de changer l'ordre de démarrage, changez l'entrée de démarrage par défaut de l'amorceur Windows.
Par exemple, vous pouvez démarrer Windows, puis saisir la commande suivante dans une invite de commande en mode administrateur :
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi


============================ Boot Info After Repair ============================

 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/grubx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi /bootmgr

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb déjà monté ou point de montage actif.


================================ 2 OS detected =================================

OS#1:   Ubuntu 20.04.4 LTS on sda5
OS#2:   Windows 10 or 11 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: UHD Graphics 605 from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.2 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: V1.22(1.22) from Insyde Corp.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled but mokutil says: SecureBoot enabled - Veuillez indiquer ce message à boot.repair@gmail.com.
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,0003,0000,2001,2002,2003
Boot0000* Windows Boot Manager    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...1................
Boot0001* ubuntu    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002  

728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bootx64.efi
85fa9d77b929ec4231aba29476574eb6   sda1/Boot/fbx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda1/Boot/grubx64.efi
469e608783843a701d172242f016c79c   sda1/Boot/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda1/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
e69be5ddc7c4165e0f3e5ee05d267ec2   sda1/Microsoft/Boot/bootmgfw.efi
5a0ceb06ab09d5c2be36b38bcb33617f   sda1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda4    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot
sda4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 626B8912-44DE-4AAC-83A0-08661DBB593C
          Start       End   Sectors   Size Type
sda1       2048    206847    204800   100M EFI System
sda2     206848    239615     32768    16M Microsoft reserved
sda3     239616 668520480 668280865 318.7G Microsoft basic data
sda4  975722496 976771071   1048576   512M Windows recovery environment
sda5  668522496 975722495 307200000 146.5G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 7.23 GiB, 7759462400 bytes, 15155200 sectors
Disk identifier: 0x38b1c112
      Boot   Start      End Sectors  Size Id Type
sdb1  *          0  5619583 5619584  2.7G  0 Empty
sdb2          1700     9699    8000  3.9M ef EFI (FAT-12/16/32)
sdb3       5619712 15155199 9535488  4.6G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:gpt:ATA CT500MX500SSD1:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:342GB:342GB:ntfs:Basic data partition:msftdata;
5:342GB:500GB:157GB:ext4::;
4:500GB:500GB:537MB:ntfs::hidden, diag;
sdb:7759MB:scsi:512:512:unknown: USB Flash Memory:;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                      PARTLABEL
sda                                                                                                                  
&#9500;&#9472;sda1 vfat     A61A-FBBB                            93160ae9-fe7f-4e90-84bc-3416eb250e06                            EFI system partition
&#9500;&#9472;sda2                                               14461110-4e8b-4223-a507-4c5a78efc582                            Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     D62A1C0B2A1BE6F1                     75e20abe-b526-425c-92c1-1f015bc634f2                            Basic data partition
&#9500;&#9472;sda4 ntfs     26D0042BD00403B1                     6633297f-497f-4f32-bac9-d23be151ab90                            
&#9492;&#9472;sda5 ext4     0c46e8ff-f013-4229-a77f-797f9ef428d7 72e838ac-7495-4265-97e6-629958e3d9a5                            
sdb    iso9660  2021-02-09-19-06-26-00                                                    Ubuntu 20.04.2.0 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2021-02-09-19-06-26-00               38b1c112-01                          Ubuntu 20.04.2.0 LTS amd64 
&#9500;&#9472;sdb2 vfat     54C5-9C6C                            38b1c112-02                                                     
&#9492;&#9472;sdb3 ext4     cb3982b6-4dcc-40f5-9dc7-10f2fcb47da3 38b1c112-03                          writable                   

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2022-03-17.1/crash]   4.1G   1% /var/crash
/dev/disk/by-label/writable[/install-logs-2022-03-17.1/log]     4.1G   1% /var/log
/dev/sda1                                                      44.9M  53% /mnt/boot-sav/sda1
/dev/sda3                                                     298.4G   6% /mnt/boot-sav/sda3
/dev/sda4                                                        88M  83% /mnt/boot-sav/sda4
/dev/sda5                                                     125.9G   7% /mnt/boot-sav/sda5
/dev/sdb1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/disk/by-label/writable[/install-logs-2022-03-17.1/crash] ext4            rw,relatime
/dev/disk/by-label/writable[/install-logs-2022-03-17.1/log]   ext4            rw,relatime
/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3                                                     fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4                                                     fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5                                                     ext4            rw,relatime
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 0c46e8ff-f013-4229-a77f-797f9ef428d7 root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   0c46e8ff-f013-4229-a77f-797f9ef428d7
Ubuntu, with Linux 5.13.0-35-generic   0c46e8ff-f013-4229-a77f-797f9ef428d7
Ubuntu, with Linux 5.8.0-43-generic   0c46e8ff-f013-4229-a77f-797f9ef428d7
Windows Boot Manager (on sda1)   osprober-efi-A61A-FBBB
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=0c46e8ff-f013-4229-a77f-797f9ef428d7 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=A61A-FBBB  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 318,776374817 = 342,283526144  boot/grub/grub.cfg                             1
 464,535839081 = 498,791559168  boot/vmlinuz                                   1
 464,535839081 = 498,791559168  boot/vmlinuz-5.13.0-35-generic                 1
 323,495113373 = 347,350233088  boot/vmlinuz-5.8.0-43-generic                  2
 323,495113373 = 347,350233088  boot/vmlinuz.old                               2
 326,604488373 = 350,688899072  boot/initrd.img                                4
 326,604488373 = 350,688899072  boot/initrd.img-5.13.0-35-generic              4
 326,279045105 = 350,339457024  boot/initrd.img-5.8.0-43-generic               2
 326,279045105 = 350,339457024  boot/initrd.img.old                            2

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18151 Aug 12  2021 10_linux
-rwxr-xr-x 1 root root 42359 Jan 13  2021 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Jan 13  2021 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jan 13  2021 30_os-prober
-rwxr-xr-x 1 root root  1424 Jan 13  2021 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21 03:06 35_fwupd
-rwxr-xr-x 1 root root   214 Jan 13  2021 40_custom
-rwxr-xr-x 1 root root   216 Jan 13  2021 41_custom

=========================== sda5/etc/grub.d/35_fwupd ===========================

#! /bin/sh
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      . /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
    chainloader ${EFI_PATH}
}
EOF
      fi
fi
```

The boot-info seems to indicate that everything's fine but I still have the same issue : Windows doesn't boot if I use the grub but does boot when I place it first in Bios boot order.

---

### Post by yancek on 2022-03-17
>  repairing Windows boot with a live USB 

What windows software did you use on the live USB to do this and what was the result?

You have windows in the MBR of the disk but it appears to be an EFI install as the EFI files to boot both Ubuntu and windows exist on the EFI partition (sda1).  You should have a chainloader entry for windows in //boot/grub/grub.cfg and it should be pointing to the windows file bootmgfw.efi.  Does that line exist?  One other possibility is that windows is hibernated and the Grub bootloader will not boot a hibernated partition.

---

### Post by tea for one on 2022-03-17
> SecureBoot enabled but mokutil says: SecureBoot enabled
Disable Secure Boot in your UEFI Set Up.
Boot into Ubuntu and run via a terminal
```
sudo update-grub
```

> BootCurrent: 0003
BootOrder: 0003,0002,0000,0001,2001,2002,2003
Boot0000* Windows Boot Manager    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...1................
Boot0001* Ubuntu    PciRoot(0x0)/Pci(0x12,0x0)/Sata(0,0,0)/HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(EFIubuntushimx64.efi)A01 ..
Boot0002* ubuntu    HD(1,GPT,93160ae9-fe7f-4e90-84bc-3416eb250e06,0x800,0x32000)/File(EFIubuntushimx64.efi)
Boot0003* Linpus lite    HD(1,MBR,0x38b1c112,0x6a4,0x1f40)/File(EFIBootgrubx64.efi)RC

Did you use Linpus Lite in the live session?
If you are trying to repair Grub in Ubuntu 20.04, it is advisable to use Ubuntu 20.04 in a live session.

---

### Post by boubflo on 2022-03-17
Thanks for your answer !

> What windows software did you use on the live USB to do this and what was the result?

I just used the **Startup Repair **from a Windows 10 live usb.

> 
You should have a chainloader entry for windows in //boot/grub/grub.cfg  and it should be pointing to the windows file bootmgfw.efi.  Does that  line exist?
[/COLOR]

I do have the line on /boot/grub/grub.cfg :
```
chainloader /EFI/Microsoft/Boot/bootmgfw.efi 
```

> One other possibility is that windows is hibernated and the Grub bootloader will not boot a hibernated partition.

I read about that possibility and desactivated hibernation from Windows properties. It doesn't seem to be the issue.

---

### Post by boubflo on 2022-03-17
> Disable Secure Boot in your UEFI Set Up.

That seems to work ! But I also had to disable Fastboot in the BIOS.
I didn't have this problem before with the same hardware, so I'm lost as to why I had to disable those two features.

> Did you use Linpus Lite in the live session?
It was a live usb key with Ubuntu 20.04 Desktop (and it certainly looked like it), but the BIOS seems to have seen it as Linpus : another mystery ! 

Anyway, thanks for your help !
Do you think there's any way I can enable SecureBoot again, or that's not supported ? (It really seemed to me that it was possible before...).

---

### Post by tea for one on 2022-03-17
> **boubflo said:**
> That seems to work ! But I also had to disable Fastboot in the BIOS.
I didn't have this problem before with the same hardware, so I'm lost as to why I had to disable those two features.
Windows updates have a special ability to alter UEFI settings without user intervention.
> **boubflo said:**
> Do you think there's any way I can enable SecureBoot again, or that's not supported ? (It really seemed to me that it was possible before...).
Of course, you can enable Secure Boot, but why would you want to?

Secure boot is undoubtedly essential for shared computers in commercial enterprises - the boss would not want disgruntled employees damaging the IT with malicious software.
As a home user with full control of my PC, secure boot does not provide me with any extra security.

If the problem is now solved, it is a nice gesture to mark the thread as solved to help other searchers/forum members.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by boubflo on 2022-03-17
> [COLOR=#000000]Of course, you can enable Secure Boot, but why would you want to?[/COLOR]

[COLOR=#000000]Secure boot is undoubtedly essential for shared computers in commercial enterprises - the boss would not want disgruntled employees damaging the IT with malicious software.[/COLOR]
[COLOR=#000000]As a home user with full control of my PC, secure boot does not provide me with any extra security.[/COLOR]

Well, this laptop is used in my entreprise, that's why I was asking. I still have to find out how to enable Secure Boot and be able to boot to Windows from grub then...

---

### Post by tea for one on 2022-03-17
I think that Grub sometimes does not find Windows with Secure Boot enabled.
As you have reported that Grub has located Windows and added it to the menu, why not enable Secure Boot in the UEFI and see if it is still OK?

---

### Post by boubflo on 2022-03-18
> why not enable Secure Boot in the UEFI and see if it is still OK?

I tried it, Windows won't boot from Grub as soon as I enable Secure Boot and/or Fast Boot.

---

### Post by tea for one on 2022-03-18
I cannot reproduce your situation exactly because my PC will boot Ubuntu and Windows 11 with Secure Boot On and Off.

Just to recap:-

Secure boot off - Grub appears and both Windows and Ubuntu boot OK.
Secure boot on - Grub appears and Ubuntu boots - Windows does **not** boot.

What happens when Windows does not boot?

I have read various comment in these forums about Acer Trust Settings within UEFI, I wonder if that is part of the solution?

---

### Post by ajgreeny on 2022-03-18
> **boubflo said:**
> I tried it, Windows won't boot from Grub as soon as I enable Secure Boot and/or Fast Boot.

I no longer use Windows of any version but I think you may be confusing **Fast Boot**, which is set in many BIOS systems, with another setting, **faststart**, which is disabled as far as I'm aware from Windows itself; nothing to do with the BIOS/UEFI.

Faststart is the method that Windows uses to put the OS into a hibernation state and which stops it booting from grub.

I've no idea how you get to that setting in Windows but I'm sure you will be able to find out how it's done, so see if disabling that helps.

---

### Post by grahammechanical on 2022-03-18
To confirm what ajgreeny said:

> The Fast Startup feature in Windows 10 allows your computer start up  faster after a shutdown. When you shut down your computer, Fast Startup  will put your computer into a hibernation state instead of a full  shutdown. Fast Startup is enabled by default if your computer is capable  of hibernation.

[https://docs.microsoft.com/en-us/troubleshoot/windows-client/deployment/updates-not-install-with-fast-startup](https://docs.microsoft.com/en-us/troubleshoot/windows-client/deployment/updates-not-install-with-fast-startup)

My BIOS motherboard has a Quick boot feature and the manual says this

> Enabling this item allows the BIOS to skip some power on self tests [POST] while booting to decrease the time needed to boot the system 

And then there is a definition by Intel of fast boot in Intel Visual BIOS

> Fast Boot is a feature in BIOS that reduces your computer boot time. If Fast Boot is enabled:
[LIST]
[*]Boot from Network, Optical, and Removable Devices are disabled.
[*]Video and USB devices (keyboard, mouse, drives) won't be available until the operating system loads.
[/LIST]

[https://www.intel.com/content/www/us/en/support/articles/000006699/intel-nuc.html](https://www.intel.com/content/www/us/en/support/articles/000006699/intel-nuc.html)

Regards

---

### Post by boubflo on 2022-03-22
> Secure boot off - Grub appears and both Windows and Ubuntu boot OK.
Secure boot on - Grub appears and Ubuntu boots - Windows does **not** boot.

That's it exactly. When Windows does not boot, I only got the usual acer logo but no turning wheel and it can stays stuck that way for hours and hours if I don't poweroff.

---

### Post by boubflo on 2022-03-22
Well, I think I am gonna with the Secure Boot disabled for this one computer.

Thank you all for your help !

---

