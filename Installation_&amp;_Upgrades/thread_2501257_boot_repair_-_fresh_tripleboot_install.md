---
title: "boot repair - fresh tripleboot install"
date: 2024-09-29
forum: Installation &amp; Upgrades
---

### Post by david1104 on 2024-09-29
Lenovo T490s trying to triple boot Ubuntu, Kali, and Windows.  Installed in that order.  Boots only to Windows, after trying to repair GRUB2.
I guess I selected the wrong dropdown.  I am working with ubuntu, not lubuntu.


Boot successfully repaired.

Please write on a paper the following URL:
[https://paste.ubuntu.com/p/VRPgYBDYxr/](https://paste.ubuntu.com/p/VRPgYBDYxr/)


In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

Locked-NVram detected. (Ubuntu) Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Please do not forget to make your UEFI firmware boot on the Ubuntu 24.04 LTS entry (nvme0n1p5/efi/ubuntu/grubx64.efi file) !


```
boot-repair-4ppa2074                                              [20240929_1939]

============================= Boot Repair Summary ==============================






Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p2,
using the following options:  nvme0n1p5/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /mnt/boot-sav/nvme0n1p5/efi/Boot/bootx64.efi
mv /mnt/boot-sav/nvme0n1p5/efi/Boot/bkpbootx64.efi /mnt/boot-sav/nvme0n1p5/efi/Boot/bootx64.efi
Mount /dev/nvme0n1p5 on /mnt/boot-sav/nvme0n1p2/boot/efi

=================== Reinstall the grub-efi of /dev/nvme0n1p2 ===================

chroot /mnt/boot-sav/nvme0n1p2 grub-install --version
grub-install (GRUB) 2.12-1ubuntu7
modprobe: FATAL: Module efivars not found in directory /lib/modules/5.15.0-76-generic
chroot /mnt/boot-sav/nvme0n1p2 modprobe efivars

chroot /mnt/boot-sav/nvme0n1p2 efibootmgr -v before grub install
BootCurrent: 0021
Timeout: 2 seconds
BootOrder: 0000,001B,001C,001D,001E,001F,0020,0021,0022,0012,0011,0024,0023
Boot0000* Windows Boot Manager    HD(5,GPT,6dd3fc49-77d2-4a65-aaf5-fe85e1b94434,0xe1de000,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000000000100000010000000040000007fff0400
dp: 04 01 2a 00 05 00 00 00 00 e0 1d 0e 00 00 00 00 00 20 03 00 00 00 00 00 49 fc d3 6d d2 77 65 4a aa f5 fe 85 e1 b9 44 34 02 02 / 04 04 46 00 5c 00 45 00 46 00 49 00 5c 00 4d 00 69 00 63 00 72 00 6f 00 73 00 6f 00 66 00 74 00 5c 00 42 00 6f 00 6f 00 74 00 5c 00 62 00 6f 00 6f 00 74 00 6d 00 67 00 66 00 77 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
data: 57 49 4e 44 4f 57 53 00 01 00 00 00 88 00 00 00 78 00 00 00 42 00 43 00 44 00 4f 00 42 00 4a 00 45 00 43 00 54 00 3d 00 7b 00 39 00 64 00 65 00 61 00 38 00 36 00 32 00 63 00 2d 00 35 00 63 00 64 00 64 00 2d 00 34 00 65 00 37 00 30 00 2d 00 61 00 63 00 63 00 31 00 2d 00 66 00 33 00 32 00 62 00 33 00 34 00 34 00 64 00 34 00 37 00 39 00 35 00 7d 00 00 00 00 00 01 00 00 00 10 00 00 00 04 00 00 00 7f ff 04 00
Boot0010  ThinkShield secure wipe    FvFile(3593a0d5-bd52-43a0-808e-cbff5ece2477)
dp: 04 06 14 00 d5 a0 93 35 52 bd a0 43 80 8e cb ff 5e ce 24 77 / 7f ff 04 00
Boot0011* LENOVO CLOUD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri(https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b ad 38 cc bb f7 ed f0 4d 95 9c f4 2a a7 4d 36 50 / 03 18 3b 00 68 74 74 70 73 3a 2f 2f 64 6f 77 6e 6c 6f 61 64 2e 6c 65 6e 6f 76 6f 2e 63 6f 6d 2f 70 63 63 62 62 73 2f 63 64 65 70 6c 6f 79 2f 65 66 69 2f 62 6f 6f 74 2e 65 66 69 / 7f ff 04 00
Boot0012* HTTPS BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri()
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b ad 38 cc bb f7 ed f0 4d 95 9c f4 2a a7 4d 36 50 / 03 18 04 00 / 7f ff 04 00
Boot0013  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
dp: 04 06 14 00 66 8b 1c 72 6c 42 86 4e 8e 99 34 57 c4 6a b0 b9 / 7f ff 04 00
Boot0014  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
dp: 04 06 14 00 2d 76 6a 12 58 57 ca 4f 85 31 20 1a 7f 57 f8 50 / 7f ff 04 00
Boot0015  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
dp: 04 06 14 00 a6 d9 d8 a7 b0 6a eb 4a ad 9d 16 3e 59 a7 a3 80 / 7f ff 04 00
Boot0016  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
dp: 04 06 14 00 5b 61 7e 3f 45 0d 80 4f 88 dc 26 b2 34 95 85 60 / 7f ff 04 00
Boot0017  Regulatory Information    FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
dp: 04 06 14 00 a0 92 8c 47 22 26 b7 42 a6 5d 58 94 16 9e 4d 24 / 7f ff 04 00
Boot0018  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
dp: 04 06 14 00 f4 e6 6e f4 85 47 a3 43 92 3d 7f 78 6c 3c 84 79 / 7f ff 04 00
Boot0019  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
dp: 04 06 14 00 60 3f 5d 66 3e ad ad 4c 8e 26 db 46 ee e9 f1 b5 / 7f ff 04 00
Boot001A  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
dp: 04 06 14 00 6a d5 6f ac 41 3d fd 4e a1 b9 87 02 93 81 1a 28 / 7f ff 04 00
Boot001B* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 86 70 12 96 aa 5a 78 48 b6 6c d4 9d d3 ba 6a 55 / 7f ff 04 00
Boot001C* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 6f f0 15 a2 88 30 b5 43 a8 b8 64 10 09 46 1e 49 / 7f ff 04 00
Boot001D* NVMe0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 00 1c 19 99 32 d9 4c 4e ae 9a a0 b6 e9 8e b8 a4 00 / 7f ff 04 00
Boot001E* NVMe1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a401)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 00 1c 19 99 32 d9 4c 4e ae 9a a0 b6 e9 8e b8 a4 01 / 7f ff 04 00
Boot001F* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f602)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 91 af 62 59 56 44 9f 41 a7 b9 1f 4f 89 2a b0 f6 02 / 7f ff 04 00
Boot0020* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 91 af 62 59 56 44 9f 41 a7 b9 1f 4f 89 2a b0 f6 01 / 7f ff 04 00
Boot0021* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 33 e8 21 aa af 33 bc 47 89 bd 41 9f 88 c5 08 03 / 7f ff 04 00
Boot0022* PXE BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 78 a8 4a af 2b 2a fc 4e a7 9c f5 cc 8f 3d 38 03 / 7f ff 04 00
Boot0023  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b ae a2 09 0a df de 21 4e 8b 3a 5e 47 18 56 a3 54 06 / 7f ff 04 00
Boot0024  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 91 af 62 59 56 44 9f 41 a7 b9 1f 4f 89 2a b0 f6 06 / 7f ff 04 00
Boot0025* IDER BOOT CDROM    PciRoot(0x0)/Pci(0x14,0x0)/USB(11,1)
dp: 02 01 0c 00 d0 41 03 0a 00 00 00 00 / 01 01 06 00 00 14 / 03 05 06 00 0b 01 / 7f ff 04 00
Boot0026* IDER BOOT Floppy    PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)
dp: 02 01 0c 00 d0 41 03 0a 00 00 00 00 / 01 01 06 00 00 14 / 03 05 06 00 0b 00 / 7f ff 04 00
Boot0027* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 91 af 62 59 56 44 9f 41 a7 b9 1f 4f 89 2a b0 f6 / 7f ff 04 00
Boot0028* ATAPI CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b ae a2 09 0a df de 21 4e 8b 3a 5e 47 18 56 a3 54 / 7f ff 04 00

chroot /mnt/boot-sav/nvme0n1p2 uname -r
5.15.0-76-generic

chroot /mnt/boot-sav/nvme0n1p2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/nvme0n1p5
mv /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/nvme0n1p2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme0n1p2 efibootmgr -v after grub install
BootCurrent: 0021
Timeout: 2 seconds
BootOrder: 0000,001B,001C,001D,001E,001F,0020,0021,0022,0012,0011,0024,0023
Boot0000* Windows Boot Manager    HD(5,GPT,6dd3fc49-77d2-4a65-aaf5-fe85e1b94434,0xe1de000,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000000000100000010000000040000007fff0400
dp: 04 01 2a 00 05 00 00 00 00 e0 1d 0e 00 00 00 00 00 20 03 00 00 00 00 00 49 fc d3 6d d2 77 65 4a aa f5 fe 85 e1 b9 44 34 02 02 / 04 04 46 00 5c 00 45 00 46 00 49 00 5c 00 4d 00 69 00 63 00 72 00 6f 00 73 00 6f 00 66 00 74 00 5c 00 42 00 6f 00 6f 00 74 00 5c 00 62 00 6f 00 6f 00 74 00 6d 00 67 00 66 00 77 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
data: 57 49 4e 44 4f 57 53 00 01 00 00 00 88 00 00 00 78 00 00 00 42 00 43 00 44 00 4f 00 42 00 4a 00 45 00 43 00 54 00 3d 00 7b 00 39 00 64 00 65 00 61 00 38 00 36 00 32 00 63 00 2d 00 35 00 63 00 64 00 64 00 2d 00 34 00 65 00 37 00 30 00 2d 00 61 00 63 00 63 00 31 00 2d 00 66 00 33 00 32 00 62 00 33 00 34 00 34 00 64 00 34 00 37 00 39 00 35 00 7d 00 00 00 00 00 01 00 00 00 10 00 00 00 04 00 00 00 7f ff 04 00
Boot0010  ThinkShield secure wipe    FvFile(3593a0d5-bd52-43a0-808e-cbff5ece2477)
dp: 04 06 14 00 d5 a0 93 35 52 bd a0 43 80 8e cb ff 5e ce 24 77 / 7f ff 04 00
Boot0011* LENOVO CLOUD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri(https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b ad 38 cc bb f7 ed f0 4d 95 9c f4 2a a7 4d 36 50 / 03 18 3b 00 68 74 74 70 73 3a 2f 2f 64 6f 77 6e 6c 6f 61 64 2e 6c 65 6e 6f 76 6f 2e 63 6f 6d 2f 70 63 63 62 62 73 2f 63 64 65 70 6c 6f 79 2f 65 66 69 2f 62 6f 6f 74 2e 65 66 69 / 7f ff 04 00
Boot0012* HTTPS BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri()
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b ad 38 cc bb f7 ed f0 4d 95 9c f4 2a a7 4d 36 50 / 03 18 04 00 / 7f ff 04 00
Boot0013  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
dp: 04 06 14 00 66 8b 1c 72 6c 42 86 4e 8e 99 34 57 c4 6a b0 b9 / 7f ff 04 00
Boot0014  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
dp: 04 06 14 00 2d 76 6a 12 58 57 ca 4f 85 31 20 1a 7f 57 f8 50 / 7f ff 04 00
Boot0015  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
dp: 04 06 14 00 a6 d9 d8 a7 b0 6a eb 4a ad 9d 16 3e 59 a7 a3 80 / 7f ff 04 00
Boot0016  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
dp: 04 06 14 00 5b 61 7e 3f 45 0d 80 4f 88 dc 26 b2 34 95 85 60 / 7f ff 04 00
Boot0017  Regulatory Information    FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
dp: 04 06 14 00 a0 92 8c 47 22 26 b7 42 a6 5d 58 94 16 9e 4d 24 / 7f ff 04 00
Boot0018  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
dp: 04 06 14 00 f4 e6 6e f4 85 47 a3 43 92 3d 7f 78 6c 3c 84 79 / 7f ff 04 00
Boot0019  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
dp: 04 06 14 00 60 3f 5d 66 3e ad ad 4c 8e 26 db 46 ee e9 f1 b5 / 7f ff 04 00
Boot001A  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
dp: 04 06 14 00 6a d5 6f ac 41 3d fd 4e a1 b9 87 02 93 81 1a 28 / 7f ff 04 00
Boot001B* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 86 70 12 96 aa 5a 78 48 b6 6c d4 9d d3 ba 6a 55 / 7f ff 04 00
Boot001C* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 6f f0 15 a2 88 30 b5 43 a8 b8 64 10 09 46 1e 49 / 7f ff 04 00
Boot001D* NVMe0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 00 1c 19 99 32 d9 4c 4e ae 9a a0 b6 e9 8e b8 a4 00 / 7f ff 04 00
Boot001E* NVMe1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a401)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 00 1c 19 99 32 d9 4c 4e ae 9a a0 b6 e9 8e b8 a4 01 / 7f ff 04 00
Boot001F* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f602)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 91 af 62 59 56 44 9f 41 a7 b9 1f 4f 89 2a b0 f6 02 / 7f ff 04 00
Boot0020* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 91 af 62 59 56 44 9f 41 a7 b9 1f 4f 89 2a b0 f6 01 / 7f ff 04 00
Boot0021* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 33 e8 21 aa af 33 bc 47 89 bd 41 9f 88 c5 08 03 / 7f ff 04 00
Boot0022* PXE BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 78 a8 4a af 2b 2a fc 4e a7 9c f5 cc 8f 3d 38 03 / 7f ff 04 00
Boot0023  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b ae a2 09 0a df de 21 4e 8b 3a 5e 47 18 56 a3 54 06 / 7f ff 04 00
Boot0024  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
dp: 03 0a 25 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 91 af 62 59 56 44 9f 41 a7 b9 1f 4f 89 2a b0 f6 06 / 7f ff 04 00
Boot0025* IDER BOOT CDROM    PciRoot(0x0)/Pci(0x14,0x0)/USB(11,1)
dp: 02 01 0c 00 d0 41 03 0a 00 00 00 00 / 01 01 06 00 00 14 / 03 05 06 00 0b 01 / 7f ff 04 00
Boot0026* IDER BOOT Floppy    PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)
dp: 02 01 0c 00 d0 41 03 0a 00 00 00 00 / 01 01 06 00 00 14 / 03 05 06 00 0b 00 / 7f ff 04 00
Boot0027* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 91 af 62 59 56 44 9f 41 a7 b9 1f 4f 89 2a b0 f6 / 7f ff 04 00
Boot0028* ATAPI CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b ae a2 09 0a df de 21 4e 8b 3a 5e 47 18 56 a3 54 / 7f ff 04 00
Warning: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/nvme0n1p2 update-grub
Sourcing file `/etc/default/grub'
Found linux image: /boot/vmlinuz-6.8.0-31-generic
Found initrd image: /boot/initrd.img-6.8.0-31-generic
Found Kali GNU/Linux Rolling on /dev/nvme0n1p3
Found Windows Boot Manager on /dev/nvme0n1p5@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...

Unhide GRUB boot menu in nvme0n1p2/boot/grub/grub.cfg

Boot successfully repaired.

Locked-NVram detected. (Ubuntu) Please report this message to boot.repair@gmail.com
Please do not forget to make your UEFI firmware boot on the Ubuntu 24.04 LTS entry (nvme0n1p5/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => Grub2 (v2.00) is installed in the MBR of /dev/nvme0n1 and looks at sector 
    2048 of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sda.

nvme0n1p1: _____________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme0n1p3: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Kali GNU/Linux Rolling
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

nvme0n1p4: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvme0n1p5: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/SecureBootRecovery.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

nvme0n1p6: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p7: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme0n1p8: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 32792 of /dev/sda1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /efi/boot/grubx64.efi 
                       /efi/boot/mmx64.efi /ldlinux.sys


================================ 3 OS detected =================================

OS#1:   Ubuntu 24.04 LTS on nvme0n1p2
OS#2:   Kali GNU/Linux Rolling on nvme0n1p3
OS#3:   Windows 10 or 11 on nvme0n1p7

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: WhiskeyLake-U GT2 [UHD Graphics 620] from Intel Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: N2JETA5W (1.83 )(1.83) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0021
Timeout: 2 seconds
BootOrder: 0000,001B,001C,001D,001E,001F,0020,0021,0022,0012,0011,0024,0023
Boot0000* Windows Boot Manager    HD(5,GPT,6dd3fc49-77d2-4a65-aaf5-fe85e1b94434,0xe1de000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0010  ThinkShield secure wipe    FvFile(3593a0d5-bd52-43a0-808e-cbff5ece2477)
Boot0011* LENOVO CLOUD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri(https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi)
Boot0012* HTTPS BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri()
Boot0013  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0014  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0015  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0016  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0017  Regulatory Information    FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
Boot0018  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0019  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot001A  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot001B* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot001C* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot001D* NVMe0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001E* NVMe1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a401)
Boot001F* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f602)
Boot0020* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot0021* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot0022* PXE BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0023  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot0024  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0025* IDER BOOT CDROM    PciRoot(0x0)/Pci(0x14,0x0)/USB(11,1)
Boot0026* IDER BOOT Floppy    PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)
Boot0027* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0028* ATAPI CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)

