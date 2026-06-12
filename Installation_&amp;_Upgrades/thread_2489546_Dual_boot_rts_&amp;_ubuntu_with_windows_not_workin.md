---
title: "Dual boot rts &amp; ubuntu with windows not working | Boot-repair scan"
date: 2023-08-02
forum: Installation &amp; Upgrades
---

### Post by johnli30 on 2023-08-02
I was given a 10th gen pc that already had windows 10 which I upgraded to 11. I installed ubuntu 20.04 and first got the alert for rts & ubuntu. I changed to AHCI mode in the bios and continue my installation without problem. Except that after restarting, when I choose windows, I have the blue screen then preparation for repair but nothing good in the end. 
Even the boot is not stable because sometimes it does not offer me to choose between windows and ubuntu but it goes directly to the grub terminal. To return to normal, I go to the bios where I have the possibility of starting on ubuntu (which offers me the choices of the system) or on windows.
In searches, I found boot-repair of which below is the result of the analysis. But I find it curious that it detects windows 7 as the installed OS. 
Then continue anyway with the boot-repair recommendations?


Thanks in advance for your help.

```
boot-repair-4ppa203                                              [20230802_1513]
============================== Boot Info Summary ===============================
 => No boot loader is installed in the MBR of /dev/nvme0n1. => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sda.
nvme0n1p1: _____________________________________________________________________
    File system:           Boot sector type:  -    Boot sector info: 
nvme0n1p2: _____________________________________________________________________
    File system:       vfat    Boot sector type:  Windows 8/10/11/2012: FAT32    Boot sector info:  No errors found in the Boot Parameter Block.    Operating System:      Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi                        /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi                        /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi                        /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi                        /efi/Microsoft/Boot/bootmgr.efi                        /efi/Microsoft/Boot/cbmr_driver.efi
nvme0n1p3: _____________________________________________________________________
    File system:       ntfs    Boot sector type:  Windows 8/10/11/2012: NTFS    Boot sector info:  No errors found in the Boot Parameter Block.    Operating System:  Windows 7    Boot files:        /bootmgr /Windows/System32/winload.exe
nvme0n1p4: _____________________________________________________________________
    File system:       ntfs    Boot sector type:  Windows 8/10/11/2012: NTFS    Boot sector info:  No errors found in the Boot Parameter Block.    Operating System:      Boot files:        
nvme0n1p5: _____________________________________________________________________
    File system:       ntfs    Boot sector type:  Windows 8/10/11/2012: NTFS    Boot sector info:  No errors found in the Boot Parameter Block.    Operating System:      Boot files:        
sda1: __________________________________________________________________________
    File system:       ntfs    Boot sector type:  Windows 8/10/11/2012: NTFS    Boot sector info:  No errors found in the Boot Parameter Block.    Operating System:      Boot files:        
sda2: __________________________________________________________________________
    File system:       ntfs    Boot sector type:  Windows 8/10/11/2012: NTFS    Boot sector info:  No errors found in the Boot Parameter Block.    Operating System:      Boot files:        
sda3: __________________________________________________________________________
    File system:       ext4    Boot sector type:  -    Boot sector info:     Operating System:  Ubuntu 20.04.6 LTS    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

================================ 2 OS detected =================================
OS#1:   Ubuntu 20.04.6 LTS on sda3OS#2:   Windows 7 on nvme0n1p3
================================ Host/Hardware =================================
CPU architecture: 64-bitVideo: Intel Corporation from Intel CorporationBOOT_IMAGE of the installed session in use:/boot/vmlinuz-5.15.0-78-generic root=UUID=9878b34c-05b3-4537-bb0a-f791bdeb361e ro quiet splash vt.handoff=7df -Th / : /dev/sda3        ext4    98G     18G   76G  19% /
===================================== UEFI =====================================
BIOS/UEFI firmware: X509JA.310(5.14) from American Megatrends Inc.The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.SecureBoot enabled.BootCurrent: 0000Timeout: 1 secondsBootOrder: 0000,0005Boot0000* ubuntu    HD(2,GPT,458f8e82-d7d3-4914-9782-5a4bd702c1be,0x40800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)Boot0005* Windows Boot Manager    HD(2,GPT,458f8e82-d7d3-4914-9782-5a4bd702c1be,0x40800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................

============================= Drive/Partition Info =============================
Disks info: ____________________________________________________________________
sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytesnvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    34 sectors * 512 bytes
Partitions info (1/3): _________________________________________________________
sda3    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbiosnvme0n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-farnvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbiosnvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbiosnvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbiossda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbiossda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
Partitions info (2/3): _________________________________________________________
sda3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinbootnvme0n1p2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinbootnvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinbootnvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinbootnvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinbootsda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinbootsda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
Partitions info (3/3): _________________________________________________________
sda3    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdanvme0n1p2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1nvme0n1p5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdasda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
fdisk -l (filtered): ___________________________________________________________
Disk nvme0n1: 238.49 GiB, 256060514304 bytes, 500118192 sectorsDisk identifier: F031F55E-65A2-45D2-B1AB-19AD4F53AD4C              Start       End   Sectors  Size Typenvme0n1p1        34    262177    262144  128M Microsoft reservednvme0n1p2    264192    468991    204800  100M EFI Systemnvme0n1p3    468992 497495127 497026136  237G Microsoft basic datanvme0n1p4 497496064 499003391   1507328  736M Windows recovery environmentnvme0n1p5 499007488 500117503   1110016  542M Windows recovery environmentDisk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectorsDisk identifier: 0x1156b32f      Boot      Start        End   Sectors   Size Id Typesda1             2048  903716863 903714816 430.9G  7 HPFS/NTFS/exFATsda2        903716864 1743804415 840087552 400.6G  7 HPFS/NTFS/exFATsda3       1743804416 1953523711 209719296   100G 83 Linux
parted -lm (filtered): _________________________________________________________
sda:1000GB:scsi:512:4096:msdos:ATA TOSHIBA MQ04ABF1:;1:1049kB:463GB:463GB:ntfs::;2:463GB:893GB:430GB:ntfs::;3:893GB:1000GB:107GB:ext4::;nvme0n1:256GB:nvme:512:512:gpt:SPCC M.2 PCIe SSD:;1:17.4kB:134MB:134MB:::msftres;2:135MB:240MB:105MB:fat32::boot, esp;3:240MB:255GB:254GB:ntfs::msftdata;4:255GB:255GB:772MB:ntfs::hidden, diag;5:255GB:256GB:568MB:ntfs::diag;
blkid (filtered): ______________________________________________________________
NAME        FSTYPE   UUID                                 PARTUUID                             LABEL        PARTLABELsda                                                                                                         &#9500;&#9472;sda1      ntfs     EC48855D48852802                     1156b32f-01                                       &#9500;&#9472;sda2      ntfs     B6D8B8FED8B8BDC5                     1156b32f-02                          Disque local &#9492;&#9472;sda3      ext4     9878b34c-05b3-4537-bb0a-f791bdeb361e 1156b32f-03                                       nvme0n1                                                                                                     &#9500;&#9472;nvme0n1p1                                               3efea6d5-110c-4bc0-a0f9-8db0660cb16e              &#9500;&#9472;nvme0n1p2 vfat     90F9-17BC                            458f8e82-d7d3-4914-9782-5a4bd702c1be              &#9500;&#9472;nvme0n1p3 ntfs     DC3EFBD03EFBA1A6                     e7359663-2507-46a4-b45f-1208b1020bee              &#9500;&#9472;nvme0n1p4 ntfs     70FC0AABFC0A6C22                     eeb2376c-2a39-403d-88ce-4468a5018202              &#9492;&#9472;nvme0n1p5 ntfs     C80C358D0C357790                     c952b4e6-08c4-4b80-a53e-6989f00e13c4              
Mount points (filtered): _______________________________________________________
                Avail Use% Mounted on/dev/nvme0n1p3 116.9G  51% /mnt/boot-sav/nvme0n1p3/dev/nvme0n1p4  89.5M  88% /mnt/boot-sav/nvme0n1p4/dev/nvme0n1p5  86.9M  84% /mnt/boot-sav/nvme0n1p5/dev/sda1      273.6G  37% /mnt/boot-sav/sda1/dev/sda2      102.8G  74% /mnt/boot-sav/sda2/dev/sda3       75.7G  18% /
Mount options (filtered): ______________________________________________________

=================== nvme0n1p2/efi/ubuntu/grub.cfg (filtered) ===================
search.fs_uuid 9878b34c-05b3-4537-bb0a-f791bdeb361e root hd0,msdos3 set prefix=($root)'/boot/grub'configfile $prefix/grub.cfg
====================== sda3/boot/grub/grub.cfg (filtered) ======================
Ubuntu   9878b34c-05b3-4537-bb0a-f791bdeb361eUbuntu, avec Linux 5.15.0-78-generic   9878b34c-05b3-4537-bb0a-f791bdeb361eUbuntu, avec Linux 5.15.0-67-generic   9878b34c-05b3-4537-bb0a-f791bdeb361eWindows Boot Manager (sur nvme0n1p2)   osprober-efi-90F9-17BC### END /etc/grub.d/30_os-prober ###UEFI Firmware Settings   uefi-firmware### END /etc/grub.d/30_uefi-firmware ###
========================== sda3/etc/fstab (filtered) ===========================
# <file system> <mount point>   <type>  <options>       <dump>  <pass># / was on /dev/sda3 during installationUUID=9878b34c-05b3-4537-bb0a-f791bdeb361e /               ext4    errors=remount-ro 0       1# /boot/efi was on /dev/nvme0n1p2 during installationUUID=90F9-17BC  /boot/efi       vfat    umask=0077      0       1/swapfile                                 none            swap    sw              0       0
======================= sda3/etc/default/grub (filtered) =======================
GRUB_DEFAULT=0GRUB_TIMEOUT_STYLE=hiddenGRUB_TIMEOUT=10GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"GRUB_CMDLINE_LINUX=""
==================== sda3: Location of files loaded by Grub ====================
           GiB - GB             File                                 Fragment(s) 851.846809387 = 914.663546880  boot/grub/grub.cfg                             2 838.701129913 = 900.548481024  boot/vmlinuz                                   1 837.065425873 = 898.792157184  boot/vmlinuz-5.15.0-67-generic                 2 838.701129913 = 900.548481024  boot/vmlinuz-5.15.0-78-generic                 1 837.065425873 = 898.792157184  boot/vmlinuz.old                               2 839.188961029 = 901.072285696  boot/initrd.img                                2 839.142055511 = 901.021921280  boot/initrd.img-5.15.0-67-generic              3 839.188961029 = 901.072285696  boot/initrd.img-5.15.0-78-generic              2 839.142055511 = 901.021921280  boot/initrd.img.old                            3
===================== sda3: ls -l /etc/grub.d/ (filtered) ======================
-rwxr-xr-x 1 root root 18224 Dec  2  2022 10_linux-rwxr-xr-x 1 root root 42359 Dec  2  2022 10_linux_zfs-rwxr-xr-x 1 root root 13101 Dec 18  2022 20_linux_xen-rwxr-xr-x 1 root root 12059 Dec  2  2022 30_os-prober-rwxr-xr-x 1 root root  1424 Dec  2  2022 30_uefi-firmware-rwxr-xr-x 1 root root   700 Jul  3  2022 35_fwupd-rwxr-xr-x 1 root root   214 Dec  2  2022 40_custom-rwxr-xr-x 1 root root   216 Dec  2  2022 41_custom


Suggested repair: ______________________________________________________________
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed ofsda3,using the following options:  nvme0n1p2/boot/efiAdditional repair would be performed: unhide-bootmenu-10s use-standard-efi-file
Final advice in case of suggested repair: ______________________________________
Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.6 LTS entry (nvme0n1p2/efi/****/shim****.efi (**** will be updated in the final message) file) !If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.For example you can boot into Windows, then type the following command in an admin command prompt:bcdedit /set {bootmgr} path \EFI\****\shim****.efi (**** will be updated in the final message)
```

---

### Post by ubfan1 on 2023-08-02
Maybe windows needs the AHCI drivers?  Google for the download.

---

### Post by oldfred on 2023-08-02
Why is sda MBR(msdos)?
Microsoft has required gpt for UEFI boot since 2012, as you have that on your NVMe drive.
The only time you use MBR, is if old system and you have to boot Windows in old BIOS/MBR boot mode.
Ubuntu in either UEFI or BIOS will work from gpt. 

Note, that many tools to convert from MBR to gpt, totally erase drive, so good backups required. 
If lots of data on sda, best to wait and plan for gpt later, but do not use gpt.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by johnli30 on 2023-08-02
Ok thank you for these answers.
I understand that windows was installed from the start in MBR.
I'll just make the backups my datas and restore everything to normal.

---

