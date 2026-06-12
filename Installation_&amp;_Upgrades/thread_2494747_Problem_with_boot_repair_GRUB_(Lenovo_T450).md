---
title: "Problem with boot repair GRUB (Lenovo T450)"
date: 2024-01-25
forum: Installation &amp; Upgrades
---

### Post by claudioroma on 2024-01-25
Good evening, I have a problem that I can't solve with repair boot. 

I have a Lenovo T450 laptop running Windows 10. 

I installed Ubuntu 22.04 via USB and had no problems. 

The Dual boot, with which the system should let me choose the operating system, does not appear, but goes directly to Windows. 

I followed the instructions on this page: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and I produced the bootinfo file residing at this URL: [https://paste.ubuntu.com/p/x7GD2rkb3V/](https://paste.ubuntu.com/p/x7GD2rkb3V/)
 
> boot-repair-4ppa2075                                              [20240125_1520]

============================= Boot Repair Summary ==============================





modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda6,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file


Do you want to remove the [hidden] flag of /dev/sda1 ?
parted /dev/sda set 1 hidden off

                                                                          
[email]SET@_label0.set[/email]_text('''Checking full partitions. Questa operazione potrebbe richiedere diversi minuti...''')
Could not detect USEDPERCENT of /dev/sda3 ().
/dev/sda3       202464016 -17526616 219990632    - /mnt/boot-sav/sda3

Mount /dev/sda1 on /mnt/boot-sav/sda6/boot/efi

===================== Reinstall the grub-efi of /dev/sda6 ======================

chroot /mnt/boot-sav/sda6 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
chroot /mnt/boot-sav/sda6 modprobe efivars

chroot /mnt/boot-sav/sda6 efibootmgr -v before grub install
EFI variables are not supported on this system.


chroot /mnt/boot-sav/sda6 uname -r
6.2.0-26-generic

chroot /mnt/boot-sav/sda6 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/sda6 efibootmgr -v after grub install
EFI variables are not supported on this system.

Warning: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/sda6 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Found linux image: /boot/vmlinuz-6.5.0-14-generic
Found initrd image: /boot/initrd.img-6.5.0-14-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi

Unhide GRUB boot menu in sda6/boot/grub/grub.cfg

Procedura di boot riparata.

Locked-NVram rilevato. Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    405495808 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt7)/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on sda6
OS#2:   Windows 10 or 11 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Haswell-ULT Integrated Graphics Controller from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: JBET73WW (1.37 )(1.37) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 000C
Timeout: 0 seconds
BootOrder: 000C,0013,0007,000D,0008,0009,000A,000B,0012
Boot0000  Setup	FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu	FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0002  Diagnostic Splash Screen	FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Lenovo Diagnostics	FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0004  Startup Interrupt Menu	FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0005  Rescue and Recovery	FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0006  MEBx Hot Key	FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0007* USB CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0008* USB FDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0009* ATA HDD0	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot000A* ATA HDD1	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot000B* ATA HDD2	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f602)
Boot000C* USB HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot000D* PCI LAN	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot000E* IDER BOOT CDROM	PciRoot(0x0)/Pci(0x16,0x2)/Ata(0,1,0)
Boot000F* IDER BOOT Floppy	PciRoot(0x0)/Pci(0x16,0x2)/Ata(0,0,0)
Boot0010* ATA HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0011* ATAPI CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0012* PCI LAN	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0013* Windows Boot Manager	HD(1,GPT,a2b908b3-9263-4b5f-a63a-bcd1afd8672f,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................

64349b3622c65f495a99dbf6102496e3   sda1/Boot/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   sda1/Boot/fbx64.efi
a660182adef313615746a665966d2ccc   sda1/Boot/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/ubuntu/shimx64.efi
05fd7027486c73232752c9faeb99fdfe   sda1/Microsoft/Boot/bootmgfw.efi
87fa2cd44bed8bf4925e0045932cf67e   sda1/Microsoft/Boot/bootmgr.efi
a7d2b5a20ff5098975ba4743f80faf26   sda1/Boot/LenovoBT.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda	: is-GPT,	no-BIOSboot,	hashidESP, 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda3	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda5	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda6	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB
sda4	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1	: hidenESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
sda3	: isnotESP,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda5	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
sda6	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda4	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

sda1	: not--sepboot,	no-kernel,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda3	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda5	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda6	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda4	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: EBB86AB5-E958-43A6-A6B9-3F64B3FB192E
         Start        End   Sectors   Size Type
sda1       2048     534527    532480   260M EFI System
sda2     534528     567295     32768    16M Microsoft reserved
sda3     567296  405495328 404928033 193.1G Microsoft basic data
sda4  405495808  405497855      2048     1M Linux filesystem
sda5  998166528 1000214527   2048000  1000M Windows recovery environment
sda6  405497856  998166527 592668672 282.6G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 14.65 GiB, 15728640000 bytes, 30720000 sectors
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0
       Start      End  Sectors  Size Type
sdb1       64  9828451  9828388  4.7G Microsoft basic data
sdb2  9828452  9838519    10068  4.9M EFI System
sdb3  9838520  9839119      600  300K Microsoft basic data
sdb4  9842688 30719936 20877249   10G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:512GB:scsi:512:512:gpt:ATA SanDisk SD7SB2Q5:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, hidden, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:208GB:207GB:ntfs:Basic data partition:msftdata;
4:208GB:208GB:1049kB:::;
6:208GB:511GB:303GB:ext4::;
5:511GB:512GB:1049MB:ntfs:Basic data partition:hidden, diag;
sdb:15.7GB:scsi:512:512:gpt:VendorCo ProductCode:;
1:32.8kB:5032MB:5032MB::ISO9660:hidden, msftdata;
2:5032MB:5037MB:5155kB::Appended2:boot, esp;
3:5037MB:5038MB:307kB::Gap1:hidden, msftdata;
4:5039MB:15.7GB:10.7GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1 vfat     725E-A443                            a2b908b3-9263-4b5f-a63a-bcd1afd8672f SYSTEM                   EFI system partition
&#9500;&#9472;sda2                                               8807fe93-9c01-4514-afea-e3c0edafa68d                          Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     CEA061E7A061D70D                     92c9015a-89c3-41c3-a8b1-f342e68577f2 Windows                  Basic data partition
&#9500;&#9472;sda4                                               d0109ed1-c018-4400-9cce-3bb85df76649                          
&#9500;&#9472;sda5 ntfs     589A62629A623C9E                     a7dc4b5a-0406-457c-b480-f6910dd26dc0 WinRE_DRV                Basic data partition
&#9492;&#9472;sda6 ext4     78be974f-641c-48ba-8ba3-1c7dc457956a d79cd234-ab42-4757-987c-62c453d0f1a2                          
sdb    iso9660  2023-08-08-01-19-05-00                                                    Ubuntu 22.04.3 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2023-08-08-01-19-05-00               f45e2fa1-c5a6-4d79-876e-c8245af921e0 Ubuntu 22.04.3 LTS amd64 ISO9660
&#9500;&#9472;sdb2 vfat     F7DB-4D56                            f45e2fa1-c5a6-4d79-876d-c8245af921e0 ESP                      Appended2
&#9500;&#9472;sdb3                                               f45e2fa1-c5a6-4d79-876c-c8245af921e0                          Gap1
&#9492;&#9472;sdb4 ext4     c335ff6f-8134-4691-9088-ee9b3f97bc6b 0084089a-3e01-7f4b-ae90-0b1f6c2f5a7e writable                 

Mount points (filtered): _______________________________________________________

                                                               Avail            Use% Mounted on
/dev/sda1                                                     220.6M             14% /mnt/boot-sav/sda1
/dev/sda3                                                     209.8G 36444489125821% /mnt/boot-sav/sda3
/dev/sda5                                                     411.7M             59% /mnt/boot-sav/sda5
/dev/sda6                                                     250.9G              4% /mnt/boot-sav/sda6
/dev/sdb1                                                          0            100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda6                                                     ext4            rw,relatime
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 78be974f-641c-48ba-8ba3-1c7dc457956a root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda6/boot/grub/grub.cfg (filtered) ======================

Ubuntu   78be974f-641c-48ba-8ba3-1c7dc457956a
Windows Boot Manager (on sda1)   osprober-efi-725E-A443
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda6/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=78be974f-641c-48ba-8ba3-1c7dc457956a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=725E-A443  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda6/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda6: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 344,041568756 = 369,411821568  boot/vmlinuz                                   1
 296,166141510 = 318,005972992  boot/vmlinuz-6.2.0-26-generic                  1
 344,041568756 = 369,411821568  boot/vmlinuz-6.5.0-14-generic                  1
 296,166141510 = 318,005972992  boot/vmlinuz.old                               1
 274,054161072 = 294,263414784  boot/initrd.img                                1
 273,763534546 = 293,951356928  boot/initrd.img-6.2.0-26-generic               1
 274,054161072 = 294,263414784  boot/initrd.img-6.5.0-14-generic               1
 273,763534546 = 293,951356928  boot/initrd.img.old                            1

===================== sda6: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom
I am available to carry out the BIOS settings or otherwise in order to obtain dual boot. 

Can you please help me make sure I have dual boot? 

Thanks in advance

---

### Post by tea for one on 2024-01-25
Line 52 - Warning: NVram is locked (Ubuntu not found in efibootmgr)

Can you access your UEFI settings and disable these options (if they are present):-
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
Lock UEFI BIOS Settings
Boot Order Lock 

Also, double check that your ESP is not flagged as hidden.
Gparted in a "Try Ubuntu" session will do this.

---

### Post by claudioroma on 2024-01-25
Thank you tea for one for your reply. 
I disabled:
 [B]TPM (Trusted Platform Module) 
Boot Order Lock[/B] 

the other options you indicated are not present. 

Regarding: **Lock UEFI BIOS Settings**** **what should I activate?**Both**.... or **Legacy First**?  

Thanks in advance for your reply

---

### Post by tea for one on 2024-01-25
You have Windows 10 and Ubuntu 22.04 in UEFI mode, therefore you do not need Legacy boot options.
Can you now boot into Ubuntu?

---

### Post by claudioroma on 2024-01-25
> **tea for one said:**
> You have Windows 10 and Ubuntu 22.04 in UEFI mode, therefore you do not need Legacy boot options.
Can you now boot into Ubuntu?

so for this:
**Lock UEFI BIOS Settings  **do I have to set UEFI mode? 

A thousand thanks !!

---

### Post by tea for one on 2024-01-25
I do not know exactly, because I do not have a PC with this UEFI setting.
Why not just try it - it can always be reversed.

---

### Post by claudioroma on 2024-01-26
Ok thanks, I'll try and let you know.
Thanks again.

---

### Post by claudioroma on 2024-01-26
**Tea for one **you're a legend it's gone!!!
Now I can work with Ubuntu 22.04
Thank you so much.

---

### Post by tea for one on 2024-01-26
That's good news.
To help other forum members/searchers, it's a nice gesture to mark the thread as solved:-
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