66f69798ad23240e43b7ba0044a914c4   nvme0n1p5/Boot/bkpbootx64.efi
66f69798ad23240e43b7ba0044a914c4   nvme0n1p5/Boot/bootx64.efi
66f69798ad23240e43b7ba0044a914c4   nvme0n1p5/ubuntu/grubx64.efi
13bbe79f47b4d57f791e51f5c01f7ac8   nvme0n1p5/Microsoft/Boot/SecureBootRecovery.efi
62c7a02cbd58c7b7a54f2e776a1880a7   nvme0n1p5/Microsoft/Boot/bootmgfw.efi
a04c74d166128825fc1c64afed71aaac   nvme0n1p5/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    hasBIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p2    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    not-far
nvme0n1p3    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
nvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p7    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p8    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme0n1p2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p5    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p7    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p8    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p7    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p8    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 576491C4-5E77-45EF-B2B1-B963C4DC9112
             Start       End   Sectors  Size Type
nvme0n1p1      2048      4095      2048    1M BIOS boot
nvme0n1p2      4096 104028159 104024064 49.6G Linux filesystem
nvme0n1p3 104028160 221214719 117186560 55.9G Linux filesystem
nvme0n1p4 221214720 236838911  15624192  7.5G Linux swap
nvme0n1p5 236838912 237043711    204800  100M EFI System
nvme0n1p6 237043712 237076479     32768   16M Microsoft reserved
nvme0n1p7 237076480 399606244 162529765 77.5G Microsoft basic data
nvme0n1p8 399607808 400676863   1069056  522M Windows recovery environment
Disk sda: 7.5 GiB, 8053063680 bytes, 15728640 sectors
Disk identifier: 0x0020954f
     Boot Start      End  Sectors  Size Id Type
