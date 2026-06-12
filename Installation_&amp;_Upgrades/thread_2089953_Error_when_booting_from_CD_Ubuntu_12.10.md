---
title: "Error when booting from CD Ubuntu 12.10"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by gqferreira on 2012-11-30
Goodnight everyone.

Lately I'm nervous to go with Ubuntu.
I used it as my only OS since version 8.04 until 11:10 when I started having problems every time I went to install it.
A year ago I'm on Windows because everything I try to install on my machine goes wrong, until the LTS version is unstable.

I downloaded Ubuntu 12.10 and now tried to boot.

1 - First problem:
"Secure Boot not enabled"

I tried a few things on the internet nothing intuitive, a few things here ... other there ... did not find anything that explained clearly. So I risked moving into BIOS and found a property called more or less "Quick Boot", I enabled.
I tried booting again and again the message appeared, but instead of freezing the system as before, allowed me to go to the Grub.

2 - Second problem:
I chose the option "Try without installing" and came another error like this: "Error on reading from cd'0 0x5b55 sector." He spends a few seconds and gives a "Kernel Panic"
I've done a CD and the md5 matches the hash informed on the Ubuntu website, the CD is intact.

I downloaded Ubuntu 12.10 x64.

My machine is a notebook CCE
i7-2630QM CPU @ 2.00 GHz
4 GB DDR3 1333
HM65 Express Chipset Family
HD 500GB Hitachi

bios-vendor: Phoenix Technologies Ltd.
bios-version: 2.07_
baseboard-manufacturer: Intel Corp.
baseboard-product-name: Emerald Lake

Thanks for listening,
Gustavo Ferreira

---

### Post by oldfred on 2012-11-30
Turn off quick boot as that almost always causes issues.

Is system configured for the new UEFI or older BIOS boot? Unless you have the new Windows 8, you should not have secure boot. Only the 64 bit version of 12.10 works with secure boot. If Windows is UEFI you have to boot Ubuntu in UEFI mode.

Post this to see if drive has efi partition as first partition for UEFI or not. Also if drive is gpt then Windows will only boot in UEFI mode.

       sudo parted /dev/sda unit s print

If you have sdb also run that.

---

### Post by gqferreira on 2012-11-30
Ok, I turned off quick boot.

I have Windows 7 and the Ubuntu 12.04 in may machine.
The result is it:

gustavo@gustavo-pc:~$ sudo parted /dev/sda unit s print
Modelo: ATA Hitachi HTS54505 (scsi)
Disco /dev/sda: 976773168s
Tamanho de setor (lógico / Físico): 512B/512B
Tabela de Partição: gpt

Número  Início      Fim         Tamanho     Sistema de arquivos  Nome                          Sinalizador
 1      2048s       206847s     204800s     fat32                EFI system partition          boot
 2      206848s     468991s     262144s                          Microsoft reserved partition  msftres
 3      468992s     204802047s  204333056s  ntfs                 Basic data partition
 4      204802048s  400114548s  195312501s  ext4
 5      400114549s  556364549s  156250001s  ext4
 6      556364550s  564177050s  7812501s    linux-swap(v1)
 7      564177051s  976772754s  412595704s  ext4

Thank for you attention.:P

---

### Post by oldfred on 2012-12-01
You have the new UEFI system as Windows is install in UEFI with gpt partitions.

You have to install the 64 bit version in UEFI mode. But even if you did not Boot-Repair will convert a 64 bit BIOS type install to UEFI by uninstalling grub-pc and installing grub-efi.
Grub also has a bug in creating a chain load entry for Windows. It still creates a BIOS version when with UEFI you need an efi version. Boot_Repair will also fix that.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

If all the fixes do not work post link to full BootInfo Report so we can  see all the details.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

 [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)
            UEFI Ubuntu installs in BIOS, Boot-Repair to fix - UEFI Windows 7
[http://ubuntuforums.org/showthread.php?t=2048457](http://ubuntuforums.org/showthread.php?t=2048457)
[http://ubuntuforums.org/showthread.php?t=2058453](http://ubuntuforums.org/showthread.php?t=2058453)

    UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

---

### Post by gqferreira on 2012-12-01
Thank you but my Windows is not EFI?

---

### Post by oldfred on 2012-12-01
First partition is FAT which usually is UEFI partition.
And with gpt partitioning Windows only boots in UEFI mode. Your partitioning is gpt.

---

### Post by rgrig on 2012-12-09
I have the same problem:
 - I have a Sony Vaio series S with Windows 7 installed
 - Windows uses EFI
 - I burned ubuntu-12.10-desktop-amd64.iso; the md5 is fine
 - trying to boot from the DVD causes error reading sector from cd0, and then kernel panic (as above)

I can get BootInfo as follows:
 - switch the laptop from UEFI to Legacy
 - now the CD boots, and I can install&run boot-repair
 - the report is at [http://paste.ubuntu.com/1421108/](http://paste.ubuntu.com/1421108/)

I want to dual-boot, so leaving the laptop in the legacy (non-UEFI) mode is not an option.

EDIT: Except, I just noticed that I get an error about sector 0x5b500 (not 0x5b55).

---

### Post by rgrig on 2012-12-09
The following worked for me:
1. Put laptop in legacy (non-UEFI) boot mode.
2. Install Ubuntu.  You must setup the partitions manually, because the installer does not recognize the Windows OS (because Windows uses EFI, and the installer only looks for legacy stuff).
3. Switch Ubuntu to EFI mode, as described here: 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The best hint you might need to go thru steps 1-3 above is probably the message "error reading from sector 0x5b500" while trying to boot the installation CD.

---

### Post by gqferreira on 2012-12-15
Thanks olfred for the help but I do not quite understand. I have just resolved as follows:
* - I enabled "Quick boot".
* - I created a bootable SD-Card and installed by him.

I have not had problems like this and I'm using Ubuntu now.

Thanks to all!:guitar:

---

