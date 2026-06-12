---
title: "Lenovo IdeaPad 1 14IGL05 - System Reset warning after Installation"
date: 2023-01-20
forum: Installation &amp; Upgrades
---

### Post by walledgardenxd on 2023-01-20
Hiya ubuntuers,

i'm trying to install ubuntu on my Lenovo IdeaPad 1 14IGL05. I've tried it multiple times but during start i'm receiving the System Reset warning in the top left of the screen without any further information and a boot loop. Tho, i can still access the BIOS with F2.

Do you have any ideas on how to resolve this issue? Would be greatly appreciated!

This is the Boot Repair log

boot-repair-4ppa203                                              [COLOR=#666666][[/COLOR]20230121_0025[COLOR=#666666]][/COLOR]

[COLOR=#666666]=============================[/COLOR] Boot Repair [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]==============================[/COLOR]






Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p2,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file


Mount nvme0n1p1 on /mnt/boot-sav/nvme0n1p2/boot/efi

Unhide GRUB boot menu in nvme0n1p2/etc/default/grub

[COLOR=#666666]=====================[/COLOR] Reinstall the grub-efi of [COLOR=#B8860B]nvme0n1p2[/COLOR] [COLOR=#666666]======================[/COLOR]

chroot /mnt/boot-sav/nvme0n1p2 grub-install --version
grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] [COLOR=#666666]2[/COLOR].06-2ubuntu7
chroot /mnt/boot-sav/nvme0n1p2 modprobe efivars

chroot /mnt/boot-sav/nvme0n1p2 efibootmgr -v before grub install
BootCurrent: [COLOR=#666666]0015[/COLOR]
Timeout: [COLOR=#666666]0[/COLOR] seconds
BootOrder: [COLOR=#666666]0015[/COLOR],0001,0013,0000,0014,0016,0017,0018
Boot0000* Windows Boot Manager	HD[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR],GPT,4bdee7ac-476b-4c24-87fe-1a60cb4b05af,0x800,0x100000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR]EFIMicrosoftBootbootmgfw.efi[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]...3................
Boot0001* ubuntu	HD[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR],GPT,4bdee7ac-476b-4c24-87fe-1a60cb4b05af,0x800,0x100000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR]EFIubuntushimx64.efi[COLOR=#666666])[/COLOR]
Boot0010  Setup	FvFile[COLOR=#666666]([/COLOR]721c8b66-426c-4e86-8e99-3457c46ab0b9[COLOR=#666666])[/COLOR]
Boot0011  Boot Menu	FvFile[COLOR=#666666]([/COLOR][COLOR=#666666]86488440[/COLOR]-41bb-42c7-93ac-450fbf7766bf[COLOR=#666666])[/COLOR]
Boot0012  Diagnostic Splash	FvFile[COLOR=#666666]([/COLOR]a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380[COLOR=#666666])[/COLOR]
Boot0013* NVMe: MTFDHBA256TCK-1AS1AABHA                	PciRoot[COLOR=#666666]([/COLOR]0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x13,0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x0,0x0[COLOR=#666666])[/COLOR]/NVMe[COLOR=#666666]([/COLOR]0x1,00-A0-75-01-27-76-2F-4E[COLOR=#666666])[/COLOR]....2.LN........
Boot0014* eMMC Card:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,63a04a38d7705b4888c69653c982e114[COLOR=#666666])[/COLOR]
Boot0015* USB HDD: TOSHIBA TransMemory	PciRoot[COLOR=#666666]([/COLOR]0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x15,0x0[COLOR=#666666])[/COLOR]/USB[COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR],0[COLOR=#666666])[/COLOR][COLOR=#666666]3[/COLOR].!..3.G..A.....
Boot0016* USB FDD:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49[COLOR=#666666])[/COLOR]
Boot0017* USB CD:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55[COLOR=#666666])[/COLOR]
Boot0018* USB LAN:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322[COLOR=#666666])[/COLOR]

chroot /mnt/boot-sav/nvme0n1p2 uname -r
[COLOR=#666666]5[/COLOR].15.0-43-generic

chroot /mnt/boot-sav/nvme0n1p2 grub-install --efi-directory[COLOR=#666666]=[/COLOR]/boot/efi --target[COLOR=#666666]=[/COLOR]x86_64-efi
Installing [COLOR=#AA22FF]**for**[/COLOR] x86_64-efi platform.
grub-install: warning: EFI variables cannot be [COLOR=#AA22FF]set[/COLOR] on this system.
grub-install: warning: You will have to [COLOR=#AA22FF]complete[/COLOR] the GRUB setup manually.
Installation finished. No error reported.
df /dev/nvme0n1p1
mv /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/nvme0n1p2 grub-install --efi-directory[COLOR=#666666]=[/COLOR]/boot/efi --target[COLOR=#666666]=[/COLOR]x86_64-efi
Installing [COLOR=#AA22FF]**for**[/COLOR] x86_64-efi platform.
grub-install: warning: EFI variables cannot be [COLOR=#AA22FF]set[/COLOR] on this system.
grub-install: warning: You will have to [COLOR=#AA22FF]complete[/COLOR] the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme0n1p2 efibootmgr -v after grub install
BootCurrent: [COLOR=#666666]0015[/COLOR]
Timeout: [COLOR=#666666]0[/COLOR] seconds
BootOrder: [COLOR=#666666]0015[/COLOR],0001,0013,0000,0014,0016,0017,0018
Boot0000* Windows Boot Manager	HD[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR],GPT,4bdee7ac-476b-4c24-87fe-1a60cb4b05af,0x800,0x100000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR]EFIMicrosoftBootbootmgfw.efi[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]...3................
Boot0001* ubuntu	HD[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR],GPT,4bdee7ac-476b-4c24-87fe-1a60cb4b05af,0x800,0x100000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR]EFIubuntushimx64.efi[COLOR=#666666])[/COLOR]
Boot0010  Setup	FvFile[COLOR=#666666]([/COLOR]721c8b66-426c-4e86-8e99-3457c46ab0b9[COLOR=#666666])[/COLOR]
Boot0011  Boot Menu	FvFile[COLOR=#666666]([/COLOR][COLOR=#666666]86488440[/COLOR]-41bb-42c7-93ac-450fbf7766bf[COLOR=#666666])[/COLOR]
Boot0012  Diagnostic Splash	FvFile[COLOR=#666666]([/COLOR]a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380[COLOR=#666666])[/COLOR]
Boot0013* NVMe: MTFDHBA256TCK-1AS1AABHA                	PciRoot[COLOR=#666666]([/COLOR]0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x13,0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x0,0x0[COLOR=#666666])[/COLOR]/NVMe[COLOR=#666666]([/COLOR]0x1,00-A0-75-01-27-76-2F-4E[COLOR=#666666])[/COLOR]....2.LN........
Boot0014* eMMC Card:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,63a04a38d7705b4888c69653c982e114[COLOR=#666666])[/COLOR]
Boot0015* USB HDD: TOSHIBA TransMemory	PciRoot[COLOR=#666666]([/COLOR]0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x15,0x0[COLOR=#666666])[/COLOR]/USB[COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR],0[COLOR=#666666])[/COLOR][COLOR=#666666]3[/COLOR].!..3.G..A.....
Boot0016* USB FDD:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49[COLOR=#666666])[/COLOR]
Boot0017* USB CD:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55[COLOR=#666666])[/COLOR]
Boot0018* USB LAN:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322[COLOR=#666666])[/COLOR]
Warning: NVram was not modified.

chroot /mnt/boot-sav/nvme0n1p2 update-grub
Sourcing file [COLOR=#BB4444]`[/COLOR]/etc/default/grub[COLOR=#BB4444]'[/COLOR]
[COLOR=#BB4444]Sourcing file `/etc/default/grub.d/init-select.cfg'[/COLOR]
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-43-generic
Found initrd image: /boot/initrd.img-5.15.0-43-generic
Memtest86+ needs a [COLOR=#666666]16[/COLOR]-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.

Unhide GRUB boot menu in nvme0n1p2/boot/grub/grub.cfg

Bootsektor wurde erfolgreich repariert.

Sie können Ihren Rechner nun neu starten.
Please [COLOR=#AA22FF]**do**[/COLOR] not forget to make your UEFI firmware boot on the Ubuntu [COLOR=#666666]22[/COLOR].04.1 LTS entry [COLOR=#666666]([/COLOR]nvme0n1p1/efi/ubuntu/grubx64.efi file[COLOR=#666666])[/COLOR] !


[COLOR=#666666]============================[/COLOR] Boot Info After [COLOR=#B8860B]Repair[/COLOR] [COLOR=#666666]============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu [COLOR=#666666]22[/COLOR].04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 [COLOR=#666666]([/COLOR]v1.99-2.00[COLOR=#666666])[/COLOR]
    Boot sector info:  Grub2 [COLOR=#666666]([/COLOR]v1.99-2.00[COLOR=#666666])[/COLOR] is installed in the boot sector of 
                       sda and looks at sector [COLOR=#666666]0[/COLOR] of the same hard drive [COLOR=#AA22FF]**for**[/COLOR] 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda ist bereits eingehängt oder wird gerade benutzt.


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]1[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]

OS#1:   Ubuntu [COLOR=#666666]22[/COLOR].04.1 LTS on [COLOR=#B8860B]nvme0n1p2[/COLOR]

[COLOR=#666666]================================[/COLOR] Host/Hardware [COLOR=#666666]=================================[/COLOR]

CPU architecture: [COLOR=#666666]64[/COLOR]-bit
Video: GeminiLake [COLOR=#666666][[/COLOR]UHD Graphics [COLOR=#666666]600[/COLOR][COLOR=#666666]][/COLOR] from Intel Corporation
Live-session OS is Ubuntu [COLOR=#666666]64[/COLOR]-bit [COLOR=#666666]([/COLOR]Ubuntu [COLOR=#666666]22[/COLOR].04.1 LTS, jammy, x86_64[COLOR=#666666])[/COLOR]

[COLOR=#666666]=====================================[/COLOR] [COLOR=#B8860B]UEFI[/COLOR] [COLOR=#666666]=====================================[/COLOR]

BIOS/UEFI firmware: DWCN25WW[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR].25[COLOR=#666666])[/COLOR] from LENOVO
The firmware is EFI-compatible, and is [COLOR=#AA22FF]set[/COLOR] in EFI-mode [COLOR=#AA22FF]**for**[/COLOR] this live-session.
SecureBoot disabled [COLOR=#666666]([/COLOR]confirmed by mokutil[COLOR=#666666])[/COLOR].
BootCurrent: [COLOR=#666666]0015[/COLOR]
Timeout: [COLOR=#666666]0[/COLOR] seconds
BootOrder: [COLOR=#666666]0015[/COLOR],0001,0013,0000,0014,0016,0017,0018
Boot0000* Windows Boot Manager	HD[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR],GPT,4bdee7ac-476b-4c24-87fe-1a60cb4b05af,0x800,0x100000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR][COLOR=#BB6622]**\E**[/COLOR]FI[COLOR=#BB6622]**\M**[/COLOR]icrosoft[COLOR=#BB6622]**\B**[/COLOR]oot[COLOR=#BB6622]**\b**[/COLOR]ootmgfw.efi[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]...3................
Boot0001* ubuntu	HD[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR],GPT,4bdee7ac-476b-4c24-87fe-1a60cb4b05af,0x800,0x100000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR][COLOR=#BB6622]**\E**[/COLOR]FI[COLOR=#BB6622]**\u**[/COLOR]buntu[COLOR=#BB6622]**\s**[/COLOR]himx64.efi[COLOR=#666666])[/COLOR]
Boot0010  Setup	FvFile[COLOR=#666666]([/COLOR]721c8b66-426c-4e86-8e99-3457c46ab0b9[COLOR=#666666])[/COLOR]
Boot0011  Boot Menu	FvFile[COLOR=#666666]([/COLOR][COLOR=#666666]86488440[/COLOR]-41bb-42c7-93ac-450fbf7766bf[COLOR=#666666])[/COLOR]
Boot0012  Diagnostic Splash	FvFile[COLOR=#666666]([/COLOR]a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380[COLOR=#666666])[/COLOR]
Boot0013* NVMe: MTFDHBA256TCK-1AS1AABHA                	PciRoot[COLOR=#666666]([/COLOR]0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x13,0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x0,0x0[COLOR=#666666])[/COLOR]/NVMe[COLOR=#666666]([/COLOR]0x1,00-A0-75-01-27-76-2F-4E[COLOR=#666666])[/COLOR]....2.LN........
Boot0014* eMMC Card:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,63a04a38d7705b4888c69653c982e114[COLOR=#666666])[/COLOR]
Boot0015* USB HDD: TOSHIBA TransMemory	PciRoot[COLOR=#666666]([/COLOR]0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x15,0x0[COLOR=#666666])[/COLOR]/USB[COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR],0[COLOR=#666666])[/COLOR][COLOR=#666666]3[/COLOR].!..3.G..A.....
Boot0016* USB FDD:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49[COLOR=#666666])[/COLOR]
Boot0017* USB CD:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55[COLOR=#666666])[/COLOR]
Boot0018* USB LAN:	VenMsg[COLOR=#666666]([/COLOR]bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322[COLOR=#666666])[/COLOR]

728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/BOOT/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/BOOT/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   nvme0n1p1/BOOT/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme0n1p1/BOOT/mmx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   nvme0n1p1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme0n1p1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/ubuntu/shimx64.efi

[COLOR=#666666]=============================[/COLOR] Drive/Partition [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]=============================[/COLOR]

Disks info: ____________________________________________________________________

nvme0n1	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	[COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p1	: no-os,	[COLOR=#666666]64[/COLOR], nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme0n1p2	: is-os,	[COLOR=#666666]64[/COLOR], apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p2	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p2	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	nvme0n1

fdisk -l [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ___________________________________________________________

Disk nvme0n1: [COLOR=#666666]238[/COLOR].47 GiB, [COLOR=#666666]256060514304[/COLOR] bytes, [COLOR=#666666]500118192[/COLOR] sectors
Disk identifier: 66F2149A-A45C-486C-915F-48F4ACDEEF5E
            Start       End   Sectors  Size Type
nvme0n1p1    [COLOR=#666666]2048[/COLOR]   [COLOR=#666666]1050623[/COLOR]   [COLOR=#666666]1048576[/COLOR]  512M EFI System
nvme0n1p2 [COLOR=#666666]1050624[/COLOR] [COLOR=#666666]500117503[/COLOR] [COLOR=#666666]499066880[/COLOR]  238G Linux filesystem
Disk sda: [COLOR=#666666]29[/COLOR].08 GiB, [COLOR=#666666]31229607936[/COLOR] bytes, [COLOR=#666666]60995328[/COLOR] sectors
Disk identifier: 9240A165-D190-4AB6-8A10-46DC207B42EE
        Start      End  Sectors  Size Type
sda1       [COLOR=#666666]64[/COLOR]  [COLOR=#666666]7465119[/COLOR]  [COLOR=#666666]7465056[/COLOR]  [COLOR=#666666]3[/COLOR].6G Microsoft basic data
sda2  [COLOR=#666666]7465120[/COLOR]  [COLOR=#666666]7473615[/COLOR]     [COLOR=#666666]8496[/COLOR]  [COLOR=#666666]4[/COLOR].1M EFI System
sda3  [COLOR=#666666]7473616[/COLOR]  [COLOR=#666666]7474215[/COLOR]      [COLOR=#666666]600[/COLOR]  300K Microsoft basic data
sda4  [COLOR=#666666]7475200[/COLOR] [COLOR=#666666]60995264[/COLOR] [COLOR=#666666]53520065[/COLOR] [COLOR=#666666]25[/COLOR].5G Linux filesystem

parted -lm [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________

sda:31.2GB:scsi:512:512:gpt:TOSHIBA TransMemory:;
[COLOR=#666666]1[/COLOR]:32.8kB:3822MB:3822MB::ISO9660:hidden, msftdata;
[COLOR=#666666]2[/COLOR]:3822MB:3826MB:4350kB::Appended2:boot, esp;
[COLOR=#666666]3[/COLOR]:3826MB:3827MB:307kB::Gap1:hidden, msftdata;
[COLOR=#666666]4[/COLOR]:3827MB:31.2GB:27.4GB:ext4::;
nvme0n1:256GB:nvme:512:512:gpt:MTFDHBA256TCK-1AS1AABHA:;
[COLOR=#666666]1[/COLOR]:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
[COLOR=#666666]2[/COLOR]:538MB:256GB:256GB:ext4::;

blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda         iso9660  [COLOR=#666666]2022[/COLOR]-08-10-16-21-45-00                                                    Ubuntu [COLOR=#666666]22[/COLOR].04.1 LTS amd64 
&#9500;&#9472;sda1      iso9660  [COLOR=#666666]2022[/COLOR]-08-10-16-21-45-00               9240a165-d190-4ab6-8a11-46dc207b42ee Ubuntu [COLOR=#666666]22[/COLOR].04.1 LTS amd64 ISO9660
&#9500;&#9472;sda2      vfat     8D6C-A9F8                            9240a165-d190-4ab6-8a12-46dc207b42ee ESP                      Appended2
&#9500;&#9472;sda3                                                    9240a165-d190-4ab6-8a13-46dc207b42ee                          Gap1
&#9492;&#9472;sda4      ext4     4a65d1e2-983a-4e95-b442-2576f657ff40 0534548e-89bf-a642-929c-d219fd50ab90 writable                 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 vfat     8F6E-A87D                            4bdee7ac-476b-4c24-87fe-1a60cb4b05af                          EFI System Partition
&#9492;&#9472;nvme0n1p2 ext4     85d565be-a54f-4ee0-9c74-54b4ea98b575 f0407afd-da75-4d48-a0f2-a6b79cd8d180                          

Mount points [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[COLOR=#666666][[/COLOR]/install-logs-2023-01-21.1/crash[COLOR=#666666]][/COLOR]  [COLOR=#666666]23[/COLOR].7G   [COLOR=#666666]0[/COLOR]% /var/crash
/dev/disk/by-label/writable[COLOR=#666666][[/COLOR]/install-logs-2023-01-21.1/log[COLOR=#666666]][/COLOR]    [COLOR=#666666]23[/COLOR].7G   [COLOR=#666666]0[/COLOR]% /var/log
/dev/nvme0n1p1                                                [COLOR=#666666]504[/COLOR].8M   [COLOR=#666666]1[/COLOR]% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2                                                [COLOR=#666666]210[/COLOR].9G   [COLOR=#666666]4[/COLOR]% /mnt/boot-sav/nvme0n1p2
/dev/sda1                                                          [COLOR=#666666]0[/COLOR] [COLOR=#666666]100[/COLOR]% /cdrom

Mount options [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: [COLOR=#B8860B]______________________________________________________[/COLOR]


[COLOR=#666666]===================[/COLOR] nvme0n1p1/efi/ubuntu/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]===================[/COLOR]

search.fs_uuid 85d565be-a54f-4ee0-9c74-54b4ea98b575 root 
[COLOR=#AA22FF]set[/COLOR] [COLOR=#B8860B]prefix[/COLOR][COLOR=#666666]=([/COLOR][COLOR=#B8860B]$root[/COLOR][COLOR=#666666])[/COLOR][COLOR=#BB4444]'/boot/grub'[/COLOR]
configfile [COLOR=#B8860B]$prefix[/COLOR]/grub.cfg

[COLOR=#666666]===================[/COLOR] nvme0n1p2/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]====================[/COLOR]

Ubuntu   85d565be-a54f-4ee0-9c74-54b4ea98b575
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].15.0-43-generic   85d565be-a54f-4ee0-9c74-54b4ea98b575
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#666666]========================[/COLOR] nvme0n1p2/etc/fstab [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]========================[/COLOR]

[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/nvme0n1p2 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]85d565be-a54f-4ee0-9c74-54b4ea98b575 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro [COLOR=#666666]0[/COLOR]       [COLOR=#666666]1[/COLOR]
[COLOR=#008800]*# /boot/efi was on /dev/nvme0n1p1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]8F6E-A87D  /boot/efi       vfat    [COLOR=#B8860B]umask[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]0077[/COLOR]      [COLOR=#666666]0[/COLOR]       [COLOR=#666666]1[/COLOR]
/swapfile                                 none            swap    sw              [COLOR=#666666]0[/COLOR]       [COLOR=#B8860B]0[/COLOR]

[COLOR=#666666]====================[/COLOR] nvme0n1p2/etc/default/grub [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]=====================[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT_STYLE[/COLOR][COLOR=#666666]=[/COLOR]menu
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]10[/COLOR]
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s [COLOR=#666666]2[/COLOR]> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo[/COLOR] Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]
[COLOR=#B8860B]GRUB_DISABLE_OS_PROBER[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]false[/COLOR]

[COLOR=#666666]=================[/COLOR] nvme0n1p2: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             boot/grub/grub.cfg                             [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]60[/COLOR],743160248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]65[/COLOR],222471680   boot/vmlinuz                                   [COLOR=#666666]2[/COLOR]
  [COLOR=#666666]60[/COLOR],743160248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]65[/COLOR],222471680   boot/vmlinuz-5.15.0-43-generic                 [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]180[/COLOR],750972748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]194[/COLOR],079879168  boot/initrd.img                                [COLOR=#666666]3[/COLOR]
 [COLOR=#666666]180[/COLOR],750972748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]194[/COLOR],079879168  boot/initrd.img-5.15.0-43-generic              [COLOR=#666666]3[/COLOR]
 [COLOR=#666666]180[/COLOR],750972748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]194[/COLOR],079879168  boot/initrd.img.old                            [COLOR=#B8860B]3[/COLOR]

[COLOR=#666666]===================[/COLOR] nvme0n1p2: ls -l /etc/grub.d/ [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]===================[/COLOR]

-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]18683[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 10_linux
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]43031[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 10_linux_zfs
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]14180[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 20_linux_xen
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]13369[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 30_os-prober
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root  [COLOR=#666666]1372[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 30_uefi-firmware
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]700[/COLOR] Feb [COLOR=#666666]19[/COLOR]  [COLOR=#666666]2022[/COLOR] 35_fwupd
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]214[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 40_custom [COLOR=#111111][FONT=monospace]-rwxr-xr-x [/FONT][/COLOR][COLOR=#666666][FONT=monospace]1[/FONT][/COLOR][COLOR=#111111][FONT=monospace] root root   [/FONT][/COLOR][COLOR=#666666][FONT=monospace]215[/FONT][/COLOR][COLOR=#111111][FONT=monospace] Apr [/FONT][/COLOR][COLOR=#666666][FONT=monospace]15[/FONT][/COLOR][COLOR=#111111][FONT=monospace]  [/FONT][/COLOR][COLOR=#666666][FONT=monospace]2022[/FONT][/COLOR][COLOR=#111111][FONT=monospace] 41_custom[/FONT][/COLOR]

---

### Post by tea for one on 2023-01-21
Can you access your UEFI settings and check (if applicable) some security settings:-

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast)
Disable Legacy mode
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

My guess is that you have Platform Trust Technology enabled.

---

