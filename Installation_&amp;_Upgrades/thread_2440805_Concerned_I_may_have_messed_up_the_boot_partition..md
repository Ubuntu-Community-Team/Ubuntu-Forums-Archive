---
title: "Concerned I may have messed up the /boot partition."
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by casey-earnshaw on 2020-04-15
Hi everyone

I've installed Ubuntu LTS for a friend who was interested in Linux but wanted to keep her windows. When trying to install it I got EFI errors. What I ended up doing to allow the system to install and boot was to create an EXT2 200mb /boot partition as the first partition, after doing so it was able to boot up along side windows via the grub menu. However every time we have tried to install a piece of software (such as steam) we get the following error:

```
Setting up initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.173.17) ...
update-initramfs: Generating /boot/initrd.img-5.3.0-46-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-5.3.0-46-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 1
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.3.0-46-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-5.3.0-46-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is this happening because I set too small a size for the boot partition? If so is there a way I can increase it without having to reinstall the whole system and how big a partition would you recommend in the future?

Thanks for your time. I appreciate any help you can give

---

### Post by oldfred on 2020-04-15
Post this:
sudo parted -l
lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint

Do not confuse a required ESP - efi system partition that has grub boot files with an optional /boot partition.
The /boot is often used with LVM or server installs, but otherwise not with desktops.

---

### Post by casey-earnshaw on 2020-04-15
Thanks for your reply. We have decided to reinstall but give the boot partition 4 gigs I won’t be able to run commands until it’s finished now I’ll let you know in half an hour or so

---

### Post by casey-earnshaw on 2020-04-15
Okay so setting that much has fixed the errors although I am left with a feeling that I’ve done it wrong. Still she’s happily exploring the system right now and it is booting so we might just leave it now. When the installer complained about efi it opened Firefox and it seems that a bug associated with it was being quite talked about. Is it possible that the installer was incorrectly assuming we needed a special partition due to this bug?

---

### Post by oldfred on 2020-04-15
Again post partition info.
Do not know what you have from general description.

Is install UEFI or BIOS, MBR or gpt partitioning?

---

### Post by yancek on 2020-04-15
You haven't indicated which version of windows is being used which is significant because microsoft has been licensing 'windows' systems for 35 years!  Ubuntu also has had the site at the link below available online for years and is the official documentation on dual booting with windows UEFI.  Reading that might save you a lot of future trouble.  Posting the output of the commands suggested above would be a good beginning to getting help.

Generally on a standard install (without LVM) there isn't much reason to have a separate boot partition.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by TheFu on 2020-04-15
The original question:
>  Is this happening because I set too small a size for the boot partition?
Answer: Yes.  /boot is too small and will need lots and lots of maintenance to keep from filling up.  A full /boot/ often/usually causes all sorts of difficult problems. 

None of the following is helpful to you at this point.

4G for /boot is huge.  I feel a little wasteful having 700+MB for /boot/.
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/sdb1                         ext2  720M  252M  432M  37% /boot
/dev/mapper/hadar--vg-root        ext4   22G  8.3G   13G  40% /

```
LVM is usually not all that useful for non-professionals. There are some complexities with using it to the greatest advantage and the default Ubuntu LVM install is less than great as configured.  I always have to resize the LVs for swap and /, then usually create a few other LVs for other purposes and mount those where needed, like /home/ or /u/ or /var/lib/.  Initially, that / LV wasn't 22G in size. It was 480G.

If you don't care about LVM, probably best to ignore it and what I've written.

There are all sorts of disk layouts, sizes, depending on the available hardware, planned workloads, and other considerations.
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) has a concrete layout example with sizes and commands to see the sizes and lvm data.

---

### Post by casey-earnshaw on 2020-04-16
Hi

Sorry it's taken me a while to respond to this. Thank you for all your help so far.

The version of windows is Windows 10 home.

The output of parted -l is:

```
Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  556MB   555MB   ntfs         Basic data partition          hidden, diag
 2      556MB   661MB   105MB   fat32        EFI system partition          boot, esp
 3      661MB   677MB   16.8MB               Microsoft reserved partition  msftres
 4      677MB   532GB   532GB   ntfs         Basic data partition          msftdata
 5      532GB   536GB   4000MB  ext4
 6      536GB   596GB   60.0GB  ext4
 7      596GB   2000GB  1404GB  ext4

```

lsblk outputs

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  89.1M  1 loop /snap/core/8268
loop1    7:1    0   4.2M  1 loop /snap/gnome-calculator/544
loop2    7:2    0   3.7M  1 loop /snap/gnome-system-monitor/127
loop3    7:3    0   956K  1 loop /snap/gnome-logs/81
loop4    7:4    0 160.2M  1 loop /snap/gnome-3-28-1804/116
loop5    7:5    0  44.9M  1 loop /snap/gtk-common-themes/1440
loop6    7:6    0  14.8M  1 loop /snap/gnome-characters/399
loop7    7:7    0  54.7M  1 loop /snap/core18/1668
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0   529M  0 part 
&#9500;&#9472;sda2   8:2    0   100M  0 part /boot/efi
&#9500;&#9472;sda3   8:3    0    16M  0 part 
&#9500;&#9472;sda4   8:4    0 495.2G  0 part 
&#9500;&#9472;sda5   8:5    0   3.7G  0 part /boot
&#9500;&#9472;sda6   8:6    0  55.9G  0 part /
&#9492;&#9472;sda7   8:7    0   1.3T  0 part /home

```

Although the boot partition is probably way too big everything seems to be working and she seems quite happy with it so that's at least positive.

Thanks again

---