sda1  *     2048 15728607 15726560  7.5G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:8053MB:scsi:512:512:msdos:VendorCo ProductCode:;
1:1049kB:8053MB:8052MB:fat32::boot, lba;
nvme0n1:256GB:nvme:512:512:gpt:INTEL SSDPEKKF256G8L:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:53.3GB:53.3GB:ext4::;
3:53.3GB:113GB:60.0GB:ext4:kali:;
4:113GB:121GB:8000MB:linux-swap(v1)::swap;
5:121GB:121GB:105MB:fat32:EFI system partition:boot, esp;
6:121GB:121GB:16.8MB::Microsoft reserved partition:msftres;
7:121GB:205GB:83.2GB:ntfs:Basic data partition:msftdata;
8:205GB:205GB:547MB:ntfs::hidden, diag;

Free space >10MiB: ______________________________________________________________

nvme0n1: 195643MiB:244198MiB:48555MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9492;&#9472;sda1      vfat     FE33-AB62                            0020954f-01                          BOOT-REPAIR 
nvme0n1                                                                                                    
&#9500;&#9472;nvme0n1p1                                               c89c8181-24c5-4cca-86c1-b1c416029313             
&#9500;&#9472;nvme0n1p2 ext4     ab9eb91f-1874-457a-b17f-58523aba3fde a7497853-d0d0-4ef9-9657-8a3a1a9faabd             
&#9500;&#9472;nvme0n1p3 ext4     86f08960-ede7-45a0-bb5e-7219fd13cca6 c67d7d6b-5533-4e16-a6d8-4100c9a02b08             kali
&#9500;&#9472;nvme0n1p4 swap     36f39e1f-55b9-43ec-a605-eaf0d08c550d e8a00968-b978-4f98-9fba-4d6afc635382             
&#9500;&#9472;nvme0n1p5 vfat     4E23-0E74                            6dd3fc49-77d2-4a65-aaf5-fe85e1b94434             EFI system partition
&#9500;&#9472;nvme0n1p6                                               9bb7ea4b-a5fc-4bed-b244-9bdcea53997f             Microsoft reserved partition
&#9500;&#9472;nvme0n1p7 ntfs     B81C294F1C2909C8                     c8171eba-5f4f-4fe2-aba6-20a767fe0c5e             Basic data partition
&#9492;&#9472;nvme0n1p8 ntfs     9CC84A7FC84A57A2                     e273f44b-d7c5-46ff-bea9-666f146b1bcb             

