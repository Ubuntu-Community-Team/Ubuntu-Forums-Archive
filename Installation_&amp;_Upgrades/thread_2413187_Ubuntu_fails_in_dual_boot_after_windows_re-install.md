---
title: "Ubuntu fails in dual boot after windows re-installation"
date: 2019-02-22
forum: Installation &amp; Upgrades
---

### Post by gipsyshadow on 2019-02-22
Hi, In my new PC I firstly managed a dual boot windows 10 pro - ubuntu 18.04.1lts dual boot with success. Yesterday I wanted to try a different win10 release (enterprise) and I installed it, then I tried to upgrade grub but I'm sure I messed up lots of things and now Ubuntu doesn't boot anymore.
In my MB's bios if I set boot order (1.win, 2.ubuntu) win starts as ubuntu was not present, I mean no grub display. If I set the boot order (1.ubuntu, 2.win) grub menu is displayed but there's no windows boot option, I mean only ubuntu, and if I select ubuntu I get black screen and led monitor gets yellow as if the PC was switched off. So I can run only ubuntu from live usb.
Here're some command outputs I guess could be useful to see the mess I've done:
```

ubuntu@ubuntu:~$ sudo fdisk -l
[...]
Device         Start        End    Sectors   Size Type
/dev/sda1       2048    1023999    1021952   499M Windows recovery environment
/dev/sda2    1024000    1228799     204800   100M EFI System
/dev/sda3    1228800    1261567      32768    16M Microsoft reserved
/dev/sda4  103561216  266242047  162680832  77.6G Microsoft basic data
/dev/sda5  266242048  286722047   20480000   9.8G Microsoft basic data
/dev/sda6  286722048 1953523711 1666801664 794.8G Microsoft basic data
/dev/sda7    1261568  103560396  102298829  48.8G Linux filesystem

Partition table entries are not in disk order.
[...]
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdc1       1701998450 3638285201 1936286752 923.3G  d unknown
/dev/sdc2       1701995885 2246105740  544109856 259.5G  a OS/2 Boot Manager
/dev/sdc3       1769087090 3538458322 1769371233 843.7G 6f unknown
/dev/sdc4       2885681152 2885734849      53698  26.2M  a OS/2 Boot Manager

Partition table entries are not in disk order.

```
```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD1003FZEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   629MB   105MB   fat32        EFI system partition          boot, esp
 3      629MB   646MB   16.8MB               Microsoft reserved partition  msftres
 7      646MB   53.0GB  52.4GB  ext4
 4      53.0GB  136GB   83.3GB  ntfs         Basic data partition          msftdata
 5      136GB   147GB   10.5GB  ext4                                       msftdata
 6      147GB   1000GB  853GB   ntfs                                       msftdata

```
```

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
label: gpt
label-id: 80053721-D476-46FF-BDF8-55738A46C5DA
device: /dev/sda
unit: sectors
first-lba: 34
last-lba: 1953525134

/dev/sda1 : start=        2048, size=     1021952, type=DE94BBA4-06D1-4D40-A16A-BFD50179D6AC, uuid=54980FB0-BAC4-4CE1-A798-59457D9ED9DC, name="Basic data partition", attrs="RequiredPartition"
/dev/sda2 : start=     1024000, size=      204800, type=C12A7328-F81F-11D2-BA4B-00A0C93EC93B, uuid=55A5E162-F205-4BAA-A392-B50D8540D604, name="EFI system partition"
/dev/sda3 : start=     1228800, size=       32768, type=E3C9E316-0B5C-4DB8-817D-F92DF00215AE, uuid=27F3ECB1-A3D7-4165-B101-04B86B764FA8, name="Microsoft reserved partition"
/dev/sda4 : start=   103561216, size=   162680832, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7, uuid=87152797-7668-4EBF-9530-82AAB43456FF, name="Basic data partition"
/dev/sda5 : start=   266242048, size=    20480000, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7, uuid=39E42FAA-A7CD-4E13-B2F4-A839480FE995
/dev/sda6 : start=   286722048, size=  1666801664, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7, uuid=69DC3608-16E8-496F-9743-E56ABAD0F423
/dev/sda7 : start=     1261568, size=   102298829, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=609DAA35-6C30-4BE0-974D-0E0C9B6DDEBE

```
I attach a gparted live screenshot too. Consider that sda7 (48.78G) is ROOT, sda5 (9.77G) is HOME and sda4 (77.57G) is win10. Also consider that it takes very few time to reinstall both OOSS with my hardware therefore I think we can consider this option too if it's the fastest one to solve the mess I made :)

---

### Post by yancek on 2019-02-22
> In my MB's bios if I set boot order (1.win, 2.ubuntu) win starts as ubuntu was not present, I mean no grub display

If you had a Legacy/MBR install, it would be possible by going through a multi-step convoluted process to boot a Linux system from the windows bootloader.  I'm not aware of any way this would work on an EFI install which is what you have so basically, that is expected behavior.  From windows you can only boot windows.

> If I set the boot order (1.ubuntu, 2.win) grub menu is displayed but there's no windows boot option, I mean only ubuntu

Before installing the new windows version, when you selected Ubuntu from the boot options, did you have a windows entry and did it boot or did you have to select each from the BIOS boot options?

