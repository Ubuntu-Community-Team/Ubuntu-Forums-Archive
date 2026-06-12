---
title: "Did Ubuntu 22.04 install brick my laptop?"
date: 2023-01-03
forum: Installation &amp; Upgrades
---

### Post by r2020r on 2023-01-03
Hi


Machine: HP Zbook 15 
BIOS:      UEFI (Hybird...)
Dual Boot: NO


I installed Ubuntu 22.04 and it worked. I did a clean install that involved formatting the disk, and there is no dual boot. After the installation, machine **rebooted repeatedly in a loop. **Message on the screen was "**RESET SYSTEM**".


I went in to BIOS and changed  to *UEFI (Native...).*


**After that**

[LIST=1]
[*]I am not able to enter the "*F10 BIOS Setup*". When I press *F10*, I get HP logo and nothing else (see the attached pic).
[*]I pressed "*F9 Boot option*" and it shows a long list of items (*Ubuntu....*), as if some program made entries in an infinite loop (see the attached pic).
[*]I tried booting from *Ubuntu Live CD* and it hangs, does not even show the boot menu.
[*]I tried booting from *Clone Zilla CD (*to install the Win10 image that I took before installing Ubuntu) and it also hangs; nothing appears on screen.
[*]I **removed the mSATA **drive on which I had installed the Ubuntu 22.04, and machined stopped rebooting. But still I am not able to enter "*F10 BIOS Setup*",  not able to boot from *Ubuntu Live CD*
[*]Previously I had working Ubuntu 22.04 on this machine. I had removed that HDD and put a new mSATA. Now I put back the old HDD, hoping that the system will boot in to Ubuntu. But system did not boot. All other problem continued.  "*F10 BIOS Setup*" and *Ubuntu Live CD *do not work.
[/LIST]

Since I can not enter in to "*F10 BIOS Setup*", I can not even flush the BIOS. Seems like dead-end,
[LIST]
[*]**does it mean my machine is Bricked?**
[*]Is there a way I Can clear the entries from Boot Menu?
[*]Does it need hardware level intervention to make the machine useful again? Any idea what kind of intervention.
[/LIST]


My thought is that, the more I force myself to use Ubuntu, the more resistance it puts in the form of repeated boot, etc... I had 18.04 for many years and it ran just fine, on this same laptop. But 22.04 does not even take off(not even boot). I had problems installing 22.04 on P50 and Zbook. It is seems way sensitive to bios settings. 


Thanks

---

