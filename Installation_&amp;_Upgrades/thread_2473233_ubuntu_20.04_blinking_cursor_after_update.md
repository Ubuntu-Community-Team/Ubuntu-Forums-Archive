---
title: "ubuntu 20.04 blinking cursor after update"
date: 2022-03-29
forum: Installation &amp; Upgrades
---

### Post by tuci on 2022-03-29
I'm considering using the Boot-Repair Recommended repair to fix this issue. 
Would appreciate other opinions.

Here's my Boot-Repair analysis:

```
 boot-repair-4ppa200                                              [20220329_0949]

============================== Boot Info Summary ===============================


 => No boot loader is installed in the MBR of /dev/nvme0n1.


nvme0n1p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/dell/SOS/bootmgfw.efi 
                       /efi/dell/SOS/bootmgr.efi /efi/dell/SOS/bootx64.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


nvme0n1p2: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme0n1p3: _____________________________________________________________________


    File system:       BitLocker
    Boot sector type:  Unknown
    Boot sector info: 


nvme0n1p4: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


nvme0n1p5: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


nvme0n1p6: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


nvme0n1p7: _____________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub




================================ 1 OS detected =================================


OS#1:   The OS now in use - Ubuntu 20.04.4 LTS CurrentSession on nvme0n1p7


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: TU117M [GeForce GTX 1650 Mobile / Max-Q] UHD Graphics 630 (Mobile) from NVIDIA Corporation Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.13.0-30-generic root=UUID=85e80131-8d51-43e7-8121-112c88ae0b0e ro quiet splash vt.handoff=7
df -Th / : /dev/nvme0n1p7 ext4  246G   68G  165G  30% /


===================================== UEFI =====================================


BIOS/UEFI firmware: 1.0.0(1.0) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to [email]boot.repair@gmail.com[/email].
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000
Boot0000* ubuntu	HD(1,GPT,c6352c47-89a3-47fa-b2b3-c6cfd385f3af,0x800,0x154000)/File(\EFI\UBUNTU\SHIMX64.EFI)




============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


nvme0n1	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


nvme0n1p7	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios
nvme0n1p1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme0n1p3	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
nvme0n1p4	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
nvme0n1p5	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
nvme0n1p6	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios


Partitions info (2/3): _________________________________________________________


nvme0n1p7	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p3	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p4	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
nvme0n1p5	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
nvme0n1p6	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


nvme0n1p7	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	nvme0n1
nvme0n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p3	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p4	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p5	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p6	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1


fdisk -l (filtered): ___________________________________________________________


Disk nvme0n1: 953.89 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 1D4081C2-0B48-43D9-B745-D09BE7E00B69
               Start        End    Sectors   Size Type
nvme0n1p1       2048    1394687    1392640   680M EFI System
nvme0n1p2    1394688    1656831     262144   128M Microsoft reserved
nvme0n1p3    1656832 1442502655 1440845824 687.1G Microsoft basic data
nvme0n1p4 1966790656 1968818175    2027520   990M Windows recovery environment
nvme0n1p5 1968818176 1998045183   29227008    14G Windows recovery environment
nvme0n1p6 1998047232 2000408575    2361344   1.1G Windows recovery environment
nvme0n1p7 1442502656 1966790655  524288000   250G Linux filesystem
Partition table entries are not in disk order.


parted -lm (filtered): _________________________________________________________


nvme0n1:1024GB:nvme:512:512:gpt:KXG60ZNV1T02 NVMe TOSHIBA 1024GB:;
1:1049kB:714MB:713MB:fat32:EFI system partition:boot, esp;
2:714MB:848MB:134MB::Microsoft reserved partition:msftres;
3:848MB:739GB:738GB::Basic data partition:msftdata;
7:739GB:1007GB:268GB:ext4::;
4:1007GB:1008GB:1038MB:ntfs::hidden, diag;
5:1008GB:1023GB:15.0GB:ntfs::hidden, diag;
6:1023GB:1024GB:1209MB:ntfs::hidden, diag;


blkid (filtered): ______________________________________________________________


NAME        FSTYPE    UUID                                 PARTUUID                             LABEL       PARTLABEL
nvme0n1                                                                                                     
&#9500;&#9472;nvme0n1p1 vfat      B2CA-65B0                            c6352c47-89a3-47fa-b2b3-c6cfd385f3af ESP         EFI system partition
&#9500;&#9472;nvme0n1p2                                                9d38204b-8e43-44a9-b60f-4f0c37d0972f             Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 BitLocker                                      9e44cc7e-50cc-447e-b3c8-dbb890be544b             Basic data partition
&#9500;&#9472;nvme0n1p4 ntfs      F4322F0E322ED600                     a9a7a509-f649-4a7c-a849-681649931832 WINRETOOLS  
&#9500;&#9472;nvme0n1p5 ntfs      50C42F2EC42F162E                     08e5cf82-303f-4807-864f-9d84258b9d40 Image       
&#9500;&#9472;nvme0n1p6 ntfs      6CD6231AD622E454                     2e11324c-6330-4078-af7b-25340949c288 DELLSUPPORT 
&#9492;&#9472;nvme0n1p7 ext4      85e80131-8d51-43e7-8121-112c88ae0b0e 2fc328cf-c9ee-467e-b34d-8ea75e9a9884             


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/nvme0n1p4         408.7M  59% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5         195.8M  99% /mnt/boot-sav/nvme0n1p5
/dev/nvme0n1p6           496M  57% /mnt/boot-sav/nvme0n1p6
/dev/nvme0n1p7         164.8G  28% /


Mount options (filtered): ______________________________________________________


/dev/nvme0n1p4         fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p5         fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p6         fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p7         ext4            rw,relatime,errors=remount-ro


=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================


search.fs_uuid 85e80131-8d51-43e7-8121-112c88ae0b0e root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


=================== nvme0n1p7/boot/grub/grub.cfg (filtered) ====================


Ubuntu   85e80131-8d51-43e7-8121-112c88ae0b0e
Ubuntu, with Linux 5.13.0-35-generic   85e80131-8d51-43e7-8121-112c88ae0b0e
Ubuntu, with Linux 5.13.0-30-generic   85e80131-8d51-43e7-8121-112c88ae0b0e
Windows Boot Manager (on nvme0n1p1)   osprober-efi-B2CA-65B0
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


======================== nvme0n1p7/etc/fstab (filtered) ========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p7 during installation
UUID=85e80131-8d51-43e7-8121-112c88ae0b0e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=B2CA-65B0  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


==================== nvme0n1p7/etc/default/grub (filtered) =====================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


================= nvme0n1p7: Location of files loaded by Grub ==================


           GiB - GB             File                                 Fragment(s)
 767.217773438 = 823.793811456  boot/grub/grub.cfg                             3
 747.434276581 = 802.551443456  boot/vmlinuz                                   1
 692.760738373 = 743.846178816  boot/vmlinuz-5.13.0-30-generic                 2
 747.434276581 = 802.551443456  boot/vmlinuz-5.13.0-35-generic                 1
 692.760738373 = 743.846178816  boot/vmlinuz.old                               2
 702.315631866 = 754.105667584  boot/initrd.img                                2
 750.233596802 = 805.557190656  boot/initrd.img-5.13.0-30-generic              2
 702.315631866 = 754.105667584  boot/initrd.img-5.13.0-35-generic              2
 750.233596802 = 805.557190656  boot/initrd.img.old                            2


=================== nvme0n1p7: ls -l /etc/grub.d/ (filtered) ===================


-rwxr-xr-x 1 root root 18151 Aug 12  2021 10_linux
-rwxr-xr-x 1 root root 42359 Aug 12  2021 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Aug 12  2021 20_linux_xen
-rwxr-xr-x 1 root root 12059 Aug 12  2021 30_os-prober
-rwxr-xr-x 1 root root  1424 Aug 12  2021 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21 05:06 35_fwupd
-rwxr-xr-x 1 root root   214 Aug 12  2021 40_custom
-rwxr-xr-x 1 root root   216 Aug 12  2021 41_custom


======================== nvme0n1p7/etc/grub.d/35_fwupd =========================


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


The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p7,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file


Blockers in case of suggested repair: __________________________________________


 Please use this software in a live-session (live-CD or live-USB). This will enable this feature.


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 20.04.4 LTS CurrentSession entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !
```

---

### Post by tea for one on 2022-03-29
[COLOR="#0000FF"]OS#1: The OS now in use - Ubuntu 20.04.4 LTS CurrentSession on nvme0n1p7[/COLOR]

According to the above line from the boot-repair report, you are already using your Ubuntu installation.

Therefore, what is the exact issue?
Is it something to do with nvme0n1p3?
File system: BitLocker

---

### Post by ActionParsnip on 2022-03-30
If you boot an older kernel, is it OK?

---

