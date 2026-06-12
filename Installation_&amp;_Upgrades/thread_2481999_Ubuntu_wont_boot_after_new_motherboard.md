---
title: "Ubuntu wont boot after new motherboard"
date: 2022-12-15
forum: Installation &amp; Upgrades
---

### Post by rainbowgrisea-74 on 2022-12-15
Hello!
I have Ubuntu and Windows 10 installed on my SSD. After I changed my motherboard my PC wont boot, I'm stuck at grub. 
This is what boot repair program managed to find out:


boot-repair-4ppa203                                              [20221215_2019]


============================== Boot Info Summary ===============================


 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 
    43008 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt4)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bootx64.efi /efi/BOOT/grub.cfg


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi




================================ 0 OS detected =================================




================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Navi 23 [Radeon RX 6600/6600 XT/6600M] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.1 LTS, jammy, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 1.D0(5.13) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0001
Boot0001* UEFI OS	HD(1,GPT,f497799c-3108-4810-868e-cadc44fb7503,0xb000,0x14000)/File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot0002* UEFI: KingstonDataTraveler 3.0PMAP, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(13,0)/HD(1,MBR,0x1f4ffd,0x800,0x1d4da80)..BO


7202398d9391b81094e60278fb283cdd   sdb1/BOOT/bootx64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sdb	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdb1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far


Partitions info (2/3): _________________________________________________________


sda1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot
sdb1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sdb1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb


fdisk -l (filtered): ___________________________________________________________


Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0xe35083b2
      Boot Start       End   Sectors   Size Id Type
sda1  *     2048 976769023 976766976 465.8G  7 HPFS/NTFS/exFAT
Disk sdb: 111.79 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: 75EC96FF-FEA6-4E82-8270-2359AA33BF56
      Start    End Sectors Size Type
sdb1  45056 126975   81920  40M EFI System
Disk sdc: 14.65 GiB, 15733161984 bytes, 30728832 sectors
Disk identifier: 0x001f4ffd
      Boot Start      End  Sectors  Size Id Type
sdc1  *     2048 30728831 30726784 14.7G  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:500GB:scsi:512:512:msdos:ATA WDC WD5000AAKX-0:;
1:1049kB:500GB:500GB:ntfs::boot;
sdb:120GB:scsi:512:512:gpt:ATA SSD 120GB:;
1:23.1MB:65.0MB:41.9MB:fat32:EFI System:boot, esp;
sdc:15.7GB:scsi:512:512:msdos:Kingston DataTraveler 3.0:;
1:1049kB:15.7GB:15.7GB:fat32::boot, lba;


Free space >10MiB: ______________________________________________________________


sdb: 0.02MiB:22.0MiB:22.0MiB
sdb: 62.0MiB:114473MiB:114411MiB


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9492;&#9472;sda1 ntfs     9E14066A140645AD                     e35083b2-01                          Storage     
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     6FC2-583A                            f497799c-3108-4810-868e-cadc44fb7503             EFI System
sdc                                                                                                   
&#9492;&#9472;sdc1 vfat     82D6-B212                            001f4ffd-01                          UBUNTU 22_0 


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda1                298G  36% /mnt/boot-sav/sda1
/dev/sdb1               38.4M   2% /mnt/boot-sav/sdb1
/dev/sdc1               11.1G  24% /cdrom


Mount options (filtered): ______________________________________________________




====================== sdb1/efi/BOOT/grub.cfg (filtered) =======================


#search --label hiveroot --set root
search --fs-uuid b4b60f60-cd34-49c7-859b-53f802e8659c --set root
set prefix=($root)'/boot/grub'
configfile $prefix/grub.efi.cfg


====================== sdc1/boot/grub/grub.cfg (filtered) ======================


Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


==================== sdc1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would not act on the boot.

---

### Post by MAFoElffen on 2022-12-15
Change the order of the SATA disk cables on the two drives... Right not your second drive is the one with the EFI partition... Just a quick observation.

---

### Post by rainbowgrisea-74 on 2022-12-15
Thank you! I changed the order of cables, run the program. 
This is what I get after repairing:

boot-repair-4ppa203                                              [20221215_2143]


============================= Boot Repair Summary ==============================










GPT PMBR size mismatch (14745599 != 234441647) will be corrected by write.


Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi of
sdb8,
using the following options:  sdb1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file