### Post by r2020r on 2023-01-03
HP has a key combination to reset the bios to factory defaults. That helped me access the "F10 Bios Setup". I will try to resolve rest of the issues.
[https://support.hp.com/in-en/document/ish_3932413-2337994-16#GUID-955D0E72-B4DD-46D6-A6DA-6E15DD06254E](https://support.hp.com/in-en/document/ish_3932413-2337994-16#GUID-955D0E72-B4DD-46D6-A6DA-6E15DD06254E)

Press "Power button + Windows Key + B" this restored the bios to previous working copy.

Thanks

---

### Post by MAFoElffen on 2023-01-03
That is just strange. This would be the first time in 13 years of supporting Ubuntu, that I even heard that an installation would or even could change the BIOS settings! And I am a certified warranty service tech for HP, Dell and Lenovo.

 "That" has made your problem very interesting to me. You have my curiosity. I have lots of questions.

One problem I read in your first post is that you installed, then... you changed it to UEFI... What BIOS mode was it set to when you installed? That model HP has 4 settings... SecureBoot (Enabled)... Then SecureBoot (disabled) with another setting of either Legacy, UEFI Hybrid (with CSM) or UEFI Native (Without CSM)...

---

### Post by oldfred on 2023-01-03
HP is not particularly Linux friendly. Most have had to update UEFI firmware. And after install change boot order in UEFI settings.
If single booting, many have had to change an Ubuntu UEFI entry to read "Windows Boot Manager" as Windows wants that as at least one of its boots.

We have seen several others with multiple duplicate UEFI boot entries. But I always assumed they just did multiple installs or efibootmgr entries.

Can you boot Ubuntu live installer?
If so add Boot-Repair and post link to its summary report. 

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by r2020r on 2023-01-03
Thanks for responding
> [COLOR=#000000]One problem I read in your first post is that you installed, then... you changed it to UEFI... What BIOS mode was it set to when you installed? That model HP has 4 settings... SecureBoot (Enabled)... Then SecureBoot (disabled) with another setting of either Legacy, UEFI Hybrid (with CSM) or UEFI Native (Without CSM)...[/COLOR]
[LIST=1]
[*]When I installed the system was in **[COLOR=#000000]UEFI Hybrid (with CSM)[/COLOR]**
[*]SecureBoot has been **GRAYED **out. Not able to change it. It's status does not change with boot mode. Stays GRAYED out
[/LIST]

I ran boot-repair tool and it said 
```
[FONT=Arial]An error occurred during the repair.[/FONT]
[FONT=Arial]Error: NVram is locked (Ubuntu not found in efibootmgr). [/FONT]
```

---

### Post by r2020r on 2023-01-03
Thanks oldfred

> **oldfred said:**
> 
Can you boot Ubuntu live installer?
If so add Boot-Repair and post link to its summary report. 


I ran boot-repair and here is the summary [https://paste.ubuntu.com/p/pspcTpJsxT/](https://paste.ubuntu.com/p/pspcTpJsxT/)

```
boot-repair-4ppa203                                              [20230104_0349]

============================= Boot Repair Summary ==============================












Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups




rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
Mount sda1 on /mnt/boot-sav/sda2/boot/efi


Unhide GRUB boot menu in sda2/etc/default/grub


======================== Reinstall the grub-efi of sda2 ========================


chroot /mnt/boot-sav/sda2 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.1
chroot /mnt/boot-sav/sda2 modprobe efivars


chroot /mnt/boot-sav/sda2 efibootmgr -v before grub install
No BootOrder is set; firmware will attempt recovery


chroot /mnt/boot-sav/sda2 uname -r
5.15.0-25-generic


chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi


chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.


chroot /mnt/boot-sav/sda2 efibootmgr -v after grub install
No BootOrder is set; firmware will attempt recovery
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com


chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-56-generic
Found initrd image: /boot/initrd.img-5.15.0-56-generic
Found linux image: /boot/vmlinuz-5.15.0-25-generic
Found initrd image: /boot/initrd.img-5.15.0-25-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi


Unhide GRUB boot menu in sda2/boot/grub/grub.cfg


An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com


Locked-NVram detected.




============================ Boot Info After Repair ============================


 => Grub2 (v2.00) is installed in the MBR of /dev/mmcblk0 and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sda.


mmcblk0p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       204800 sectors.. But according to the info from the 
                       partition table, it has 1048575 sectors.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/HP/BiosUpdate/CryptRSA32.efi 
                       /efi/HP/BiosUpdate/CryptRSA.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate32.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub




================================ 1 OS detected =================================


OS#1:   Ubuntu 22.04 LTS on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: GK106GLM [Quadro K2100M] EFI VGA from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: L70 Ver. 01.47(1.47) from Hewlett-Packard
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - This system doesn't support Secure Boot.
No BootOrder is set; firmware will attempt recovery


728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   sda1/Boot/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/Boot/mmx64.efi
3795ef72a4ed0369ca44e711527904bf   sda1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
1b8c0684ede8539ccc205cf7a750eca3   sda1/HP/BiosUpdate/CryptRSA32.efi
6488d391f74263c9da3c3d47dffa6212   sda1/HP/BiosUpdate/CryptRSA.efi
28ccbac4a5471948714b53343c1a4db8   sda1/HP/BiosUpdate/HpBiosUpdate32.efi
668e03796f854694457d4960dac00b9d   sda1/HP/BiosUpdate/HpBiosUpdate.efi
d1f6c29ed98f2a8102fd87c118371e0b   sda1/Microsoft/Boot/bootmgfw.efi
85b10a5efd8419adc616cb2a5a70db30   sda1/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: EE21D0DF-7A2E-4777-B161-770D4539ED28
        Start        End   Sectors   Size Type
sda1     2048    1050623   1048576   512M EFI System
sda2  1050624 1000214527 999163904 476.4G Linux filesystem
Disk mmcblk0: 3.64 GiB, 3904897024 bytes, 7626752 sectors
Disk identifier: 0x00778327
          Boot Start     End Sectors  Size Id Type
mmcblk0p1 *     2048 7626751 7624704  3.6G  e W95 FAT16 (LBA)


parted -lm (filtered): _________________________________________________________


sda:512GB:scsi:512:512:gpt:ATA SK hynix SC300 m:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:512GB:512GB:ext4::;
mmcblk0:3905MB:sd/mmc:512:512:msdos:SD SA04G:;
1:1049kB:3905MB:3904MB:fat16::boot, lba;


blkid (filtered): ______________________________________________________________


NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9500;&#9472;sda1      vfat     8E8D-693A                            f03ca49b-2c43-41be-84db-2465f243ad62             EFI System Partition
&#9492;&#9472;sda2      ext4     521154bc-b98b-4e4d-895f-85fcaf352456 eafb2be1-754e-432a-afc3-13523e36b3ec             
mmcblk0                                                                                                    
&#9492;&#9472;mmcblk0p1 vfat     8474-3495                            00778327-01                          UBUNTU 22_0 


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/mmcblk0p1         194.2M  95% /cdrom
/dev/sda1               46.6M  51% /mnt/boot-sav/sda1
/dev/sda2              433.8G   2% /mnt/boot-sav/sda2


Mount options (filtered): ______________________________________________________




=================== mmcblk0p1/boot/grub/grub.cfg (filtered) ====================


Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


================= mmcblk0p1: Location of files loaded by Grub ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 521154bc-b98b-4e4d-895f-85fcaf352456 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda2/boot/grub/grub.cfg (filtered) ======================


Ubuntu   521154bc-b98b-4e4d-895f-85fcaf352456
Ubuntu, with Linux 5.15.0-56-generic   521154bc-b98b-4e4d-895f-85fcaf352456
Ubuntu, with Linux 5.15.0-25-generic   521154bc-b98b-4e4d-895f-85fcaf352456
Windows Boot Manager (on sda1)   osprober-efi-8E8D-693A
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sda2/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=521154bc-b98b-4e4d-895f-85fcaf352456 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8E8D-693A  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


======================= sda2/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda2: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 340.457046509 = 365.562970112  boot/vmlinuz                                   1
   6.011287689 = 6.454571008    boot/vmlinuz-5.15.0-25-generic                 1
 340.457046509 = 365.562970112  boot/vmlinuz-5.15.0-56-generic                 1
   6.011287689 = 6.454571008    boot/vmlinuz.old                               1
 341.692428589 = 366.889451520  boot/initrd.img                                1
 341.441505432 = 366.620024832  boot/initrd.img-5.15.0-25-generic              1
 341.692428589 = 366.889451520  boot/initrd.img-5.15.0-56-generic              1
 341.441505432 = 366.620024832  boot/initrd.img.old                            1


===================== sda2: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15  2022 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom
```

---

### Post by r2020r on 2023-01-03
I installed again by UEFI (Native...). Installation completed successfully. But system still reboots in a loop.
[COLOR=#000000]After the installation I see that [/COLOR]**Secure Boot is NOT grayed out. When I installed, Secure Boot was not enabled.**

---

### Post by r2020r on 2023-01-03
I installed again in* UEFI (Native...).* It was clean/erase install. Installation completed successfully. But system still reboots in a loop.
After the installation I see that  **Secure Boot **is NOT grayed out. When I installed, Secure Boot was not enabled.
I ran the boot-repair again. Here is the output [https://paste.ubuntu.com/p/dh4smzKWCW/](https://paste.ubuntu.com/p/dh4smzKWCW/)

```
 boot-repair-4ppa203                                              [20230104_0425]

============================= Boot Repair Summary ==============================












Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups




rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
Mount sda1 on /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e/boot/efi


Unhide GRUB boot menu in sda2/etc/default/grub


======================== Reinstall the grub-efi of sda2 ========================


chroot /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.1
chroot /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e modprobe efivars


chroot /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e efibootmgr -v before grub install
No BootOrder is set; firmware will attempt recovery


chroot /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e uname -r
5.15.0-25-generic


chroot /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda1
mv /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e/boot/efi/EFI/Boot/bootx64.efi /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e/boot/efi/EFI/Boot/bkpbootx64.efi
cp /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e/boot/efi/efi/ubuntu/grubx64.efi /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e/boot/efi/EFI/Boot/bootx64.efi


chroot /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.


chroot /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e efibootmgr -v after grub install
No BootOrder is set; firmware will attempt recovery
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com


chroot /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-56-generic
Found initrd image: /boot/initrd.img-5.15.0-56-generic
Found linux image: /boot/vmlinuz-5.15.0-25-generic
Found initrd image: /boot/initrd.img-5.15.0-25-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi


Unhide GRUB boot menu in sda2/boot/grub/grub.cfg


An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com


Locked-NVram detected.




============================ Boot Info After Repair ============================


 => Grub2 (v2.00) is installed in the MBR of /dev/mmcblk0 and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sda.


mmcblk0p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       204800 sectors.. But according to the info from the 
                       partition table, it has 1048575 sectors.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/HP/BiosUpdate/CryptRSA32.efi 
                       /efi/HP/BiosUpdate/CryptRSA.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate32.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub




================================ 1 OS detected =================================


OS#1:   Ubuntu 22.04 LTS on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: GK106GLM [Quadro K2100M] EFI VGA from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: L70 Ver. 01.47(1.47) from Hewlett-Packard
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - This system doesn't support Secure Boot.
No BootOrder is set; firmware will attempt recovery


728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   sda1/Boot/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/Boot/mmx64.efi
3795ef72a4ed0369ca44e711527904bf   sda1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
1b8c0684ede8539ccc205cf7a750eca3   sda1/HP/BiosUpdate/CryptRSA32.efi
6488d391f74263c9da3c3d47dffa6212   sda1/HP/BiosUpdate/CryptRSA.efi
28ccbac4a5471948714b53343c1a4db8   sda1/HP/BiosUpdate/HpBiosUpdate32.efi
668e03796f854694457d4960dac00b9d   sda1/HP/BiosUpdate/HpBiosUpdate.efi
d1f6c29ed98f2a8102fd87c118371e0b   sda1/Microsoft/Boot/bootmgfw.efi
85b10a5efd8419adc616cb2a5a70db30   sda1/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda2	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios
sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far


Partitions info (2/3): _________________________________________________________


sda2	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


sda2	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: B74B540C-248E-4913-AD66-AEC83A304E0D
        Start        End   Sectors   Size Type
sda1     2048    1050623   1048576   512M EFI System
sda2  1050624 1000214527 999163904 476.4G Linux filesystem
Disk mmcblk0: 3.64 GiB, 3904897024 bytes, 7626752 sectors
Disk identifier: 0x00778327
          Boot Start     End Sectors  Size Id Type
mmcblk0p1 *     2048 7626751 7624704  3.6G  e W95 FAT16 (LBA)


parted -lm (filtered): _________________________________________________________


sda:512GB:scsi:512:512:gpt:ATA SK hynix SC300 m:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:512GB:512GB:ext4::;
mmcblk0:3905MB:sd/mmc:512:512:msdos:SD SA04G:;
1:1049kB:3905MB:3904MB:fat16::boot, lba;


blkid (filtered): ______________________________________________________________


NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9500;&#9472;sda1      vfat     8E8D-693A                            b11dcda9-d43a-4758-8a11-94c635b2fd4e             EFI System Partition
&#9492;&#9472;sda2      ext4     dd07ab56-89f8-43c9-9d98-e6d374c7a81e db8d57cf-1c31-41cc-9d75-46f7317b1f36             
mmcblk0                                                                                                    
&#9492;&#9472;mmcblk0p1 vfat     8474-3495                            00778327-01                          UBUNTU 22_0 


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/mmcblk0p1         194.2M  95% /cdrom
/dev/sda1               46.6M  51% /mnt/boot-sav/sda1
/dev/sda2              433.6G   2% /media/ubuntu/dd07ab56-89f8-43c9-9d98-e6d374c7a81e


Mount options (filtered): ______________________________________________________




=================== mmcblk0p1/boot/grub/grub.cfg (filtered) ====================


Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


================= mmcblk0p1: Location of files loaded by Grub ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid dd07ab56-89f8-43c9-9d98-e6d374c7a81e root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda2/boot/grub/grub.cfg (filtered) ======================


Ubuntu   dd07ab56-89f8-43c9-9d98-e6d374c7a81e
Ubuntu, with Linux 5.15.0-56-generic   dd07ab56-89f8-43c9-9d98-e6d374c7a81e
Ubuntu, with Linux 5.15.0-25-generic   dd07ab56-89f8-43c9-9d98-e6d374c7a81e
Windows Boot Manager (on sda1)   osprober-efi-8E8D-693A
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sda2/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=dd07ab56-89f8-43c9-9d98-e6d374c7a81e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8E8D-693A  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


======================= sda2/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda2: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
  10.089859009 = 10.833903616   boot/vmlinuz                                   1
   6.165035248 = 6.619656192    boot/vmlinuz-5.15.0-25-generic                 2
  10.089859009 = 10.833903616   boot/vmlinuz-5.15.0-56-generic                 1
   6.165035248 = 6.619656192    boot/vmlinuz.old                               2
  11.317432404 = 12.152000512   boot/initrd.img                                1
  11.074317932 = 11.890958336   boot/initrd.img-5.15.0-25-generic              1
  11.317432404 = 12.152000512   boot/initrd.img-5.15.0-56-generic              1
  11.074317932 = 11.890958336   boot/initrd.img.old                            1


===================== sda2: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15  2022 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom
```

---

### Post by r2020r on 2023-01-04
I reinstalled with *UEFI Native *and made sure that *Secure boot *is also enabled. Installation succeeded. But infinite reboot continued to happen. I ran boot-repair but after that also problem continued. Here is the output of boot-repair.

```
boot-repair-4ppa203                                              [20230104_0502]

============================= Boot Repair Summary ==============================








Default settings: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04 LTS entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !


User settings: _________________________________________________________________


The settings chosen by the user will purge and reinstall the grub-efi-amd64-signed of
sda2,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups




rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
Mount sda1 on /mnt/boot-sav/sda2/boot/efi
chroot /mnt/boot-sav/sda2 apt-get -y update
Purge the GRUB of sda2
grub-efi-amd64-signed available


The following package was automatically installed and is no longer required:
systemd-hwe-hwdb
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 369 not upgraded.
DEBCHECK debOK, grub-efi-amd64-signed
DEBCHECK debOK
Please type: sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda2" apt-get install -fynsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y grub-com*nsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y grub2-com*nsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y shim-signednsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y grub-common:*nsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y grub2-common:*n
shim-signed available
linux-headers-generic available
linux-signed-generic NOT available (apt-cache policy  problem)
Then type: sudo chroot "/mnt/boot-sav/sda2" apt-get install -y grub-efi-amd64-signed shim-signed linux-headers-generic


Unhide GRUB boot menu in sda2/etc/default/grub


Reinstall the grub-efi-amd64-signed shim-signed linux-headers-generic of sda2 =


chroot /mnt/boot-sav/sda2 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.1
chroot /mnt/boot-sav/sda2 modprobe efivars


chroot /mnt/boot-sav/sda2 efibootmgr -v before grub install
No BootOrder is set; firmware will attempt recovery


chroot /mnt/boot-sav/sda2 uname -r
5.15.0-25-generic


chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/


chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.


chroot /mnt/boot-sav/sda2 efibootmgr -v after grub install
No BootOrder is set; firmware will attempt recovery
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com


chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-56-generic
Found initrd image: /boot/initrd.img-5.15.0-56-generic
Found linux image: /boot/vmlinuz-5.15.0-25-generic
Found initrd image: /boot/initrd.img-5.15.0-25-generic
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi


Unhide GRUB boot menu in sda2/boot/grub/grub.cfg


An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com


Locked-NVram detected.




============================ Boot Info After Repair ============================


 => Grub2 (v2.00) is installed in the MBR of /dev/mmcblk0 and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sda.


mmcblk0p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       204800 sectors.. But according to the info from the 
                       partition table, it has 1048575 sectors.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/grubx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/HP/BiosUpdate/CryptRSA32.efi 
                       /efi/HP/BiosUpdate/CryptRSA.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate32.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub




================================ 1 OS detected =================================


OS#1:   Ubuntu 22.04 LTS on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: GK106GLM [Quadro K2100M] EFI VGA from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: L70 Ver. 01.47(1.47) from Hewlett-Packard
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - This system doesn't support Secure Boot.
No BootOrder is set; firmware will attempt recovery


728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   sda1/Boot/fbx64.efi
3795ef72a4ed0369ca44e711527904bf   sda1/Boot/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/Boot/mmx64.efi
3795ef72a4ed0369ca44e711527904bf   sda1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
1b8c0684ede8539ccc205cf7a750eca3   sda1/HP/BiosUpdate/CryptRSA32.efi
6488d391f74263c9da3c3d47dffa6212   sda1/HP/BiosUpdate/CryptRSA.efi
28ccbac4a5471948714b53343c1a4db8   sda1/HP/BiosUpdate/HpBiosUpdate32.efi
668e03796f854694457d4960dac00b9d   sda1/HP/BiosUpdate/HpBiosUpdate.efi
d1f6c29ed98f2a8102fd87c118371e0b   sda1/Microsoft/Boot/bootmgfw.efi
85b10a5efd8419adc616cb2a5a70db30   sda1/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: 862E39F6-77A8-4498-863D-B477518AAE68
        Start        End   Sectors   Size Type
sda1     2048    1050623   1048576   512M EFI System
sda2  1050624 1000214527 999163904 476.4G Linux filesystem
Disk mmcblk0: 3.64 GiB, 3904897024 bytes, 7626752 sectors
Disk identifier: 0x00778327
          Boot Start     End Sectors  Size Id Type
mmcblk0p1 *     2048 7626751 7624704  3.6G  e W95 FAT16 (LBA)


parted -lm (filtered): _________________________________________________________


sda:512GB:scsi:512:512:gpt:ATA SK hynix SC300 m:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:512GB:512GB:ext4::;
mmcblk0:3905MB:sd/mmc:512:512:msdos:SD SA04G:;
1:1049kB:3905MB:3904MB:fat16::boot, lba;


blkid (filtered): ______________________________________________________________


NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9500;&#9472;sda1      vfat     8E8D-693A                            c2a3d3bc-7aab-45eb-b82b-135dde1a3eca             EFI System Partition
&#9492;&#9472;sda2      ext4     691a22b4-1dd5-43e1-b443-3ce7eb8174e9 09d94ed6-cbe3-426e-88a5-08caec1c7cb5             
mmcblk0                                                                                                    
&#9492;&#9472;mmcblk0p1 vfat     8474-3495                            00778327-01                          UBUNTU 22_0 


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/mmcblk0p1         194.2M  95% /cdrom
/dev/sda1                 45M  53% /mnt/boot-sav/sda1
/dev/sda2              434.6G   2% /mnt/boot-sav/sda2


Mount options (filtered): ______________________________________________________




=================== mmcblk0p1/boot/grub/grub.cfg (filtered) ====================


Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


================= mmcblk0p1: Location of files loaded by Grub ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 691a22b4-1dd5-43e1-b443-3ce7eb8174e9 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda2/boot/grub/grub.cfg (filtered) ======================


Ubuntu   691a22b4-1dd5-43e1-b443-3ce7eb8174e9
Ubuntu, with Linux 5.15.0-56-generic   691a22b4-1dd5-43e1-b443-3ce7eb8174e9
Ubuntu, with Linux 5.15.0-25-generic   691a22b4-1dd5-43e1-b443-3ce7eb8174e9
Windows Boot Manager (on sda1)   osprober-efi-8E8D-693A
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sda2/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=691a22b4-1dd5-43e1-b443-3ce7eb8174e9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8E8D-693A  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


======================= sda2/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda2: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 310.730484009 = 333.644316672  boot/vmlinuz                                   1
   6.211910248 = 6.669987840    boot/vmlinuz-5.15.0-25-generic                 2
 310.730484009 = 333.644316672  boot/vmlinuz-5.15.0-56-generic                 1
   6.211910248 = 6.669987840    boot/vmlinuz.old                               2
 311.051807404 = 333.989335040  boot/initrd.img                                2
 310.121196747 = 332.990099456  boot/initrd.img-5.15.0-25-generic              1
 311.051807404 = 333.989335040  boot/initrd.img-5.15.0-56-generic              2
 310.121196747 = 332.990099456  boot/initrd.img.old                            1


===================== sda2: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18683 Dec  2 15:18 10_linux
-rwxr-xr-x 1 root root 43031 Dec  2 15:18 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Dec  2 15:18 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec  2 15:18 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec  2 15:18 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec  2 15:18 40_custom
-rwxr-xr-x 1 root root   215 Dec  2 15:18 41_custom
```

---

### Post by MAFoElffen on 2023-01-04
Wow. Triple posted. From my notes on that laptop, Try a setting of SecureBoot= Disabled and then set to "UEFI Native (with no CSM)". With Secureboot enabled, my customers had problems with Linux. Also had problems if set to UEFI Hybrid.

What is the BIOS version? And what Generation (Gx)?

As I remember, there was a few hotkey diagnostics functions for that... First was to turn off the computer and unplug the power cord. Then turn on the power via pressing an holding the power key for 11 seconds. That clears the Electronic Controller. If that didn't do it, then next was to turn out the computer, Press and hold down the Win and V keys while simultaneously pressing the power button until a BIOS ERROR message pops up which will tell you to press Enter to continue. That cleared the CMOS. Further from that would be to do what you did via Win, B and power button, which restes the BIOS to an earlier version... Which means it rolled back the BIOS version and you are not running a current version of BIOS.

Those hot key presses should only be 2-3 seconds... If the BIOS Error screen just shows repeatedly, then you need to use an USB Recovery key to load a new BIOS Image to recover it. With that you create an "HP Tool" Key with the BIOS Image... Then while off and the USB key inserted, do the WIN/B/Power button combination and it will boot the USB Recovery Tool...

Their were several BIOS updates for it. Which updating to current may fix your troubles.

---

### Post by r2020r on 2023-01-04
Thanks **MAFoElffen**
> **MAFoElffen said:**
> Wow. Triple posted. From my notes on that laptop, Try a setting of SecureBoot= Disabled and then set to "UEFI Native (with no CSM)". With Secureboot enabled, my customers had problems with Linux. Also had problems if set to UEFI Hybrid.

What is the BIOS version? And what Generation (Gx)?


I tried updating BIOS from BIOS itself, using Ethernet. It showed following. I have attached the screen shot also, please take a look. **Is it suggesting to downgrade to 01.45?**. Please advise.

Bios version is **01.47 (03/03/2020)**
Zbook 15(Dream color display). This is the very first version in Zbook series.

---

### Post by r2020r on 2023-01-04
> **MAFoElffen said:**
> Wow. Triple posted. From my notes on that laptop, Try a setting of SecureBoot= Disabled and then set to "UEFI Native (with no CSM)". With Secureboot enabled, my customers had problems with Linux. Also had problems if set to UEFI Hybrid.


I tried both these combinations and did not solve the *infinite boot* problem.
[LIST]
[*]UEFI Native (with no CSM), Secure = OFF, 3rd party Graphic drivers
[*]UEFI Native (with no CSM), Secure = OFF
[/LIST]

Should I focus on solving on "*[COLOR=#111111][FONT=monospace]Error: NVram is locked [/FONT][/COLOR][COLOR=#666666][FONT=monospace]([/FONT][/COLOR][COLOR=#111111][FONT=monospace]Ubuntu not found in efibootmgr[/FONT][/COLOR]*[COLOR=#666666][FONT=monospace]*)*"?
[/FONT][/COLOR]Will I try changing TPM options in BIOS?

Please let me know, if you can think of any other option to try.

Thanks

---

### Post by r2020r on 2023-01-04
1) With BIOS **01.47 (03/03/2020) **I installed on LEGACY mode. System failed to boot saying "Boot device not found". May be mSATA is not supported in Legacy mode, not sure.

2) I downgraded the BIOS from **01.47 (03/03/2020) ** to **01.45 (04/17/2019) **tried following combinations. In all these infinite restart continued. 
[LIST]
[*]UEFI Native (with no CSM), Secure = OFF
[*]UEFI Native (with no CSM), Secure = ON
[*]UEFI Hybrid (with CSM), Secure = OFF
[/LIST]


3) With BIOS **01.45 (****04/17/2019****) **I installed on LEGACY mode. System failed to boot saying "Boot device not found".

Thanks

---

### Post by tea for one on 2023-01-04
> **r2020r said:**
> 
Should I focus on solving on "*[COLOR=#111111][FONT=monospace]Error: NVram is locked [/FONT][/COLOR][COLOR=#666666][FONT=monospace]([/FONT][/COLOR][COLOR=#111111][FONT=monospace]Ubuntu not found in efibootmgr[/FONT][/COLOR]*[COLOR=#666666][FONT=monospace]*)*"?
[/FONT][/COLOR]Will I try changing TPM options in BIOS?
When you conduct an internet search for TPM & NVram, there is a wealth of information provided. Unfortunately for me, it makes my eyes glaze over.
Nevertheless, they are both involved with secure computing.
High levels of security are essential for commercial enterprises but create hurdles for home users.
It should be incumbent on the PC vendors to make the UEFI settings more manageable.

oldfred mentioned HP being sometimes unfriendly to Linux users in post 4.
I have also noticed this in my own experience and when reading similar threads in these forum pages.

On my 7 year old HP Stream, the UEFI security settings are:-
Admin Password never used
Power On Password never used
TPM disabled (although available)
Post Hotkey Delay = 5 seconds
Legacy Support disabled
Secure Boot disabled

In your position, I would certainly try with TPM disabled.
Disabled TPM may unlock the NVram?
If you have PTT (Platform Trust Technology), try with that setting disabled also.

---

### Post by r2020r on 2023-01-04
Thanks tea for one. Your mail gave more clues.

Hi All

I was able to solve by following these steps(I am documenting in verbose fashion so that I can use it in future for myself).

[LIST=1]
[*]**Enable TPM**: Inside BIOS "*TPM Embedded security*" was grayed out. To enable "*TPM Embedded security*", I temporarily set a BIOS password. Once the temp password was set, "*TPM Embedded security*" got enabled. Inside "*TPM Embedded security*", I disabled two options: "*Embedded Security device state*" and "*OS Management of TPM*" ("*TPM Embedded security" is in security Tab)*
[*]Changed the BIOS password to "". This is same as disabling BIOS password
[*]Changed boot mode in BIOS to ***UEFI Hybrid (with CSM), Secure = OFF*. Note: "***UEFI Native*" lead to display issue at post install stage so I chose *UEFI Hybrid*.
[*]Installed Ubuntu and selected *3rd party drivers for display*. Note: Not having 3rd party drivers lead to display issue at post install stage.
[*]Installation succeeded.
[*]There was **NO repeated Reboot**. Major victory
[*]But the display was still LOW RES. OS was using its driver for Display. I tried installing Nvidia driver using "*Additional Drivers*" tool and it failed, so I thought of enabling *Secure boot*. *Secure boot *stays grayed out in all boot modes except *UEFI Native*.
[*]Changed boot mode in BIOS to **UEFI Native, Secure = ON**
[*]Booted into OS and installed *Nvidia driver (390)* using "*Additional Drivers*" tool. Driver installation succeeded and display resolution became proper. (Nvidia driver 418 installation failed)
[/LIST]

Note: Disabling "*Embedded Security device state*" and "*OS Management of TPM*" was just trail and error. I could have kept "OS Management of TPM" checked but did not.

Thanks

---

### Post by tea for one on 2023-01-04
Congratulations - your perseverance is admirable.
There is lots of useful info in this thread and, if you see fit, it is a nice gesture to mark the thread as solved (beneficial to other forum members and searchers).
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

The detail in post 15 only reinforces my ingrained opinion to try and avoid HP laptops in the future.

It is also a shame that HP printers used to be Linux friendly but have a look at this 
[https://ubuntuforums.org/showthread.php?t=2481520](https://ubuntuforums.org/showthread.php?t=2481520)

---

### Post by Impavidus on 2023-01-04
> **MAFoElffen said:**
> This would be the first time in 13 years of supporting Ubuntu, that I even heard that an installation would or even could change the BIOS settings!
Well, there was that issue with Ubuntu 17.10: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)
It could be triggered by just booting the live disk, so the original 17.10 live disk image was pulled from the servers and replaced with 17.10.1, AFAIK the only time an interim release got a point release. But that was all fixed a long time ago.

---

### Post by MAFoElffen on 2023-01-04
You both seem to be a difference time zone than me (LOL)... Woke up to lots of activity and changes.

"NVRAM lockup" is a BIOS type error problem. Concentrate on the BIOS Version and settings. I kind of remember some BIOS problems where a rollback was needed on Dells, but not on HP's... but looking through my service bulletins...

I asked what the generation "sub-model" was (or product number) so I could look up the service bulletins and BIOS release notes. That would be helpful. (There was a BIOS release in June 8, 2021 that had a lot of security updates for models with Intel Processors, that affected a lot of models <[HP Reference HPSBHF03735 Rev. 4]("https://support.hp.com/us-en/document/ish_3982318-3982351-16")>.) I kind of remember some, problems surrounding that between the brands. (but mostly on Dell.)

---

### Post by MAFoElffen on 2023-01-04
Here is the full error I found concerning the use of UEFI Hybrid (with CSM):
> 
WindowsEFI detected. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode.

(I'm a contributor to boot-repair and searched through my notes.)

A related answer to get around "NVram Lockup", on a problem that oldfred had mentioned: [https://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](https://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

But a fix to try before that, to unlock the NVRam is to zero out (format) the device:
```

sudo modprobe nvram
sudo dd if=/dev/zero of=/dev/nvram

```
Then shut down cold. Let sit for a bit, then start while clearing the CMOS, to retest.

I have tested this on one of my own devices, and this does not seem to do anything that would cause any harm. It just writes "0's" to clear the NVRam device.

---

