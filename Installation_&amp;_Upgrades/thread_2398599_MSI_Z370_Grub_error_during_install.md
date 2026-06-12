---
title: "MSI Z370 Grub error during install"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by troneleck on 2018-08-14
Hello,

i want to install Ubuntu 18.04.1 next to Windows 10 on different NVM drives but i got an install error from grub.

Boot = UEFI only
Secure Boot = off
Network = Working 
USB Stick starting as UEFI = true

I want install grub on the Ubuntu SSD and use the grub menu to boot Ubuntu or Windows.

The pictures showing the error, partitions i made and filtered syslog.

Can anyone help to make it run?

greets
Jones

---

### Post by jeremy31 on 2018-08-14
Install without networking enabled

---

### Post by oldfred on 2018-08-14
Ubuntu's UEFI grub only installs to ESP - efi system partition on first drive. Normally with SATA it is sda or hd0.
But with your NVMe drives, I have seen it correctly install to NVMe drive even when SATA drives are present.
Have not seen many with two NVMe drives and that may be issue.

First part of script does not fully parse NVMe drives. Boot-Repair uses bootinfosript, but author of that does not have an NVMe drive to test if script can correctly be updated.
       Support NVMe and MMC devices 
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues) 
    
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)  

    
Boot-Repairs advanced options may let you choose correct ESP and install grub using that.

---

### Post by troneleck on 2018-08-14
Still same problem. @ jeremy31

