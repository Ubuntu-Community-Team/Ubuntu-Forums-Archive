---
title: "Installing Edubuntu on old hardware"
date: 2024-04-02
forum: Installation &amp; Upgrades
---

### Post by jamiewannenburg1 on 2024-04-02
I'm trying to unstall Edubuntu 23.10 for my kid on grandma's old computer. It has a Pentium dual core processor.
I'm able to run the install (overwrite harddrive with default partitions), but the BIOS is unable to boot.
Here is the pastebin from boot-repair:
[https://*******.us/2HpndC](https://*******.us/2HpndC)

Can anyone help me? Is it because this is not a 32bit os?

---

### Post by TheFu on 2024-04-02
The pastebin isn't working for me. It doesn't seem to link anywhere. With out showing the actual contents under the '*******' characters, nobody will be able to help you.

---

### Post by jamiewannenburg1 on 2024-04-02
Sorry, the *** should be *******.
[https://*******.us/2HpndC](https://*******.us/2HpndC)
It seems ubuntuforums does not like the default pastebin from the boot-repair disk. Perhaps s p r u n g e?

---

### Post by deadflowr on 2024-04-02
This seems small enough to just copy/paste directly into the thread.
For the record, yeah, many years ago, the former forum staff deemed the word being asterisks as a derogatory term so it's on the banned word list.


```
boot-repair-4ppa2075                                              [20240402_0859]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt3)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 23.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /efi/boot/grubx64.efi 
                       /efi/boot/mmx64.efi /ldlinux.sys


================================ 1 OS detected =================================

OS#1:   Ubuntu 23.10 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: 82945G/GZ Integrated Graphics Controller from Intel Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: NL94510J.86A.0010.2007.0523.1650(0.0) from Intel Corp.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


925029921cfc9e40f54f55d4cffbdd49   sda2/BOOT/fbx64.efi
857e495f63f23c842e2b074e692b6e3a   sda2/BOOT/mmx64.efi
1d99ff510dac8535d215797ad5e69230   sda2/ubuntu/grubx64.efi
857e495f63f23c842e2b074e692b6e3a   sda2/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda2/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   sda2/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda	: is-GPT,	hasBIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda3	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB

Partitions info (2/3): _________________________________________________________

sda2	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda3	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

sda2	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda3	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 232.88 GiB, 250058268160 bytes, 488395055 sectors
Disk identifier: FA8CEF0D-0A8C-4CD6-A077-E2A60EA1AE9A
       Start       End   Sectors   Size Type
sda1     2048      4095      2048     1M BIOS boot
sda2     4096   1054719   1050624   513M EFI System
sda3  1054720 488394751 487340032 232.4G Linux filesystem
Disk sdb: 3.75 GiB, 4026531840 bytes, 7864320 sectors
Disk identifier: 0x27f27321
     Boot Start     End Sectors  Size Id Type
sdb1  *     2048 7864319 7862272  3.7G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:250GB:scsi:512:512:gpt:ATA ST3250312AS:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:540MB:538MB:fat32:EFI System Partition:boot, esp;
3:540MB:250GB:250GB:ext4::;
sdb:4027MB:scsi:512:512:msdos:USB USB Fash Disk:;
1:1049kB:4027MB:4025MB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1                                               d0a5c987-7690-4cc0-997d-baba7b8cbccd             
&#9500;&#9472;sda2 vfat     3826-0C52                            034994c1-73eb-4e53-b2a5-559b14d9e693             EFI System Partition
&#9492;&#9472;sda3 ext4     4cf57f9e-a978-4a90-9494-d86ad434e0e4 43d3c171-6c51-4445-b3b6-5fa5ec63c1be             
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     FE16-A730                            27f27321-01                          BOOT-REPAIR 

Mount points (filtered): _______________________________________________________

            Avail Use% Mounted on
/dev/sda2   505.9M   1% /mnt/boot-sav/sda2
/dev/sda3   196.9G   8% /mnt/boot-sav/sda3
/dev/sdb1     1.3G  65% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda2   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3   ext4            rw,relatime
/dev/sdb1   vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 4cf57f9e-a978-4a90-9494-d86ad434e0e4 root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda3/boot/grub/grub.cfg (filtered) ======================

Ubuntu   4cf57f9e-a978-4a90-9494-d86ad434e0e4
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda3/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=4cf57f9e-a978-4a90-9494-d86ad434e0e4 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=3826-0C52  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda3/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda3: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 114.952236176 = 123.429023744  boot/grub/grub.cfg                             1
 114.965625763 = 123.443400704  boot/grub/i386-pc/core.img                     1
  14.961532593 = 16.064823296   boot/vmlinuz                                   1
  14.961532593 = 16.064823296   boot/vmlinuz-6.5.0-26-generic                  1
  13.445907593 = 14.437433344   boot/vmlinuz-6.5.0-9-generic                   1
  13.445907593 = 14.437433344   boot/vmlinuz.old                               1
  15.696510315 = 16.853999616   boot/initrd.img                                1
  15.696510315 = 16.853999616   boot/initrd.img-6.5.0-26-generic               1
  15.641788483 = 16.795242496   boot/initrd.img-6.5.0-9-generic                1
  15.641788483 = 16.795242496   boot/initrd.img.old                            1

===================== sda3: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18228 Oct  2  2023 10_linux
-rwxr-xr-x 1 root root 43202 Oct  2  2023 10_linux_zfs
-rwxr-xr-x 1 root root 14459 Oct  2  2023 20_linux_xen
-rwxr-xr-x 1 root root   786 Oct  2  2023 25_bli
-rwxr-xr-x 1 root root 13120 Oct  2  2023 30_os-prober
-rwxr-xr-x 1 root root  1174 Oct  2  2023 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Sep  6  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Oct  2  2023 40_custom
-rwxr-xr-x 1 root root   215 Oct  2  2023 41_custom

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Start Boot-Repair-Disk 64-bit
Start Boot-Repair-Disk 64-bit (compatibility mode)
UEFI Firmware Settings
Test memory

========================= sdb1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda3,
using the following options:  sda2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

 The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit (www.sourceforge.net/p/boot-repair-cd), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 23.10 entry (sda2/efi/****/grub****.efi (**** will be updated in the final message) file) !
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.


```

---

### Post by deadflowr on 2024-04-02
Also...

For the record, 
Edubuntu has the same requirements to run as normal Ubuntu since it uses the same desktop.
fwiw

---

### Post by oldfred on 2024-04-02
Your system is new enough to be UEFI or within last 10 years.
But you installed in both BIOS boot mode, or grub in gpt's protective MBR and in UEFI  or grub in ESP - efi system partition.
One one will work and since fstab is showing mount of ESP, I expect that UEFI mode is what will work.

Many earlier UEFI systems had to have UEFI boot mode set in UEFI settings. Some newer ones may auto switch to which ever boot is selected from UEFI one time boot menu. Check UEFI settings and make sure default is UEFI.

You can rerun Boot-Repair report in UEFI mode & it will show more info on UEFI install. And post the normal pastebin link.

---

### Post by jamiewannenburg1 on 2024-04-08
Thank you very much for the help.
I ended up installing debian, and its installation disk worked.

---