Mount points (filtered): _______________________________________________________

               Avail Use% Mounted on
/dev/nvme0n1p2 36.3G  19% /mnt/boot-sav/nvme0n1p2
/dev/nvme0n1p3 39.1G  23% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p5 63.1M  34% /mnt/boot-sav/nvme0n1p5
/dev/nvme0n1p7 36.2G  53% /mnt/boot-sav/nvme0n1p7
/dev/nvme0n1p8 88.2M  83% /mnt/boot-sav/nvme0n1p8
/dev/sda1         5G  33% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p2 ext4            rw,relatime
/dev/nvme0n1p3 ext4            rw,relatime
/dev/nvme0n1p5 vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p7 fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p8 fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda1      vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

=================== nvme0n1p2/boot/grub/grub.cfg (filtered) ====================

Ubuntu   ab9eb91f-1874-457a-b17f-58523aba3fde
Kali GNU/Linux Rolling (on nvme0n1p3)   86f08960-ede7-45a0-bb5e-7219fd13cca6
Windows Boot Manager (on nvme0n1p5)   osprober-efi-4E23-0E74
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p2/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during curtin installation
/dev/disk/by-uuid/ab9eb91f-1874-457a-b17f-58523aba3fde / ext4 defaults 0 1
/swap.img    none    swap    sw    0    0
UUID=4E23-0E74  /boot/efi       vfat    defaults      0       1