@oldfred: [http://paste.ubuntu.com/p/dF2xytPvbh/](http://paste.ubuntu.com/p/dF2xytPvbh/)

---

### Post by oldfred on 2018-08-14
I would first try using Boot-Repair's advanced mode and install grub to this drive's ESP. You choose drive & it should install. But it looks like it used the ESP on the Windows drive, not the ESP on the Ubuntu drive. If fully  on /dev/nvme1n1p2 change fstab to UUID to that partition UUID shown as:   B5DE-11B4              

# /boot/efi was on /dev/nvme0n1p2 during installation
UUID=0676-EABF  /boot/efi       vfat    umask=0077      0       1 
    
Or manually from live installer:
       sudo efibootmgr -c -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme1n1 -p 2 
See also for details of above command:
man efibootmgr

You have some drives as gpt and some as the now 35 year old MBR(msdos). Better to eventually migrate to gpt. I started in 2010 to convert to gpt as I knew eventually I would be using UEFI & gpt. 
      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by troneleck on 2018-08-14
Boot-Repair doesent boot right.
I get the language settings and after that i end up in a initfs shell.
Errormessage was something about cant mount /dev/loop0 (or something like that).

The drives are MBR becouse they are old drives (migrated from Win7 / Mint 14) all new become GPT.

I will give it now one more try with your "manually" option and then its time to sleep. (its 2 o´clock in the morning)

Edit:

Still the same.

After your command the BootOrder changed but still the same problem.

> 
root@ubuntu:/home/ubuntu# efibootmgr -c -L "ubuntu-18" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme1n1 -p 2

BootOrder: 0003,0002,0000,000E,000F,0011,0010,0001,0012

Boot0003* ubuntu-18


What happens if i use the Win drive for the boot loader? Do i loose the Win boot loader?
What happens if i dd the win drive to the ubuntu drive and try to install ubuntu on the (old / first NVM) win drive? ( This should show if it have to be the first drive for the bootloader or if it is a other problem)

How likely will it work if i plug one 60GB SSD to my Laptop, install Ubuntu, add it back into my desctop and dd it to the second NVM.(I dont want to remove the NVM becouse there is not much space to work)

thx for your help

greets 
Jones

---

### Post by oldfred on 2018-08-14
Did you use the now older Boot-Repair ISO or use your Ubuntu installer and the ppa to add Boot-Repair to installer? Older ISO usually not compatible with newer systems.

What brand/model system? What video card/chip?
Some need boot parameters or work arounds.

I typically do not like using dd, as any typo and you lose a drive.
I do not see why ESP on second NVMe drive will not work.

With the new entry from efibootmgr what does happen?
Since script does not correctly parse NVMe drive what is in its /EFI/ubuntu folder? And /EFI/Boot folder?
Post this to see details:
sudo efibootmgr -v
       lsblk -f -o +PARTUUID /dev/nvme1n1
lsblk -f -o +PARTUUID /dev/nvme0n1

Partuuid is the GUID of the partition. And it is used by UEFI to know which partition to load files from.
Partuuid must be the same as in the ESP boot entry.

We have filed bug reports for several years on Ubuntu's grub not installing to sdb or external drives. I believe they have a way now for external drives, but no way to specify any drive other than what grub sees as first drive. When I installed Fedora just to see how its grub works, it let me choose sdb and worked to boot from sdb. Or it is some change Ubuntu does.


Please add to this (among several) bugs on install drive. But yours is somewhat different since two NVMe drives. While not very common now, I expect it will be more common in future.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by troneleck on 2018-08-15
System is:

I7 8700K
MSI Tomahawk Z370
GTX 1070 TI
32 GiB RAM

2 * Kingston A1000 SSD 240GB (M.2 / PCIe x2)
2 * Old Crucial 60GB SSD
1* Old 500GB HDD
1* Old 1TB HDD
1* New 2TB

I moved Win10 from old 60GB SSD to Kingston SSD.


This is now a clean start:
NVM2 (Ubuntu)

> 

ubuntu@ubuntu:~$ lsblk -f -o +PARTUUID /dev/nvme1n1
NAME FSTYPE LABEL UUID                                 MOUNTPOINT PARTUUID
nvme1n1
&#9474;                                                                 
&#9500;&#9472;nvme1n1p1
&#9474;    ext4         069fc1eb-5fc9-4804-895e-bd3cdd206374            4bada5ee-68dd-4538-95ee-0299454ae829
&#9500;&#9472;nvme1n1p2
&#9474;    vfat         B5DE-11B4                                       5c6d517e-cca5-4073-8ead-d26a30cf5e59
&#9500;&#9472;nvme1n1p3
&#9474;    swap         c87f1ad5-df9e-4e47-b321-3583fe9bbad9            1a631447-141c-4e49-b880-7a1b8f8efcc4
&#9492;&#9472;nvme1n1p4
     ext4         3c76c893-3cd5-45c0-b014-94166aae5816            f8e8b188-89c8-446a-96b3-7b9824d076a8
ubuntu@ubuntu:~$ mount /dev/nvme1n1p2 /mnt
mount: only root can do that
ubuntu@ubuntu:~$ sudo !!
sudo mount /dev/nvme1n1p2 /mnt
ubuntu@ubuntu:~$ ls /mnt
EFI
ubuntu@ubuntu:~$ ls /mnt/EFI/
BOOT  ubuntu
ubuntu@ubuntu:~$ ls /mnt/EFI/BOOT/
BOOTX64.EFI  fbx64.efi
ubuntu@ubuntu:~$ ls /mnt/EFI/ubuntu/
BOOTX64.CSV  fw  fwupx64.efi  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi




Now it becomes a little bit strange.
Since i have installed Mint 14 on the USB stick, long time ago, i ended up with wrong Partition names but all is working normally.
There is no Mint 14 on this stick, he got formatted 100 times and still shows this.
This is the working Win NVM.


> 
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p2 /mnt
ubuntu@ubuntu:~$ ls /mnt/
EFI  boot-info  boot-repair
ubuntu@ubuntu:~$ ls /mnt/EFI/
Boot  Microsoft  ubuntu
ubuntu@ubuntu:~$ ls /mnt/boot-info/
log
ubuntu@ubuntu:~$ ls /mnt/boot-repair/
log
ubuntu@ubuntu:~$ lsblk -f -o +PARTUUID /dev/nvme0n1
NAME FSTYPE LABEL UUID                                 MOUNTPOINT PARTUUID
nvme0n1
&#9474;    iso966 Linux Mint 14 Cinnamon 32-bit
&#9474;                 2012-11-28-19-55-14-00                          
&#9500;&#9472;nvme0n1p1
&#9474;    ntfs   Wiederherstellung
&#9474;                 A6C26E74C26E489F                                f868969e-5716-4a8b-9297-96b1d51086d9
&#9500;&#9472;nvme0n1p2
&#9474;    vfat   Linux Mint 14 Cinnamon 32-bit
&#9474;                 0676-EABF                            /mnt       c90489e2-9467-48bd-bfe9-42b22c69e3ac
&#9500;&#9472;nvme0n1p3
&#9474;    iso966 Linux Mint 14 Cinnamon 32-bit
&#9474;                 2012-11-28-19-55-14-00                          9c076b71-d9e9-42d8-b647-9f65a3f0477b
&#9492;&#9472;nvme0n1p4
     ntfs   Linux Mint 14 Cinnamon 32-bit
                  C6C0A728C0A71E25                                515ba871-06bd-4c51-b9b5-f3d78b597ce5





The BootOrder is changing automatic after restart.
0003(Ubuntu) is now again behind 0000(Win10)


> 
root@ubuntu:/home/ubuntu# efibootmgr 
BootCurrent: 0013
Timeout: 1 seconds
BootOrder: 0000,0003,0011,0013,0012,0001,0014
Boot0000* Windows Boot Manager
Boot0001  Hard Drive
Boot0003* ubuntu-18
Boot0011* ubuntu
Boot0012* USB KEY
Boot0013* UEFI: Generic Flash Disk PMAP
Boot0014  UEFI: Generic Flash Disk PMAP, Partition 1





Boot-Repair doesn't (cant) remove grub.

> 
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/nvme1n1p4" dpkg --configure -a
Setting up grub-efi-amd64-signed (1.93.3+2.02-2ubuntu8.2) ...
Installing for x86_64-efi platform.
Skipping unreadable variable "Boot0001": Input/output error
Skipping unreadable variable "Boot0001": Input/output error
Skipping unreadable variable "Boot0001": Input/output error
Could not prepare Boot variable: Input/output error
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/nvme1n1p4" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.93.3+2.02-2ubuntu8.2) ...
Installing for x86_64-efi platform.
Skipping unreadable variable "Boot0001": Input/output error
Could not prepare Boot variable: Input/output error
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ 







I have removed now all partitions from NVM for Ubuntu and the normal Ubuntu SSD (was a try if it will work from there but same error)
Now i have:
 
nvme0n1 = Win10
nvme1n1= no partition
sda = 1TB Data
sdb = 2TB Data
sdc = 500GB Data
sde = 60GB SSD for Game installations
sdd = 60 GB SSD no partition

> 

ubuntu@ubuntu:~$ efibootmgr 
BootCurrent: 0013
Timeout: 1 seconds
BootOrder: 0000,0013,0012,0001,0014
Boot0000* Windows Boot Manager
Boot0001  Hard Drive
Boot0003  
Boot0011  
Boot0012* USB KEY
Boot0013* UEFI: Generic Flash Disk PMAP
Boot0014  UEFI: Generic Flash Disk PMAP, Partition 1
ubuntu@ubuntu:~$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0   1.8G  1 loop /rofs
loop1         7:1    0  86.9M  1 loop /snap/core/4917
loop2         7:2    0  34.7M  1 loop /snap/gtk-common-themes/319
loop3         7:3    0 140.9M  1 loop /snap/gnome-3-26-1604/70
loop4         7:4    0   2.3M  1 loop /snap/gnome-calculator/180
loop5         7:5    0    13M  1 loop /snap/gnome-characters/103
loop6         7:6    0  14.5M  1 loop /snap/gnome-logs/37
loop7         7:7    0   3.7M  1 loop /snap/gnome-system-monitor/51
sda           8:0    0 931.5G  0 disk 
&#9492;&#9472;sda1        8:1    0 931.5G  0 part /mnt/boot-sav/sda1
sdb           8:16   0   1.8T  0 disk 
&#9500;&#9472;sdb1        8:17   0    16M  0 part 
&#9492;&#9472;sdb2        8:18   0   1.8T  0 part /mnt/boot-sav/sdb2
sdc           8:32   0 465.8G  0 disk 
&#9492;&#9472;sdc1        8:33   0 465.8G  0 part /mnt/boot-sav/sdc1
sdd           8:48   0  59.6G  0 disk 
sde           8:64   0  59.6G  0 disk 
&#9492;&#9472;sde1        8:65   0  59.6G  0 part /mnt/boot-sav/sde1
sdf           8:80   1  14.7G  0 disk /cdrom
&#9500;&#9472;sdf1        8:81   1   1.8G  0 part 
&#9492;&#9472;sdf2        8:82   1   2.3M  0 part 
nvme1n1     259:0    0 223.6G  0 disk 
nvme0n1     259:1    0 223.6G  0 disk 
&#9500;&#9472;nvme0n1p1 259:6    0   499M  0 part /mnt/boot-sav/nvme0n1p1
&#9500;&#9472;nvme0n1p2 259:7    0   100M  0 part /mnt/boot-sav/nvme0n1p2
&#9500;&#9472;nvme0n1p3 259:8    0    16M  0 part 
&#9492;&#9472;nvme0n1p4 259:9    0   223G  0 part 
ubuntu@ubuntu:~$ 




---

### Post by oldfred on 2018-08-15
I would expect you need nomodeset to boot live installer & first boot after install or until you install the nVidia proprietary driver from Ubuntu repository.

Even if new motherboard, vendor may still have UEFI update available. You may need to install that. Note it will reset many UEFI setting changes you have made. I keep a list. And many SSD need firmware update.

       MSI X370 Gaming Plus used rEFInd
[URL="https://ubuntuforums.org/showthread.php?t=2378837"]https://ubuntuforums.org/showthread.php?t=2378837
[/URL]
 Alternative efi boot manager for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) 
