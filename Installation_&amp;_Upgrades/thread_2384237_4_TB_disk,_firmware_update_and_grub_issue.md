---
title: "4 TB disk, firmware update and grub issue"
date: 2018-02-04
forum: Installation &amp; Upgrades
---

### Post by mev on 2018-02-04
I have what I am guessing is likely a firmware issue with an older Gateway NE-522 laptop not being able to address all of a 4 GB disk. However, I narrowed it down a bit further and post this query to further understand what is going on and why the failure shows up:

Symptoms:
I have done a fresh install of Ubuntu 19.10 on an external 4 tb disk with the following partitioning:
   /dev/sda1 is ext2 filesystem mounted as /boot with size 1000 MiB
   /dev/sda4 is ext4 filesystem mounted as / with size 200 GiB

After the initial install completes, the system boots up properly and I have what appears to be a functioning system. However, once I do:
   apt-get update
   apt-get upgrade
and reboot, the system now fails just after I get to the grub prompt with the following message:

   error: attempt to read or write outside of disk 'hd0'.

   Press any key to continue...

If I press return at this prompt, then I get a kernel and backtrace with the following message:

   Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)

I have then narrowed this a bit further and found that this panic/change seems to be related to the update of one package:

   linux-firmware

which when it installs invokes update-initramfs and generates a new /boot/initrd.img-4.13.0-21-generic file. If I save the original file to a different name, then I can successfully boot again.

I have then taken these two initial initrd.img files and unpacked them to see what is different. The only difference seems to be in the files named /var/cache/ldconfig/aux-cache. Both the original and modified files are 3403 bytes long with different contents. I have done a strings on the file contents and see the same list of shared libraries, but in different order. There may also be different binary data in this file, but this is harder to figure out.

So after my long-winded diagnosis, my question is to further understand what is going on here and why the initial boot is successful but just updating the initramfs image causes things to go awry. I'm fairly certain my workaround is to use a smaller external disk or a different system that might better support this. However, I also figure if I can better understand the issue, then I might also find other workarounds (other than staying with an older working ramdisk...).

Any clues?

---

### Post by oldfred on 2018-02-04
Wow, already on 19.10. Must be time traveler from future. :)
typo 17.10?

Post this:
sudo parted -l

You must have gpt, not the 35 year old MBR configuration that only support drives up to 2TiB.
Also is drive in BIOS set for AHCI. Old IDE setting probably does not support large drives.

---

### Post by mev on 2018-02-04
Oops, I don't know yet if it will be an issue on 19.10, since I am actually using 17.10 :p

The output of parted -l is as follows:

Model: Seagate BUP BL (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: pmbr_boot

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1050MB  1049MB  ext2         boot1
 2      1050MB  2098MB  1049MB  ext4         boot2
 3      2098MB  3147MB  1049MB  ext4         boot3
 4      3147MB  218GB   215GB   ext4         system1
 5      218GB   433GB   215GB   ext4         system2
 6      433GB   647GB   215GB   ext4         system3
 7      647GB   4001GB  3353GB  ext4         work


Model: ATA ST2000LM003 HN-M (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1960GB  1960GB  primary   ext4            boot
 2      1960GB  2000GB  40.0GB  extended
 5      1960GB  2000GB  40.0GB  logical   linux-swap(v1)

The drive where I see the problems is /dev/sda, connected via the USB port. The internal drive on this laptop is /dev/sdb and otherwise works fine as a 2 tb drive.

The BIOS is set to AHCI.

I figured I might have difficulties with the reach of the drive and hence the small /boot partition early in the disk.However, the root partition is also within the first 2 tb on this drive as well. Somehow the installation initrd is successful, but generating a new one with update-initramfs seems to be changing the state somehow so it no longer works.

---

### Post by oldfred on 2018-02-04
I am not seeing a bios_grub for BIOS boot or an ESP - efi system partition for UEFI boot.
I normally suggest both as first two partitions on every new or reformatted gpt drive. Then you can now or in future configure to boot in BIOS mode or UEFI mode.

Grub2 does not install correctly unless you have a bios_grub partition. It may use blocklists which are considered unreliable as if any boot file changes location on drive, it will not work.
The bios_grub can be anywhere  on drive, but not sure about very large drives now.
Shrink any partition by 2 or 3 GB and make a 1 or 2GB unformatted partition with the bios_grub flag, if using gparted.
If using gdisk, the bios_grub is indicated with code ef02.

Not sure if that is only problem.

Generally with desktops, I do not recommend a separate /boot. Often leads to issues as users do not properly maintain, or they try to share when multiple booting. I keep all system folders inside / (root) and use 25 to 30GB for every root. But have a large /mnt/data partition mounted in every install so I have same data in every install.

---

### Post by mev on 2018-02-04
I tried creating both bios_grub and EFI partitions and now at least have different symptoms:

The revised disk partitions are as follows:
Model: Seagate BUP BL (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  3146kB  2097kB               BIOS-Boot  bios_grub
 2      3146kB  1052MB  1049MB  fat16        efi        msftdata
 3      1052MB  2100MB  1049MB  ext2         boot1
 4      2100MB  3149MB  1049MB  ext2         boot2
 5      3149MB  4197MB  1049MB  ext2         boot3
 6      4197MB  219GB   215GB   ext4         system1
 7      219GB   434GB   215GB   ext4         system2
 8      434GB   648GB   215GB   ext4         system3
 9      648GB   4001GB  3352GB  ext4         work

I kept some boot partitions since it is easier to have them and not use them, than to later discover I need them. My goal is to set up a disk with three mid-sized Linux systems and then a larger 3 tb shared data area.  What I then did was a fresh install of Ubuntu 17.10 using only /dev/sda6 partition mounted as / and no separate boot disk. During the installation, on the menu for "where do you want to install the bootloader?", I left it at /dev/sda.

When the system boots up, I get the following error and prompt:

   error: unknown filesystem
   Entering rescue mode...
   grub rescue>

At the grub rescue prompt I can do a "ls" and see (hd0) as well as (hd0,gpt1)...(hd0,gpt9). However, if I do an "ls" on any of these partitions, I get:

   grub rescue> ls (hd0, gpt6)
   (hd0,gpt6): Filesystem is unknown

I thought perhaps it could be an issue with ext4 filesystem, so I went back and tried an experiment of creating and mounting a boot disk on /dev/sda3 as /boot and formatting this as ext2.  However, I still get the same error with "ls (hd0,gpt3)" when I try this. So I'm not quite sure if there are more steps I need to do here than just have the partitions created.

After this post, I will also try changing my BIOS to try UEFI and see if this somehow works or if I need to do more to make a UEFI boot...

---

### Post by mev on 2018-02-04
> **mev said:**
> 
After this post, I will also try changing my BIOS to try UEFI and see if this somehow works or if I need to do more to make a UEFI boot...

Changed the BIOS to UEFI and no bootable devices are found.

---

### Post by oldfred on 2018-02-04
How you boot install media, UEFI or BIOS is then how it installs.
But then how you boot installed system depends on settings in UEFI which must match how you installed.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mev on 2018-02-06
> **oldfred said:**
> How you boot install media, UEFI or BIOS is then how it installs.


Tried a UEFI install but not quite successful.

First round with my already partitioned disk, the installer crashed - so I went with a more simple approach:
* Set BIOS to UEFI
* Booted from DVD
* Picked "use entire disk" and let the installer do all the partitioning.

The install completed without error. On reboot, it dumped me into a grub> prompt.

   grub> ls 
   (hd0) (hd0,gpt2) (hd0,gpt1)

With a EFI partition and a ext2 partition

I get the following outputs:

   grub> ls (hd0, gpt2)
   (hd0, gpt2): filesystem is ext2
   grub> ls (hd0,gpt2)/
   . ../ lost+found boot/ swapfile/ etc/ media/ var/ bin/ dev/ home/ lib/ lib64/ mnt/ opt/ proc/ root/ run/ sbin/ snap/ srv/ sys/ tmp/ usr/ vmlinuz initrd.img cdrom/ initrd.img.old
   grub> linux (hd0,gpt2)/vmlinuz
   error: attempt to read or write outside of disk 'hd0'
   grub> initrd (hd0,gpt2)/initrd.img
   error: you need to load the kernel first.

It seems like attempting to load the kernel is giving me a "attempt to read or write outside of disk 'hd0'"

At this point, I am going to chalk it up to some lack of underlying (firmware?) support for this 4 tb disk. I can get a 2 tb disk in legacy mode and will just keep this one for data only and not put on a system.

---

### Post by oldfred on 2018-02-06
Back on your FAT32 partition, I missed that it said msftdata, it should be boot,esp or similar. The msftdata is just another data partition, no matter how you label it.

I do not have large drive like yours, but these are my partitions on SSD & HDD. And I do not yet have drive fully allocated.
With your 4TB drive, it would have made one very, very large / (root) partition.

```
fred@Z170N:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name    Flags
 1      1049kB  53.5GB  53.5GB  fat32        ESP     boot, esp
 2      53.5GB  86.0GB  32.5GB  ext4         xenial
 4      86.0GB  113GB   27.3GB  ext4         bionic
 3      228GB   250GB   22.0GB  ext4         ISO


Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  52.5GB  52.5GB  fat32           EFI System Partition  boot, esp
 2      52.5GB  85.0GB  32.5GB  ext4            zesty
 5      85.0GB  118GB   32.5GB  ext4            server
 6      118GB   338GB   220GB   ext4            data
 8      338GB   365GB   27.3GB  ext4            yakkety
 9      365GB   392GB   27.3GB  ext4            Fedora
 4      891GB   945GB   53.5GB  ext4            backup_b
 3      945GB   998GB   53.5GB  ext4            ISO_b
 7      998GB   1000GB  2202MB  linux-swap(v1)


fred@Z170N:~$ lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT
NAME   LABEL   PARTLABEL    SIZE UUID                                 MOUNTPOINT
sda                       232.9G                                      
&#9500;&#9472;sda1 ESP     ESP         49.8G D966-440A                            /boot/efi
&#9500;&#9472;sda2 xenial  xenial      30.3G 5c1e1a3f-261f-4da5-a0c2-8f479b3039de /
&#9500;&#9472;sda3 ISO     ISO         20.5G ab916e15-8a74-4d6e-a0b1-32718a505dc7 
&#9492;&#9472;sda4 bionic  bionic      25.4G e1e5879e-1828-4a1c-806c-b29c426ccc34 
sdb                       931.5G                                      
&#9500;&#9472;sdb1 ESP_B   EFI System Partition
&#9474;                          48.9G F496-1330                            
&#9500;&#9472;sdb2 zesty   zesty       30.3G a9bd9a65-bc8c-41b1-95b1-2dceb66b2652 
&#9500;&#9472;sdb3 ISO_b   ISO_b       49.8G c395f36d-5e02-4913-a904-e336054b2eff 
&#9500;&#9472;sdb4 backup_b
&#9474;              backup_b    49.8G dd4e4a2e-4785-4441-91b0-28234b98e625 
&#9500;&#9472;sdb5 server  server      30.3G b76dc590-99a3-4e34-af35-e0dd43507232 
&#9500;&#9472;sdb6 data    data       205.1G f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7                      2.1G 3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9500;&#9472;sdb8 yakkety yakkety     25.4G 6c042846-fc6c-4f5b-80fc-7aa678cf09b7 
&#9492;&#9472;sdb9 Fedora  Fedora      25.4G 5326d262-26af-4b38-a523-b0f4d261f1a4 
fred@Z170N:~$
``` 

One suggestion on a 3TB drive.
[https://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](https://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

### Post by mev on 2018-02-07
> **oldfred said:**
> Back on your FAT32 partition, I missed that it said msftdata, it should be boot,esp or similar. The msftdata is just another data partition, no matter how you label it.

I do not have large drive like yours, but these are my partitions on SSD & HDD. And I do not yet have drive fully allocated.
With your 4TB drive, it would have made one very, very large / (root) partition.


The msftdata probably explains why the installer crashed the first time.

However, after that crash I told the installer to use the entire disk and hence also took the default partitioning that came with that. Following is the partitioning that came from the installer using the entire disk:

Model: Seagate BUP BL (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      33.6MB  537MB   503MB   fat32        EFI System Partition  boot, esp
 2      537MB   4001GB  4000GB  ext4

This is also the configuration that resulted in the grub errors above.

At this point I am going to give up on this particular BIOS + disk combination on this (~2014) Gateway laptop. I'll either use smaller system disks for this laptop or try the larger disk on a different laptop with newer BIOS.

---

### Post by oldfred on 2018-02-07
Back when grub/Ubuntu did have a bug on larger drives, since fixed I had some users just shrink the / (root) partition using gparted. The actual data in your partition with a new install is very small. My new install of Bionic is 5.7GB with lots of apps added already.
You can see size with this:
df -h

So you could try to shrink your / partition even all the way down to 30 to 50GB with gparted.
I use 25 to 30GB for / but then have larger data partitions and more / partitions.
You may need to then do a total reinstall of grub (but should not have to). Boot-Repair added to Ubuntu installer makes that relatively easy.
        [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

I would keep the ESP on your drive. I recommend all drives, even drives that may be data only have a small / partition if just for emergency boot.
And I then like to have both the ESP & bios_grub as first two partitions, then no issues of those partitions being too far into drive.

I like this logic:
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

### Post by mev on 2018-02-08
I now have a successful installation.  Here is the parted output:

odel: Seagate BUP BL (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      33.6MB  537MB   503MB   fat32        EFI System Partition  boot, esp
 2      537MB   71.1GB  70.5GB  ext4
 3      71.1GB  123GB   52.4GB                                     lvm
 4      123GB   176GB   52.4GB  ext4
 5      176GB   4001GB  3825GB  ext4         work

Your suggestion of shrinking the Ubuntu partition did the trick. To summarize here are the combined steps I took:
1. Tried a Legacy disk mode. While it works fine for 2 tb disks, I was never able to get this to work with 4 tb.
2. Switched to using UEFI. After some incorrect steps, I had the Ubuntu installer create a proper EFI partition by asking it to install on the entire disk.
3. Using almost the entire disk for a Ubuntu system didn't work, and I ended up shrinking down the system partition down

I now have a portable 4 tb disk that meets my general goals:
= latest Ubuntu release
= latest Fedora release
= (not yet installed) - a partition to install an OS with earlier glibc so that I can create binaries that will generally run on multiple distributions
= large data disk for project workspace that is common to any of the three releases above

Thanks for your help and quick assistance for pointers of things to try.

---

### Post by oldfred on 2018-02-08
Some with Fedora, do not use default LVM install.
They just choose a /  (root) ext4 partition.

The advantage of LVM is when it controls the entire hard drive. But requires advanced LVM tools to manage it, so best only for knowledgeable users. 
Often used by those with servers, less so with desktops.

---