==================== nvme0n1p2/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
   5.222549438 = 5.607669760    boot/vmlinuz                                   1
   5.222549438 = 5.607669760    boot/vmlinuz-6.8.0-31-generic                  1
   5.222549438 = 5.607669760    boot/vmlinuz.old                               1
   6.965053558 = 7.478669312    boot/initrd.img                                1
   6.965053558 = 7.478669312    boot/initrd.img-6.8.0-31-generic               1
   6.965053558 = 7.478669312    boot/initrd.img.old                            1

=================== nvme0n1p2: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 10:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  4 10:12 40_custom
-rwxr-xr-x 1 root root   215 Apr  4 10:12 41_custom

=================== nvme0n1p3/boot/grub/grub.cfg (filtered) ====================

Kali GNU/Linux   86f08960-ede7-45a0-bb5e-7219fd13cca6
Ubuntu 24.04 LTS (24.04) (on nvme0n1p2)   ab9eb91f-1874-457a-b17f-58523aba3fde
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p3/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=86f08960-ede7-45a0-bb5e-7219fd13cca6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/nvme0n1p4 during installation
UUID=36f39e1f-55b9-43ec-a605-eaf0d08c550d none            swap    sw              0       0

==================== nvme0n1p3/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p3: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
  77.741218567 = 83.473997824   boot/grub/grub.cfg                             1
  77.743247986 = 83.476176896   boot/grub/i386-pc/core.img                     1
  79.433471680 = 85.291040768   boot/vmlinuz-6.6.15-amd64                      1
  79.433471680 = 85.291040768   vmlinuz                                        1
  79.433471680 = 85.291040768   vmlinuz.old                                    1
 102.154289246 = 109.687332864  boot/initrd.img-6.6.15-amd64                   1
 102.154289246 = 109.687332864  initrd.img                                     1
 102.154289246 = 109.687332864  initrd.img.old                                 1