I would expect that a new install of windows would set windows to first boot in the BIOS.  Try booting the Ubuntu usb and from a termnal, run the following commands consecutively and posting the output.  The first command will show the EFI entries of the system and you know what the second does, this is just to verify that sda2 is the EFI partition and then you can create a mount point with the mkdir command and mount the partition to look for your Ubuntu EFI files.

> sudo efibootmgr
sudo parted -l
sudo mkdir /mnt/sda2
sudo mount /dev/sda2 /mnt/sda2


Also, it would be useful if you could explain how you tried to update Grub.

---

### Post by oldfred on 2019-02-22
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by gipsyshadow on 2019-02-22
Thanks for help, I'll try to do my best answering to your questions because I'm not EN native language :)

First of all, these are the outputs yancek required, including the already posted "parted -l"
```

ubuntu@ubuntu:~$ sudo efibootmgr
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0001,0000
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0002* UEFI: ADATA USB Flash Drive 1100, Partition 1

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD1003FZEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   629MB   105MB   fat32        EFI system partition          boot, esp
 3      629MB   646MB   16.8MB               Microsoft reserved partition  msftres
 7      646MB   53.0GB  52.4GB  ext4
 4      53.0GB  136GB   83.3GB  ntfs         Basic data partition          msftdata
 5      136GB   147GB   10.5GB  ext4                                       msftdata
 6      147GB   1000GB  853GB   ntfs                                       msftdata


Model: ADATA USB Flash Drive (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  15.5GB  15.5GB  fat32        Microsoft Basic Data  msftdata


Model: SanDisk Cruzer (scsi)
Disk /dev/sdc: 4027MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  4027MB  4027MB  fat32


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: SanDisk Cruzer (scsi)                                              
Disk /dev/sr0: 101MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda2
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/sda2 

```
And [this](http://paste.ubuntu.com/p/dgmyKwGhb8/) is the link generated by BOOT repair after yancek's commands.
After that I opened gparted and I saw there was a key logo near to sda2 and the column mount point appeared with sda2 mounted. Anyway nothing's changed.

Now I try to explain what I did.
All was right after the 1^ dual boot installation, I mean I set boot orden within my MB's bios (1.ubuntu, 2.windows) as said by the guide I followed. At every system boot grub was displayed and I could choose between win and ubu.
I messed up win10 enterprise installation because I erased ubuntu root partition, I mean I got "not allocated space" where root was so I had to install ubuntu again (it takes less than 10') separating root and home as usual. Then booting issues started. I followed a guide to try to restore grub and gave these commands:
```
sudo -s
mount /dev/sda2 /mnt

```
I guess making a mistake but I just went on with
```

mount /dev/sda7 /mnt
mount /dev/sda2 /mnt/boot/efi
for i in dev dev/pts proc sys sys/firmware; do mount --bind /$i /mnt/$i; done
chroot /mnt
update-grub
grub-install

```
My last attempt was to install again win10 for 1^ and then ubuntu, this time not modifying partitions within win installation but nothing changed, then I started this thread :)

---

### Post by oldfred on 2019-02-22
Your grub menu in Boot-Repair's report shows a Windows entry.

Grub only actually boots working Windows, or Windows that is not hibernated, nor needs chkdsk. And Windows fast start up sets hibernation flag and with at least some Windows updates resets that flag. So if grub entry does not boot Windows that is the first thing to check. And then you can boot Windows from UEFI boot menu directly, not using grub.

Error on sda2 is standard. Parted/gparted does not like unformatted partitions, but the Microsoft Reserved partition must be unformatted. Actually gparted should not then show it as an error as it has a valid GUID as the Microsoft Reserved.

I might unplug sdc as its odd or incorrect partitioning may be confusing boot.

Black screen issues are normally related to video drivers.
What video card/chip do you have?
Did you install proprietary drivers before?

Have you tried nomodeset boot parameter?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by gipsyshadow on 2019-02-22
Thanks oldfred, I think "I" solved this problem, in the sense "you" solved it :)
Firstly I disabled win fast boot as you suggested and win boot option appeared in grub but if I tried to boot ubuntu I got black screen again but monitor led was blue (as regularly) and not yellow as before. I added nomodeset parameter to ubuntu boot line and it started regularly. Then I made a regular SW upgrade, I installed ukuu via ppa and upgraded kernel to 4.21.11. When the system restarted ubuntu booted regularly so I think the boot&graph issue is solved now. I just red this error during ubuntu shutdown "unable to write to iommu" but I don't think it deals with this issue, doesn't it?

Anyway tell me if it's the case to test the system and/or keep some outputs to ensure now it's all right. Afaik I gave
```

sudo lshw -C display

```
and I got "[...] configuration: driver=amdgpu latency=0[...]" so the proper amdgpu driver is now present again.

What about the disk order list? I mean is it a problem to have sda1,2,3,7,4,5,6 instead of the correct numbering 1-7?
When I messed up ubuntu deleting its root partition during win installation, I wanted to erase the "small" partitions (eg. sda1 500MB). Did that mean those partitions are "necessary" for system health? Could I erase some of them and merge their unallocated space to the other "necessary" partitions?

---

### Post by oldfred on 2019-02-22
Some partitions are essential and some optional.
Most of the optional ones are to reinstall Windows or a vendor image to reinstall entire hard drive to default as new configuration.
Once you have made backups, you probably do not need those. My Dell wanted both a Windows & Dell backup & process offered to then delete those partitions.

These are the required partitions for Windows.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Partition order does not matter. There are ways to reorder partitions, but that usually makes for bigger issues.

---