Mount sdb1 on /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f/boot/efi


Unhide GRUB boot menu in sdb8/etc/default/grub


======================== Reinstall the grub-efi of sdb8 ========================


chroot /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f grub-install --version
grub-install (GRUB) 2.06-2ubuntu7
chroot /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f modprobe efivars


chroot /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f efibootmgr -v before grub install
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0001,0002,0003
Boot0001* UEFI OS	HD(1,GPT,f497799c-3108-4810-868e-cadc44fb7503,0xb000,0x14000)/File(EFIBOOTBOOTX64.EFI)..BO
Boot0002* Windows Boot Manager	HD(1,GPT,737efc00-1334-4442-8a8f-b31f722b6620,0x800,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)..BO
Boot0003* ubuntu	HD(1,GPT,737efc00-1334-4442-8a8f-b31f722b6620,0x800,0x32000)/File(EFIUBUNTUSHIMX64.EFI)..BO
Boot0004* UEFI: KingstonDataTraveler 3.0PMAP, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(6,0)/HD(1,MBR,0x1f4ffd,0x800,0x1d4da80)..BO


chroot /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f uname -r
5.15.0-43-generic


chroot /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
cp /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sdc1/EFI/ubuntu/grubx64.efi
df /dev/sdb1
mv /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f/boot/efi/EFI/Boot/bootx64.efi /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f/boot/efi/EFI/Boot/bkpbootx64.efi
cp /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f/boot/efi/efi/ubuntu/grubx64.efi /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f/boot/efi/EFI/Boot/bootx64.efi
df /dev/sdc1
mv /mnt/boot-sav/sdc1/EFI/Boot/bootx64.efi /mnt/boot-sav/sdc1/EFI/Boot/bkpbootx64.efi
cp /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sdc1/EFI/Boot/bootx64.efi


chroot /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.


chroot /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f efibootmgr -v after grub install
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0001,0002,0003
Boot0001* UEFI OS	HD(1,GPT,f497799c-3108-4810-868e-cadc44fb7503,0xb000,0x14000)/File(EFIBOOTBOOTX64.EFI)..BO
Boot0002* Windows Boot Manager	HD(1,GPT,737efc00-1334-4442-8a8f-b31f722b6620,0x800,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)..BO
Boot0003* ubuntu	HD(1,GPT,737efc00-1334-4442-8a8f-b31f722b6620,0x800,0x32000)/File(EFIUBUNTUSHIMX64.EFI)..BO
Boot0004* UEFI: KingstonDataTraveler 3.0PMAP, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(6,0)/HD(1,MBR,0x1f4ffd,0x800,0x1d4da80)..BO
Warning: NVram was not modified.


chroot /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-56-generic
Found initrd image: /boot/initrd.img-5.15.0-56-generic
Found linux image: /boot/vmlinuz-5.15.0-53-generic
Found initrd image: /boot/initrd.img-5.15.0-53-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sdb1@/EFI/Microsoft/Boot/bootmgfw.efi


Unhide GRUB boot menu in sdb8/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.1 LTS entry (sdb1/efi/ubuntu/grubx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi




============================ Boot Info After Repair ============================


 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 
    43008 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt4)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


sdb2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sdb3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe


sdb4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb7: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb8: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/BOOT/grub.cfg


sdd1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi




================================ 2 OS detected =================================


