---
title: "Need help repairing my boot"
date: 2022-05-23
forum: Installation &amp; Upgrades
---

### Post by dalesd on 2022-05-23
I woke up this morning to the sound of a hard drive dying.  

It was a very old drive and fortunately all it was used for was grub. (Long story, but the computer had been upgraded many times over the years and I never figured out how to move grub to my new SSD, but it wasn't a problem because it worked, so I left it alone.)  

So I removed the dead drive and fired up a live USB drive with Ubuntu and ran Boot Repair.  
The results are here:  
[https://paste.ubuntu.com/p/YCWk2PQCdj/](https://paste.ubuntu.com/p/YCWk2PQCdj/)  

I expected Boot Repair to give me the option to reinstall GRUB on my SSD, but it only gives me the option to create a Bootinfo summary (see pasetbin link above)  
screenshot: [https://i.imgur.com/KSj6lVs.png](https://i.imgur.com/KSj6lVs.png)  
When I click the advanced options, GRUB location, GRUB options, and MBR options are all grayed out and blank.  

Anyway, what do I do from here so I can boot into Ubuntu again?  




```
boot-repair-4ppa200                                              [20220523_1006]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb: ___________________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdc and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdc: /dev/sdc already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Ubuntu 20.04.4 LTS on sda1

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GM107 [GeForce GTX 750 Ti] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: F4(4.6) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - SecureBoot disabled
Platform is in Setup Mode - Please report this message to boot.repair@gmail.com.
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001
Boot0001* UEFI: Samsung Flash Drive 1100	PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(2,GPT,9312da92-19cf-4be5-8057-8e26d983bc85,0x56d2e8,0x2130)AMBO


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1	: is-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda3	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios

Partitions info (2/3): _________________________________________________________

sda1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda3	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda3	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 1D4AB0CD-E0A6-4DA9-AA0B-B803A9BAE617
           Start        End    Sectors   Size Type
sda1        2048   39999487   39997440  19.1G EFI System
sda2  1921525760 1953523711   31997952  15.3G Linux swap
sda3    39999488 1921525759 1881526272 897.2G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 7.28 TiB, 8001563222016 bytes, 15628053168 sectors
Disk sdc: 119.51 GiB, 128320801792 bytes, 250626566 sectors
Disk identifier: 9312DA92-19CF-4BE5-8055-8E26D983BC85
        Start       End   Sectors   Size Type
sdc1       64   5690087   5690024   2.7G Microsoft basic data
sdc2  5690088   5698583      8496   4.1M EFI System
sdc3  5698584   5699183       600   300K Microsoft basic data
sdc4  5701632 250626502 244924871 116.8G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:512:gpt:ATA MKNSSDRE1TB:;
1:1049kB:20.5GB:20.5GB:ext4::boot, esp;
3:20.5GB:984GB:963GB:ext4::;
2:984GB:1000GB:16.4GB:linux-swap(v1)::swap;
sdb:8002GB:scsi:512:4096:loop:ATA ST8000VN004-2M21:;
1:0.00B:8002GB:8002GB:btrfs::;
sdc:128GB:scsi:512:512:gpt:Samsung Flash Drive:;
1:32.8kB:2913MB:2913MB::ISO9660:hidden, msftdata;
2:2913MB:2918MB:4350kB::Appended2:boot, esp;
3:2918MB:2918MB:307kB::Gap1:hidden, msftdata;
4:2919MB:128GB:125GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                       PARTLABEL
sda                                                                                                                   
&#9500;&#9472;sda1 ext4     9bbf45d7-7c4e-48ab-9e15-b906d2182cbc f3ea41a8-5493-4d28-b119-98d68b4fa7df                             
&#9500;&#9472;sda2 swap     9a1e0856-0250-4ec6-8c87-ff011958aca6 07668e3f-f5ac-4349-8473-a340d7737a60                             
&#9492;&#9472;sda3 ext4     19697fec-b7ea-4540-a00f-b73ba00ad0a7 d535c640-b833-4869-924c-5f4ce6e8258b                             
sdb    btrfs    11d9c072-3c74-4210-9d5b-7b6d7fd24a76                                      Seagate8T                   
sdc    iso9660  2022-04-19-10-21-39-00                                                    Ubuntu-MATE 22.04 LTS amd64 
&#9500;&#9472;sdc1 iso9660  2022-04-19-10-21-39-00               9312da92-19cf-4be5-8054-8e26d983bc85 Ubuntu-MATE 22.04 LTS amd64 ISO9660
&#9500;&#9472;sdc2 vfat     8D6C-A9F8                            9312da92-19cf-4be5-8057-8e26d983bc85 ESP                         Appended2
&#9500;&#9472;sdc3                                               9312da92-19cf-4be5-8056-8e26d983bc85                             Gap1
&#9492;&#9472;sdc4 ext4     c5b2c8e4-6a33-47ff-9bac-851b9bcacd7b 60382919-85b4-0141-9d2e-06c1a1aca6dd writable                    

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2022-05-23.0/crash] 108.5G   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2022-05-23.0/log]   108.5G   0% /var/log
/dev/sda1                                                       2.2G  83% /mnt/boot-sav/sda1
/dev/sda1                                                       2.2G  83% /mnt/boot-sav/sda1/boot/efi
/dev/sda3                                                     435.3G  46% /media/ubuntu-mate/19697fec-b7ea-4540-a00f-b73ba00ad0a7
/dev/sdb                                                        3.4T  53% /media/ubuntu-mate/Seagate8T
/dev/sdc1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/disk/by-label/writable[/install-logs-2022-05-23.0/crash] ext4            rw,relatime
/dev/disk/by-label/writable[/install-logs-2022-05-23.0/log]   ext4            rw,relatime
/dev/sda1                                                     ext4            rw,relatime
/dev/sda1                                                     ext4            rw,relatime
/dev/sda3                                                     ext4            rw,nosuid,nodev,relatime,errors=remount-ro
/dev/sdb                                                      btrfs           rw,nosuid,nodev,relatime,space_cache,subvolid=5,subvol=/
/dev/sdc1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Ubuntu   9bbf45d7-7c4e-48ab-9e15-b906d2182cbc
Ubuntu, with Linux 5.4.0-110-generic   9bbf45d7-7c4e-48ab-9e15-b906d2182cbc
Ubuntu, with Linux 5.4.0-109-generic   9bbf45d7-7c4e-48ab-9e15-b906d2182cbc
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda1/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=9bbf45d7-7c4e-48ab-9e15-b906d2182cbc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
# /home was on /dev/sdb3 during installation
UUID=19697fec-b7ea-4540-a00f-b73ba00ad0a7 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=9a1e0856-0250-4ec6-8c87-ff011958aca6 none            swap    sw              0       0
/dev/disk/by-uuid/07b337af-af04-4edf-a1f9-267f46ee4a00 /media/Toshiba8TB ext4 nosuid,nodev,nofail,x-gvfs-show 0 0
UUID=11d9c072-3c74-4210-9d5b-7b6d7fd24a76   /media/Seagate8T    btrfs   defaults,x-gvfs-show    0   2
UUID=9bbf45d7-7c4e-48ab-9e15-b906d2182cbc  /boot/efi       ext4    defaults      0       1

======================= sda1/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   4.581066132 = 4.918882304    boot/grub/grub.cfg                             1
  18.153942108 = 19.492646912   boot/grub/i386-pc/core.img                     1
  10.577102661 = 11.357077504   boot/vmlinuz                                  29
   7.728172302 = 8.298061824    boot/vmlinuz-5.4.0-109-generic                 7
  10.577102661 = 11.357077504   boot/vmlinuz-5.4.0-110-generic                29
   7.728172302 = 8.298061824    boot/vmlinuz.old                               7
  15.222652435 = 16.345198592   boot/initrd.img                               335
  19.064426422 = 20.470272000   boot/initrd.img-5.4.0-109-generic             146
  15.222652435 = 16.345198592   boot/initrd.img-5.4.0-110-generic             335
  19.064426422 = 20.470272000   boot/initrd.img.old                           146

===================== sda1: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18224 Jan 11 10:09 10_linux
-rwxr-xr-x 1 root root 42359 Aug 17  2020 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Apr 15  2020 20_linux_xen
-rwxr-xr-x 1 root root 12059 Mar  4  2018 30_os-prober
-rwxr-xr-x 1 root root  1424 Apr 15  2020 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 21  2017 40_custom
-rwxr-xr-x 1 root root   216 Jun 21  2017 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by oldfred on 2022-05-23
You have UEFI system.
It looks like you changed your ext4 sda1 partition to have an ESP flag.
The ESP flag must be on a FAT32 formatted partition for UEFI to be able to see it and for Boot-Repair to have a place to reinstall grub into.

You do not need that large of a swap partition.
And 19GB for / is not particularly large as snaps now consume a lot of space.

I might delete swap & combine it with / and add a 300 to 500MB FAT32 partition  as last part of old swap and with boot,esp flags using gparted.
If you create a new swap of 4GB by shrinking sda3, you have to update UUID in fstab with new UUID. If you reboot before updating swap you need to comment out current swap entry as deleted swap will not exist and boot may fail.

Then Boot-Repair should offer to reinstall grub, if live installer booted in UEFI boot mode.

---

### Post by dalesd on 2022-05-23
> **oldfred said:**
> You have UEFI system.
It looks like you changed your ext4 sda1 partition to have an ESP flag.
The ESP flag must be on a FAT32 formatted partition for UEFI to be able to see it and for Boot-Repair to have a place to reinstall grub into. 

You do not need that large of a swap partition.
And 19GB for / is not particularly large as snaps now consume a lot of space.

I might delete swap & combine it with / and add a 300 to 500MB FAT32 partition  as last part of old swap and with boot,esp flags using gparted.
If you create a new swap of 4GB by shrinking sda3, you have to update UUID in fstab with new UUID. If you reboot before updating swap you need to comment out current swap entry as deleted swap will not exist and boot may fail.



Thanks, Fred.  

Let me see if I understand.  
I need to use gparted to make a new FAT32 partition.  
Does that have to go in any particular location on the disk?   This [old help page]("https://help.ubuntu.com/community/BootPartition") says it has to be at the front of the disk, in the first 100GB, but it's also referencing Ubuntu 11.04, so perhaps it's out of date? 

Yes, 20GB is small for / (in my defense, this disk was partitioned before Snaps were a thing) and I would like to expand it.  

That's a good idea to use swap for this. I could easily get by with a lot smaller swap.  

I use gparted to make a new 500MP FAT32 partition. I do that by shrinking swap down to 4 GB and then put the remainder into /.  

> Then Boot-Repair should offer to reinstall grub, if live installer booted in UEFI boot mode.

Then I run Boot-Repair again and it will do its magic. 

I ran the command:  
```
test -d /sys/firmware/efi && echo efi || echo bios
``` 
and it returned ```
efi
``` so I think I'm good there.

---

### Post by oldfred on 2022-05-23
I think ESP has to be within the first 2TB.
Most systems have it first, or with Windows it may be second or third with just smaller partitions in front.
UEFI does suggest it be first, but moving / right has potential for issues, but can be done. Any interruption can totally corrupt data.

With any partition changes make sure you have good backups of all partitions.
I do not back up install as I consider that easy to reinstall. But have a few settings in /etc that I just manually copy into /home so backup of /home includes those. And list of installed apps to make it easy to totally reconfigure system.

---

### Post by dalesd on 2022-05-23
Good news, it's working again!  

I shrunk swap to 4GB and added a 1GB FAT32 partition, sda4  
Then I let boot-repair do its magic, yadda yadda yadda, and reboot and it's working.  

I didn't increase the size of /, because I need the system for tonight and I was worried that would take a long time.  
Am I correct in my understanding that if I want to increase the size of sda1 at the front of the disk with the ~11GB of unallocated space freed up from swap at the end of the disk, I do that by shifting the other partition(s) towards the back?  There wouldn't be some kind of trick to expand that sda1 partition into the unallocated space at the end of the disk, would there?

---

### Post by oldfred on 2022-05-23
I suggested deleting swap as that made the unallocated space next to /. And expanding right is almost instantaneous. 
Where moving or moving start of a partition can take a long time as all data is copied & any interruption totally destroys your data.
Since swap has no data, I think it can be quickly moved. And ESP is not large so it can be moved right easily if you did not put it at end or right of unallocated when viewed from gparted.
If you now have 10GB unallocated, and it is next to sda1, you should be able to quickly increase size of sda1.

---

