---
title: "Grub doesn't find Windows 7"
date: 2016-04-18
forum: Installation &amp; Upgrades
---

### Post by krishkat on 2016-04-18
Grub doesn't find Windows 7, I have already tried update-grub but it doesnt help.
Here is my System:
janis@Milchstrasse-Linux:~$ sudo parted -l
Modell: ATA Samsung SSD 850 (scsi)
Festplatte  /dev/sda:  250GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
Disk-Flags: 


Nummer  Anfang  Ende   Größe  Typ      Dateisystem  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   250GB  250GB  primary  ntfs                                ///here is Windows 7 installed




Modell: ATA WDC WD10EZEX-00B (scsi)
Festplatte  /dev/sdb:  1000GB
Sektorgröße (logisch/physisch): 512B/4096B
Partitionstabelle: msdos
Disk-Flags: 


Nummer  Anfang  Ende    Größe  Typ      Dateisystem  Flags
 1      1049kB  500GB   500GB  primary  ntfs
 2      500GB   1000GB  500GB  primary  ntfs




Modell: ATA WDC WD10EZEX-00W (scsi)
Festplatte  /dev/sdc:  1000GB
Sektorgröße (logisch/physisch): 512B/4096B
Partitionstabelle: gpt
Disk-Flags: 


Nummer  Anfang  Ende    Größe   Dateisystem     Name  Flags
 1      1049kB  5000MB  4999MB  ext4                  bios_grub
 2      5000MB  105GB   100GB   linux-swap(v1)
 3      105GB   113GB   8096MB  fat32                 boot, esp
 4      113GB   1000GB  887GB   ext4




Modell:  USB DISK 3.0 (scsi)
Festplatte  /dev/sdd:  31,6GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
Disk-Flags: 


Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      4129kB  31,6GB  31,6GB  primary  fat32        LBA

I would be very happy about fast help.

I am new here and from German

---

### Post by oldfred on 2016-04-18
If Windows is on MBR partitioned drive, it has to be installed in BIOS boot mode.

Ubuntu on gpt partitioned drive can be either UEFI boot or BIOS boot, but you show an ESP - efi system partition for UEFI boot, and a bios_grub partition which is required on gpt for BIOS boot. But we cannot tell which way you currently are booting.
If Ubuntu is BIOS:
sudo update-grub

You then must have newer hardware that is UEFI.
But UEFI & 35 year old BIOS/MBR are not really compatible. Once you start booting in one mode you cannot switch to other mode without rebooting and grub does not do that.
You can only the dual boot from UEFI boot menu or one time boot key like f10 or f12, check manual.

You can convert Ubuntu easily to BIOS boot by adding a 1 or 2 MB unformatted partition with gparted and adding bios_grub flag. Then run Boot-Repair's advanced mode to uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI). Then from grub you should be able to dual boot.

You could only easily convert Windows with a total new install as it has to have gpt partitioning for UEFI boot.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by krishkat on 2016-04-23
After some new Installations of Ubuntu 15.10 and running boot-repair serval times. Windows is still not shown in the grub2 menu. But Boot-repair shows that i am having windows. What can i do know?

Here is the log of my last boot-repair sesion: [http://pastebin.com/27b2cetk](http://pastebin.com/27b2cetk)

---

### Post by oldfred on 2016-04-23
You have to convert Ubuntu from UEFI to BIOS to dual boot. (or reinstall Windows in UEFI mode).

Add a 1 or 2MB unformatted partition anywhere on sdc with gparted and add the bios_grub flag.
Then use Boot-Repair's advanced mode to un-install/reinstall grub. You want it to uninstall the UEFI version grub-efi-amd64 and install grub-pc for BIOS boot. 
Do not run any auto fix in Boot-Repair.

---

### Post by ptn107 on 2016-04-23
Make sure the package os-prober is installed before running update-grub.

---

### Post by krishkat on 2016-04-23
@ptn107
os-prober is installed

@oldfred
I did boot repair how you told it, but it didn't help
here is the log:
[http://paste.ubuntu.com/16004910/](http://paste.ubuntu.com/16004910/)

---

### Post by oldfred on 2016-04-23
Did you boot into Ubuntu on sdc and run this?
sudo update-grub

If not adding Windows then is it hibernated or needing chkdsk?

---

### Post by krishkat on 2016-04-23
sudo update-grub didn't help
and chkdsk says everything is fine

---

### Post by oldfred on 2016-04-23
Are you booting in BIOS/CSM/Legacy & have turned off UEFI, so you do not boot Ubuntu in UEFI mode?

If in UEFI mode it will not add Windows that is a BIOS boot mode install.

---

### Post by LostFarmer on 2016-04-23
see several problems and how to fix ?   from pastebin:
> sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub4Dos: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd  sda1 is the partition that contains the needed bootmgr and /bcd but the boot sector boot code is wrong , it is not the normal NTFS but that of Grub4dos. Looking at the 'hexdump -n512 -C /dev/sda1' also agrees it is not the MS Windows boot code.  Likely why grub menu is not listing it.

---

### Post by krishkat on 2016-04-23
I know installed ubuntu in BIOS "or how the other is called" mode.
Grub2 is know showing Windows 7 and I can boot from it.
BUT my Bios doesn't find the Ubunut partition. But I can manually boot from it.
My current parition Set-UP: [https://pastebin.com/Pj99yPXg](https://pastebin.com/Pj99yPXg)

---

### Post by oldfred on 2016-04-23
UEFI & BIOS are two ways to boot.
BIOS is the 35 year old way that computers have used. 
UEFI is the new way and also has CSM:
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

With BIOS you specify a drive to boot from and boot loader is in the MBR.
With UEFI you boot a description that is from the ESP - efi system partition. All boot files are in the ESP.

More details on UEFI in links in the link in my signature. But you have your system configured for BIOS boot.

---

### Post by krishkat on 2016-04-23
Thanks for that answer.
But how can I "help" the BIOS to detect my Linux partition
I am using a Asus H-170 Pro

---

### Post by oldfred on 2016-04-23
In BIOS mode you cannot boot a partition, just a drive that has the MBR.
Your UEFI/BIOS should give you the option to boot drive sdc, but with UEFI emulating BIOS it may be called just about anything. Every UEFI is different.

---

### Post by krishkat on 2016-04-24
Now I re-installed Windows 7 and Ubuntu in UEFI mode and everything is working fine.
Now I can install all windows updates. Woho!

---