=================== nvme0n1p3: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 13940 May 18 16:52 10_linux
-rwxr-xr-x 1 root root 14513 May 18 16:52 20_linux_xen
-rwxr-xr-x 1 root root   786 May 18 16:52 25_bli
-rwxr-xr-x 1 root root 13183 May 18 16:52 30_os-prober
-rwxr-xr-x 1 root root  1174 May 18 16:52 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 18 16:52 40_custom
-rwxr-xr-x 1 root root   215 May 18 16:52 41_custom

=================== nvme0n1p5/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid ab9eb91f-1874-457a-b17f-58523aba3fde root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Start Boot-Repair-Disk 64-bit
Start Boot-Repair-Disk 64-bit (compatibility mode)
UEFI Firmware Settings
Test memory

========================= sda1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sda1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1
*******.us ko ()
```

---

### Post by yancek on 2024-09-29
You have an EFI install of windows on the same drive on which you have Legacy installs of both Ubuntu and Kali.  With that setup, you can either boot windows EFI or you can change to Legacy and boot Ubuntu and Kali and NOT windows because you made the wrong selection during install.  You should have booted both Ubuntu and Kali in EFI mode and installed both EFI.  Since they are new installs, that would be the simplest solution so take care to select UEFI on booting the install media.

---

### Post by ubfan1 on 2024-09-29
The ISO boots both ways (legacy, and UEFI), but some tools for making the install media will allow you select one way -- don't select "legacy" if you do that, select UEFI. If you create the install media to boot both ways, it's the machine's settings that determine how it boots and installs.

---

### Post by david1104 on 2024-09-29
@yancek and @ubfan1
Thank you both.

I recreated my bootable USBs in Rufus as UEFI only.  They reinstalled over the already-existing partitions without an issue.  I have my triple boot working, with Kali's bootloader (the last install) now being default.  Thanks.

[marked as solved]

---

### Post by hudsoncrawford on 2024-10-08
You&#8217;re dealing with a tricky boot issue on your Lenovo T490s after installing Ubuntu, Kali, and Windows. Since you successfully repaired GRUB2, ensure your UEFI firmware is set to boot from the Ubuntu 24.04 LTS entry (nvme0n1p5/efi/ubuntu/grubx64.efi). If problems persist, refer to the URL you provided and contact [email]boot.repair@gmail.com[/email] for further assistance. Good luck! I was really impressed with [oxessays.com/write-my-essay]("https://oxessays.com/write-my-essay") I had a difficult essay due, and their writer handled it perfectly. The paper was well-structured and insightful, and it really helped me out of a tough spot. The customer support team was also very responsive, making the entire process easy. I&#8217;ll be recommending this service to my friends!

---

