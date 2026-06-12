---
title: "Lenovo G510 &quot;ubuntu boot failed&quot;, boot-repair didn't help"
date: 2024-11-09
forum: Installation &amp; Upgrades
---

### Post by dwlcpablo on 2024-11-09
Issue after removing windows8 from Lenovo G510 and replacing it with ubuntu 20.04, the OS fails to load, with a message "ubuntu boot failed."

Boot-Repair report: [https://paste.ubuntu.com/p/zYyRYHdhBT/](https://paste.ubuntu.com/p/zYyRYHdhBT/)

> boot-repair-4ppa2081                                              [20241109_1532]

============================= Boot Repair Summary ==============================












Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda5,
using the following options:  sda2/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups




rm /mnt/boot-sav/sda2/efi/Microsoft/Boot/bootmgfw.efi /mnt/boot-sav/sda2/efi/Microsoft/Boot/bootmgfw.efi.grb
rm /mnt/boot-sav/sda2/efi/Microsoft/Boot/bootx64.efi /mnt/boot-sav/sda2/efi/Microsoft/Boot/bootx64.efi.grb
rm /mnt/boot-sav/sda2/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda2/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda2/efi/Boot/bootx64.efi
Mount /dev/sda2 on /mnt/boot-sav/sda5/boot/efi


===================== Reinstall the grub-efi of /dev/sda5 ======================


chroot /mnt/boot-sav/sda5 grub-install --version
grub-install (GRUB) 2.04-1ubuntu26.13
chroot /mnt/boot-sav/sda5 modprobe efivars


chroot /mnt/boot-sav/sda5 efibootmgr -v (filtered) before grub install
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,0004,2001,2003,2002
Boot0000* EFI USB Device (SCSI    SG 1.8.1.7.0 2+6)	PciRoot(0x0)/Pci(0x1a,0x0)/USB(0,0)/USB(1,0)/HD(1,MBR,0x2cf4ba3a,0x506fcc,0x1f40)RC
Boot0001* Windows Boot Manager	HD(2,MBR,0x9c5fdcd5,0x100800,0x100800)/File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0002* EFI Network 0 for IPv4 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* EFI Network 0 for IPv6 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0004* ubuntu	HD(2,MBR,0x9c5fdcd5,0x100800,0x100800)/File(EFIubuntushimx64.efi)RC
Boot0008* EFI Network 0 for IPv4 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0009* EFI Network 0 for IPv6 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv6([::]:<->[::]:,0,0)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


chroot /mnt/boot-sav/sda5 uname -r
5.11.0-27-generic


chroot /mnt/boot-sav/sda5 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda2
mv /mnt/boot-sav/sda5/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda5/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda5/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda5/boot/efi/EFI/Boot/bootx64.efi


chroot /mnt/boot-sav/sda5 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.


chroot /mnt/boot-sav/sda5 efibootmgr -v (filtered) after grub install
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0004,0001,2001,2003,2002
Boot0000* EFI USB Device (SCSI    SG 1.8.1.7.0 2+6)	PciRoot(0x0)/Pci(0x1a,0x0)/USB(0,0)/USB(1,0)/HD(1,MBR,0x2cf4ba3a,0x506fcc,0x1f40)RC
Boot0001* Windows Boot Manager	HD(2,MBR,0x9c5fdcd5,0x100800,0x100800)/File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0002* EFI Network 0 for IPv4 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* EFI Network 0 for IPv6 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0004* ubuntu	HD(2,MBR,0x9c5fdcd5,0x100800,0x100800)/File(EFIubuntugrubx64.efi)
Boot0008* EFI Network 0 for IPv4 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0009* EFI Network 0 for IPv6 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv6([::]:<->[::]:,0,0)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


chroot /mnt/boot-sav/sda5 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Found linux image: /boot/vmlinuz-5.11.0-27-generic
Found initrd image: /boot/initrd.img-5.11.0-27-generic
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Adding boot menu entry for UEFI Firmware Settings


Unhide GRUB boot menu in sda5/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.3 LTS entry (sda2/efi/ubuntu/grubx64.efi file) !




============================ Boot Info After Repair ============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg


sda3: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


sdb: ___________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.




================================ 1 OS detected =================================


OS#1 (linux):   Ubuntu 20.04.3 LTS on sda5


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Jet PRO [Radeon R5 M230 / R7 M260DX / Radeon 520 Mobile] Haswell Integrated Graphics Controller from Advanced Micro Devices, Inc. [AMD/ATI] Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 79CN49WW(V3.08)(1.73) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0004,0001,2001,2003,2002
Boot0000* EFI USB Device (SCSI    SG 1.8.1.7.0 2+6)	PciRoot(0x0)/Pci(0x1a,0x0)/USB(0,0)/USB(1,0)/HD(1,MBR,0x2cf4ba3a,0x506fcc,0x1f40)RC
Boot0001* Windows Boot Manager	HD(2,MBR,0x9c5fdcd5,0x100800,0x100800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0002* EFI Network 0 for IPv4 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* EFI Network 0 for IPv6 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0004* ubuntu	HD(2,MBR,0x9c5fdcd5,0x100800,0x100800)/File(\EFI\ubuntu\grubx64.efi)
Boot0008* EFI Network 0 for IPv4 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0009* EFI Network 0 for IPv6 (F0-76-1C-14-DB-6A) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(f0761c14db6a,0)/IPv6([::]:<->[::]:,0,0)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


06bc91534ebe6a85cdd56251fbaa9346   sda2/BOOT/bkpbootx64.efi
06bc91534ebe6a85cdd56251fbaa9346   sda2/BOOT/bootx64.efi
85fa9d77b929ec4231aba29476574eb6   sda2/BOOT/fbx64.efi
469e608783843a701d172242f016c79c   sda2/BOOT/mmx64.efi
06bc91534ebe6a85cdd56251fbaa9346   sda2/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sda2/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda2/ubuntu/shimx64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: notGPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda2	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda5	: is-os,	64, apt-get,	grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB


Partitions info (2/3): _________________________________________________________


sda1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, vfat
sda2	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, vfat
sda5	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ext4


Partitions info (3/3): _________________________________________________________


sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda2	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda5	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x9c5fdcd5
     Boot   Start        End    Sectors   Size Id Type
sda1          2048    1050623    1048576   512M  b W95 FAT32
sda2  *    1050624    2101247    1050624   513M ef EFI (FAT-12/16/32)
sda3       2103294 1953523711 1951420418 930.5G  5 Extended
sda5       2103296 1953523711 1951420416 930.5G 83 Linux
Disk sdb: 3.78 GiB, 4035493888 bytes, 7881824 sectors
Disk identifier: 0x2cf4ba3a
     Boot   Start     End Sectors   Size Id Type
sdb1  *          0 5999871 5999872   2.9G  0 Empty
sdb2       5271500 5279499    8000   3.9M ef EFI (FAT-12/16/32)
sdb3       6000640 7881823 1881184 918.6M 83 Linux


parted -lm (filtered): _________________________________________________________


sda:1000GB:scsi:512:4096:msdos:ATA ST1000LM024 HN-M:;
1:1049kB:538MB:537MB:fat32::;
2:538MB:1076MB:538MB:fat32::boot, esp;
3:1077MB:1000GB:999GB:::;
5:1077MB:1000GB:999GB:ext4::;
sdb:4035MB:scsi:512:512:unknown:SCSI SG 1.8.1.7.0 2+6:;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1 vfat     BABE-BB48                            9c5fdcd5-01                                                   
&#9500;&#9472;sda2 vfat     AD1C-4840                            9c5fdcd5-02                                                   
&#9500;&#9472;sda3                                               9c5fdcd5-03                                                   
&#9492;&#9472;sda5 ext4     8244827e-e1da-4a8c-b3df-4cddf614d8d3 9c5fdcd5-05                                                   
sdb    iso9660  2021-08-19-11-03-38-00                                                    Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2021-08-19-11-03-38-00               2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb2 vfat     54C5-9C6C                            2cf4ba3a-02                                                   
&#9492;&#9472;sdb3 ext4     ad9bd5e6-f549-4a86-8630-5d5374cbb439 2cf4ba3a-03                          writable                 


Mount points (filtered): _______________________________________________________


                                                               Avail Use% Mounted on
/dev/sda1                                                       511M   0% /mnt/boot-sav/sda1
/dev/sda2                                                     508.9M   1% /mnt/boot-sav/sda2
/dev/sda5                                                       861G   1% /mnt/boot-sav/sda5
/dev/sdb1                                                          0 100% /cdrom


Mount options (filtered): ______________________________________________________


/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda5                                                     ext4            rw,relatime
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048


===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 8244827e-e1da-4a8c-b3df-4cddf614d8d3 root hd0,msdos5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda5/boot/grub/grub.cfg (filtered) ======================


Ubuntu   8244827e-e1da-4a8c-b3df-4cddf614d8d3
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda5/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=8244827e-e1da-4a8c-b3df-4cddf614d8d3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=AD1C-4840  /boot/efi       vfat    umask=0077      0       1
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
   1.002933502 = 1.076891648    boot/grub/grub.cfg                             1
 855.157474518 = 918.218346496  boot/grub/i386-pc/core.img                     1
   5.862300873 = 6.294597632    boot/vmlinuz                                   2
   5.862300873 = 6.294597632    boot/vmlinuz-5.11.0-27-generic                 2
   6.456050873 = 6.932131840    boot/initrd.img                                4
   6.456050873 = 6.932131840    boot/initrd.img-5.11.0-27-generic              4
   6.456050873 = 6.932131840    boot/initrd.img.old                            4


===================== sda5: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18151 Aug 12  2021 10_linux
-rwxr-xr-x 1 root root 42359 Aug 12  2021 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Aug 12  2021 20_linux_xen
-rwxr-xr-x 1 root root 12059 Aug 12  2021 30_os-prober
-rwxr-xr-x 1 root root  1424 Aug 12  2021 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Aug 12  2021 40_custom
-rwxr-xr-x 1 root root   216 Aug 12  2021 41_custom

---

### Post by tea for one on 2024-11-09
There are a few idiosyncrasies in your installation:-
[LIST]
[*]Grub installed in the mbr of /dev/sda
[*]msdos partition table
[*]Two vfat (fat32) partitions sda1 and sda2
[*]Extended partition sda3
[*]Old fashioned logical partition sda5
[*]
[/LIST]
In your position, I would install again in UEFI mode with gpt

Boot into a &#8220;Try Ubuntu&#8221; live session and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Use gparted to create a GPT (GUID Partition Table)
Allow the installer to automatically create the necessary partitions

Edit: Any reason not to try 24.04 (either Ubuntu itself or a lighter flavour?)

---

### Post by yancek on 2024-11-09
Do you get this error when you set  Boot0004* (Ubuntu entry) to first boot priority in the BIOS?  Have you disabled Legacy boot in the BIOS.  

You have an EFI entry for windows Boot0001*so if that actually booted, it must have been a GPT drive, at least that is what Microsoft says is the requirement.  sda1 was probably the windows EFI partition where you could have installed the Ubuntu EFI files in a separate directory but apparently you deleted the existing EFI and created a second one (sda2) as well as changing the drive from GPT.

Simplest solution is to follow the advice in post 2.

---

### Post by dwlcpablo on 2024-11-11
Thx a lot guys, the gparted step helped - I created a GPT with gparted, rerun the installer and all is fine. Previously, the laptop was running a Windows 8, and i somehow borked the boot with the initial installation.

---