But yours is not really an UEFI limited system.

Often issues are by vendor so those with an older version may have solutions to your new motherboard. Bigger difference if Intel or AMD. One user posted turning off fast boot in UEFI worked, not sure if then he changed other settings.

      
 MSI x299 SLI
[https://ubuntuforums.org/showthread.php?t=2371556](https://ubuntuforums.org/showthread.php?t=2371556)
MSI Z170M Intel i7 6700 GTX 980TI 16.10 does not work, 16.04 does
[https://ubuntuforums.org/showthread.php?t=2357641](https://ubuntuforums.org/showthread.php?t=2357641) 
    
My installs to sdb or full install to external drive, always overwrite my /EFI/ubuntu folder on sda's ESP. So I quickly learned to back that up. But I always have an ESP on every drive, required for external drives to reconfigure to be bootable on their own.

Some have said they can change boot order with UEFI, but using efibootmgr does not stay. Windows updates which it regularly does also will change boot order & turn Windows fast start up back on. Windows always wants to be first and have its default settings.

[URL="https://ubuntuforums.org/showthread.php?t=2378837"]
[/URL]

---

### Post by troneleck on 2018-08-15
OK, i'm on it.

SSD Firmware is the newest.
Bios was old and i made an update from 1.1 to 1.5.

First try now:

The emty NVM is set as 1st boot device.
Device is shown as nvme0n1 and Win10 as nvme1n1.


Partitions = Attachments

SUCCES.

It looks like the bios update solved THIS problem.
I get now the boot menu and was able to select ubuntu or Windows.

BUT Ubunut isent running right.
The mouse is laggy and i cant loggin.
I´m not able to open a shell with ctrl+alt+Fx.

Thank you very much olfred for your help to this point.

---

### Post by oldfred on 2018-08-15
Have you installed the latest nVidia proprietary driver?
Do not install directly from nVidia, but only from Ubuntu.
If you want very newest driver you have to add a ppa.
If you install incorrect driver or want to change, new driver will not uninstall old, so you have to totally purge first, then install new one.

       Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html) 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
   # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by troneleck on 2018-08-15
Your nomodeset gave me the option to login.
I update the system now and install grafix driver.

Edit:

I's ALIVE!!!

Without your help i will find myself stuck into Wintrojan from Spysoft.

Thank you very much.

(I try now to set this to solved)

---

### Post by oldfred on 2018-08-15
Glad you got it working. :)

---