OS#1:   Ubuntu 22.04.1 LTS on sdb8
OS#2:   Windows 10 or 11 on sdb3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Navi 23 [Radeon RX 6600/6600 XT/6600M] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.1 LTS, jammy, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 1.D0(5.13) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0001,0002,0003
Boot0001* UEFI OS	HD(1,GPT,f497799c-3108-4810-868e-cadc44fb7503,0xb000,0x14000)/File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot0002* Windows Boot Manager	HD(1,GPT,737efc00-1334-4442-8a8f-b31f722b6620,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0003* ubuntu	HD(1,GPT,737efc00-1334-4442-8a8f-b31f722b6620,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0004* UEFI: KingstonDataTraveler 3.0PMAP, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(6,0)/HD(1,MBR,0x1f4ffd,0x800,0x1d4da80)..BO


728124f6ec8e22fbdbe7034812c81b95   sdb1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sdb1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   sdb1/Boot/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   sdb1/Boot/mmx64.efi
3795ef72a4ed0369ca44e711527904bf   sdb1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sdb1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sdb1/ubuntu/shimx64.efi
d1f6c29ed98f2a8102fd87c118371e0b   sdb1/Microsoft/Boot/bootmgfw.efi
85b10a5efd8419adc616cb2a5a70db30   sdb1/Microsoft/Boot/bootmgr.efi
7202398d9391b81094e60278fb283cdd   sdc1/BOOT/bkpbootx64.efi
3795ef72a4ed0369ca44e711527904bf   sdc1/BOOT/bootx64.efi
3795ef72a4ed0369ca44e711527904bf   sdc1/ubuntu/grubx64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sdb	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes
sdc	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdb1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdb3	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdb4	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdb5	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdb7	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdb8	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios
sdc1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far


Partitions info (2/3): _________________________________________________________


sda1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot
sdb1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb3	: isnotESP,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb4	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
sdb5	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
sdb7	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb8	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdc1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sdb1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdb3	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdb4	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdb5	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdb7	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdb8	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sdb
sdc1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdc


fdisk -l (filtered): ___________________________________________________________


Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0xe35083b2
      Boot Start       End   Sectors   Size Id Type
sda1  *     2048 976769023 976766976 465.8G  7 HPFS/NTFS/exFAT
Disk sdb: 111.79 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: DE249E97-E785-4C32-9670-F041C4C36290
          Start       End   Sectors  Size Type
sdb1       2048    206847    204800  100M EFI System
sdb2     206848    239615     32768   16M Microsoft reserved
sdb3     239616 124978603 124738988 59.5G Microsoft basic data
sdb4  124979200 126066687   1087488  531M Windows recovery environment
sdb5  233402368 234438655   1036288  506M Windows recovery environment
sdb6  126066688 134066175   7999488  3.8G Linux swap
sdb7  134066176 166066175  32000000 15.3G Linux filesystem
sdb8  166066176 233402367  67336192 32.1G Linux filesystem
Partition table entries are not in disk order.
Disk sdc: 111.79 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: 75EC96FF-FEA6-4E82-8270-2359AA33BF56
      Start    End Sectors Size Type
sdc1  45056 126975   81920  40M EFI System
Disk sdd: 14.65 GiB, 15733161984 bytes, 30728832 sectors
Disk identifier: 0x001f4ffd
      Boot Start      End  Sectors  Size Id Type
sdd1  *     2048 30728831 30726784 14.7G  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:500GB:scsi:512:512:msdos:ATA WDC WD5000AAKX-0:;
1:1049kB:500GB:500GB:ntfs::boot;
sdb:120GB:scsi:512:512:gpt:ATA Samsung SSD 850:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:64.0GB:63.9GB:ntfs:Basic data partition:msftdata;
4:64.0GB:64.5GB:557MB:ntfs::hidden, diag;
6:64.5GB:68.6GB:4096MB:linux-swap(v1)::swap;
7:68.6GB:85.0GB:16.4GB:ext4::;
8:85.0GB:120GB:34.5GB:ext4::;
5:120GB:120GB:531MB:ntfs::hidden, diag;
sdc:120GB:scsi:512:512:gpt:ATA SSD 120GB:;
1:23.1MB:65.0MB:41.9MB:fat32:EFI System:boot, esp;
sdd:15.7GB:scsi:512:512:msdos:Kingston DataTraveler 3.0:;
1:1049kB:15.7GB:15.7GB:fat32::boot, lba;


Free space >10MiB: ______________________________________________________________


sdc: 0.02MiB:22.0MiB:22.0MiB
sdc: 62.0MiB:114473MiB:114411MiB


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9492;&#9472;sda1 ntfs     9E14066A140645AD                     e35083b2-01                          Storage     
sdb                                                                                                   
&#9500;&#9472;sdb1 vfat     5C73-C16B                            737efc00-1334-4442-8a8f-b31f722b6620             EFI system partition
&#9500;&#9472;sdb2                                               ae9d53ac-b97e-40f3-80fb-2ead804f6b43             Microsoft reserved partition
&#9500;&#9472;sdb3 ntfs     22DC783FDC780F73                     f3d24399-33f5-4c55-9f41-8e996df3abb8             Basic data partition
&#9500;&#9472;sdb4 ntfs     BAC6C068C6C0268B                     b6ad18ef-0c11-4e52-97e6-b5202707ed50             
&#9500;&#9472;sdb5 ntfs     00D62910D629080C                     ee8e9ac8-bc57-4c61-9b27-edb3e20ca7ad             
&#9500;&#9472;sdb6 swap     a6687312-f618-410d-9aa5-7a59e6fb8fe2 3c201367-1d56-42c5-b718-9a5742c805d2             
&#9500;&#9472;sdb7 ext4     d4b61d04-791b-4a28-8421-dd2375763772 33eb4044-c775-4bc1-937c-0fcbd6a010a3             
&#9492;&#9472;sdb8 ext4     27ff8319-b73b-4070-9616-63c54fe3555f 7b53582b-eefd-4960-8156-2b3b4feb1906             
sdc                                                                                                   
&#9492;&#9472;sdc1 vfat     6FC2-583A                            f497799c-3108-4810-868e-cadc44fb7503             EFI System
sdd                                                                                                   
&#9492;&#9472;sdd1 vfat     82D6-B212                            001f4ffd-01                          UBUNTU 22_0 


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda1                298G  36% /media/ubuntu/Storage
/dev/sdb1               64.9M  32% /mnt/boot-sav/sdb1
/dev/sdb3               12.8G  78% /mnt/boot-sav/sdb3
/dev/sdb4               88.7M  83% /mnt/boot-sav/sdb4
/dev/sdb5               88.1M  83% /mnt/boot-sav/sdb5
/dev/sdb7                3.4G  72% /media/ubuntu/d4b61d04-791b-4a28-8421-dd2375763772
/dev/sdb8               12.9G  53% /media/ubuntu/27ff8319-b73b-4070-9616-63c54fe3555f
/dev/sdc1               35.1M  11% /mnt/boot-sav/sdc1
/dev/sdd1               11.1G  24% /cdrom


Mount options (filtered): ______________________________________________________




===================== sdb1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 27ff8319-b73b-4070-9616-63c54fe3555f root hd1,gpt8 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sdb8/boot/grub/grub.cfg (filtered) ======================


Ubuntu   27ff8319-b73b-4070-9616-63c54fe3555f
Ubuntu, with Linux 5.15.0-56-generic   27ff8319-b73b-4070-9616-63c54fe3555f
Ubuntu, with Linux 5.15.0-53-generic   27ff8319-b73b-4070-9616-63c54fe3555f
Windows Boot Manager (on sdb1)   osprober-efi-5C73-C16B
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sdb8/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=27ff8319-b73b-4070-9616-63c54fe3555f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=5C73-C16B  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda7 during installation
UUID=d4b61d04-791b-4a28-8421-dd2375763772 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a6687312-f618-410d-9aa5-7a59e6fb8fe2 none            swap    sw              0       0
/dev/disk/by-uuid/9E14066A140645AD /mnt/9E14066A140645AD auto nosuid,nodev,nofail,x-gvfs-show 0 0


======================= sdb8/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sdb8: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
  91.111343384 = 97.830060032   boot/vmlinuz                                   1
  80.447277069 = 86.379606016   boot/vmlinuz-5.15.0-53-generic                 1
  91.111343384 = 97.830060032   boot/vmlinuz-5.15.0-56-generic                 1
  80.447277069 = 86.379606016   boot/vmlinuz.old                               1
  98.436519623 = 105.695408128  boot/initrd.img                                2
 100.999019623 = 108.446871552  boot/initrd.img-5.15.0-53-generic              2
  98.436519623 = 105.695408128  boot/initrd.img-5.15.0-56-generic              2
 100.999019623 = 108.446871552  boot/initrd.img.old                            2


===================== sdb8: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15  2022 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom


====================== sdc1/efi/BOOT/grub.cfg (filtered) =======================


#search --label hiveroot --set root
search --fs-uuid b4b60f60-cd34-49c7-859b-53f802e8659c --set root
set prefix=($root)'/boot/grub'
configfile $prefix/grub.efi.cfg


====================== sdd1/boot/grub/grub.cfg (filtered) ======================


Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


==================== sdd1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

---

### Post by rainbowgrisea-74 on 2022-12-15
I managed to boot my OS, but after restarting it is stuck at grub again...

---

### Post by MAFoElffen on 2022-12-15
Is this good or not then? It's marked as solved but you said you were still stuck at boot(???) I'm confused.

---

