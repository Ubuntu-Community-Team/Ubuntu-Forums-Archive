---
title: "How to prevent not having enough space to upgrade"
date: 2023-03-29
forum: Installation &amp; Upgrades
---

### Post by deepskydiver on 2023-03-29
I use encrypted partitions.
A couple of years ago I had to do a reinstall rather than upgrade to 20.04 because I didn't have enough space on the boot partition. It was frustrating but ok..
Now once again I find myself in the position where I cannot upgrade (now to 22.04) for the same reason:

[I]Not enough free disk space

The upgrade has aborted. The upgrade needs a total of 439 M free space on disk '/boot'. Please free at least an additional 50.9 M of disk space on '/boot'. You can remove old kernels using 'sudo apt autoremove' and you could also set COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of your initramfs.
[/I]
So, a couple of questions:
- Having already removed old kernels (and reclaimed nearly 750 Kb!) is there anything I can do or will I have to reinstall?
- Am I doomed to do a clean install every 2 years, how can I avoid continually repeating this if I do a reinstall?

Thanks to those who have experience here!

---

### Post by deadflowr on 2023-03-29
We would need more information for anyone to give any useful help.
Please look at this [https://ubuntuforums.org/showthread.php?t=2475931]("https://ubuntuforums.org/showthread.php?t=2475931")

---

### Post by guiverc on 2023-03-29
I wouldn't use a /boot partition.  Do you really need one?  (*Note: I'm **not** talking about the ESP or EFI System Partition here, only /boot*).

If it's only a directory on a larger partition; its generally far easier to create space across a larger partition, than create the same space on a smaller partition with less you can clean.  Also if it's a large partition, you can just temporarily remove some larger packages, upgrade what you need; then re-install what you removed; ie. more 'easy' options.

I regularly run out of space with the *release-upgrade* process too, and on cases where the ssd/drive is very small, I perform a non-destructive re-install of the newer release to achieve what I think of as an '*Upgrade via re-install*', ie. no user file/config is touched, all my *manually installed* packages get auto-reinstalled etc.  You didn't specify though if you're asking about a **desktop or server install**, as this method is less useful for server apps/installs (*but I've used it with encrypted desktop partitions too; but love it most as its so fast!*)

FYI:  The re-install options I'm mentioning here are easier for *flavors* which have 'universe' enabled by default; esp. if many of your *manually installed* (ie. *those packages you added post-install*) came from 'universe'. I know its possible on Ubuntu Desktop too, I've just had more luck with the *flavors* (*mostly I think because I forget to enable 'universe' before re-install as is required for Ubuntu Desktop when you were using packages from 'universe' so it can download & re-install them* *for you*).

Also if you have sufficient space on /, you could just *move* the /boot data to a different location (*which has space*), adjust your *file-system table* (*fstab*) to reflect that, then perform the *release-upgrade*, and post-upgrade, restore everything back to where it was (*ie. undo the changes you made, IF you have space*)... alas this is [I]messy!

Note:  these are just my thoughts/2c. 
[/I]

---

### Post by MAFoElffen on 2023-03-29
Do these please, and post the output within CODE Tags:
```

lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq
df -hT -x tmpfs -x devtmpfs | grep -v '/snap/'

```
There are reasons for a /boot partition... But it takes work to maintain it to prevent problems.

Usually I setup my /boot partitions at about 2 GB...

---

### Post by deepskydiver on 2023-03-29
> **MAFoElffen said:**
> Do these please, and post the output within CODE Tags:
```

lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq
df -hT -x tmpfs -x devtmpfs | grep -v '/snap/'

```


Thanks the other suggestions for diagnostics felt uncomfortably invasive I guess.
What options do I have at install time to avoid or resize a boot partition?
I didn't know I had a choice.

Here are the outputs:

```

NAME                    SIZE FSTYPE      LABEL   MOUNTPOINT                   MODEL
sda                   238.5G                                                  LITEON_IT_L8T-256L9G
&#9500;&#9472;sda1                  512M vfat                /boot/efi                    
&#9500;&#9472;sda2                  732M ext4                /boot                        
&#9492;&#9472;sda3                237.3G crypto_LUKS                                      
  &#9492;&#9472;sda3_crypt        237.2G LVM2_member                                      
    &#9500;&#9472;vgubuntu-root   236.3G ext4                /                            
    &#9492;&#9472;vgubuntu-swap_1   976M swap                [SWAP]                       
sdb                   119.3G                                                  ExtremePro
&#9492;&#9472;sdb1                119.3G ntfs        SANDISK /media/b/SANDISK             

```

```


Disk /dev/sda: 238.49 GiB, 256060514304 bytes, 500118192 sectors
Disk model: LITEON IT L8T-25
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 7FEC7AA4-B6B9-43E7-816B-1A61C0273652

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2549759   1499136   732M Linux filesystem
/dev/sda3  2549760 500117503 497567744 237.3G Linux filesystem

Disk /dev/mapper/sda3_crypt: 237.25 GiB, 254737907712 bytes, 497534976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vgubuntu-root: 236.26 GiB, 253675700224 bytes, 495460352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vgubuntu-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sdb: 119.26 GiB, 128043712512 bytes, 250085376 sectors
Disk model: ExtremePro      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x025cdc0e

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1  *     2048 250085375 250083328 119.3G  7 HPFS/NTFS/exFAT

```

```

Filesystem                Type      Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4      232G   42G  179G  19% /
/dev/sda2                 ext4      704M  282M  371M  44% /boot
/dev/sda1                 vfat      511M  6.1M  505M   2% /boot/efi
/dev/sdb1                 fuseblk   120G  123M  120G   1% /media/b/SANDISK

```

---

### Post by Impavidus on 2023-03-29
On encrypted systems, /boot is mandatory.

A larger /boot partition could help. It's not as if a 2GB /boot partition takes a huge chunk of a modern hard drive.

---

### Post by ActionParsnip on 2023-03-29
If you use LTS then you don't need to upgrade every 2 years. LTS releases are supported for 5 years. Personally I ignore every other LTS release, when I come to reinstall I grab a new internal disk to install to, as well. Keeps you on a new SSD rather than flogging the old one to death :)

---

### Post by SeijiSensei on 2023-03-29
Anything smaller than 512 MB will not be able to handle upgrades. I know. I used to use 256M for /boot, and, as the years went by, it eventually ran out of space. I use 1 GB these days.

---

### Post by MAFoElffen on 2023-03-29
I typically use 1.5 to 2 GB for /boot, but I use a ZFS bpool and do automated ZSys snapshots of /boot... With my own script to clean up / roll off old snapshots.
> **Impavidus said:**
> On encrypted systems, /boot is mandatory.

A larger /boot partition could help. It's not as if a 2GB /boot partition takes a huge chunk of a modern hard drive.
That used to be true, but then Grub2 could read LUKS1. Later/Now, Grub2 can read LUKS2. So now you do not need a separate /boot partition. It "is" easier and safer to be able to recover a LUKS2 container if you have an unencrypted /boot, but is not required.

Giving up 1-2 GB's these days is a pittance on a TB drive... Times have changed.

Since you do have a separate /boot partition... I would hate to recommend this, but to give room to grow into the future, I would backup what you have, then resize your encrypted root partition and give the recovered space to your /boot partition.
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

### Post by deepskydiver on 2023-03-29
Can I resize the /boot partition?
Is there an option on install to avoid this problem?

---

### Post by MAFoElffen on 2023-03-30
> **deepskydiver said:**
> Is there an option on install to avoid this problem?
Not while using the automated checkbox option (LVM with encryption. If you manually create the partitions and Luks containers, unlocking them... Then start the installation and use the "Something Else" option in the installer, selecting the appropriate pieces to install to.

I have built LUKS encrypted systems with both non-ecrypted /boot, and encrypted boots (LUKS & LUKS2) to test on, and for contributing/testing for boot-info & boot-repair ([https://ubuntuforums.org/showthread.php?t=2470405&p=14081645#post14081645](https://ubuntuforums.org/showthread.php?t=2470405&p=14081645#post14081645)). Having both the boot and root partitions encrypted with LUKS is a pain in the behind. Not to setup.  ([https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144)) But for daily use. I usually go a step further and setup a keyfile. Otherwise, you get prompted twice at each boot, to unlock each LUKS container.

But, personally, for my own use, I setup ZFS-On-Root systems using native pool encryption.

I usually setup my own partitions and their sizes manually. Unless the system is meant to be "disposable" after just a few tests. 

> **deepskydiver said:**
> Can I resize the /boot partition?
Yes, (refer to the url I posted in my last post). Boot the LiveUSB, so that the LUKS partition is not mounted as the root drive. Install and configure the lvm2 and cryptsetup in the Live Environment. Reduce the (root) file system with resize2fs. Reduce the (root) (LVM) Logical Volume with lvreduce. Reduce the (LVM) Physical Volume with pvresize. Reduce the Crypt with cryptsetup. Reduce the Partition storing the crypt with fdisk or GParted. Then use GParted to enlarge your boot partition. Reboot to your encrypted hard drive.

---

### Post by xinuzi on 2023-03-30
enlarge your space?

(The Universe = Endless)

---

### Post by MAFoElffen on 2023-03-30
> **xinuzi said:**
> enlarge your space?

(The Universe = Endless)
@xinuzi --

Oh man!!! (Philosophically?) I lost it and couldn't stop laughing!!! That was great. 

Thank you! I needed that humor today.

---

### Post by deepskydiver on 2023-03-30
This is very disappointing.
So anyone who installs a clean Ubuntu system with an encrypted partition, *following the defaults* will not be able to upgrade to the next release.
That doesn't strike anyone else as a problem?

---

### Post by TheFu on 2023-04-03
> **deepskydiver said:**
> This is very disappointing.
So anyone who installs a clean Ubuntu system with an encrypted partition, *following the defaults* will not be able to upgrade to the next release.
That doesn't strike anyone else as a problem?
Anyone using encryption will have excellent backups, so it isn't a big deal.  If you use encryption and don't have excellent backups, you are asking for massive data loss, even if you don't realize it.

I used to use 512MB for /boot.  Then ran into the issue of it being really tight when I had multiple kernel lines installed ... say the 5.4 and 5.10 kernels.  Removing all the 5.4 kernels removed the tight space issue.  More and more people are demanding more and more file systems be supported for boot, which means the size of the boot image has to be larger and larger to bring all that support for btrfs, zfs, ext2/3/4, xfs, and fat32 on the UEFI partition.  Add in LVM and/or encryption with LUKS and it gets even larger still.

The solution would be for the Canonical installer to ask at install time which file systems we want supported.  There's a downside to asking too many questions and Canonical has decided that being simple, asking few questions, is the better option.  We can always build our own kernels and image with just the stuff we need. You are free to learn to do that.  I freak out a little that 500MB isn't large enough because I remember having 15+ OSes in a 240**MB** HDD. The amount of bloat in modern Linux is huge.

Anyway, resizing is possible, if you have contiguous free space, but the default LVM+LUKS install doesn't leave any free space. Effectively, you are screwed.

But your best hope is to clean up old kernels so that only 2 remain on the system, then a release-upgrade might have sufficient room.

I have to say this.   I've had release upgrades take over 3 hours, whereas a fresh install is about 15 minutes. Further, it removes all the cruft left over from prior versions.  With each release, subsystems are changed, so having those old files around when they aren't still being used can become confusing.  Every 3-5 yrs, a fresh install really is a good idea.

If you really care about flexible storage setups, there are many things we can do, but those things tend to be manual and require a level of understanding the casual end-user doesn't want to know.  I only learned it because the default installs were causing me issues and removing flexibility that I knew was possible.  There's always a trade off between hassle and flexibility, unfortunately.

I do understand that there is a Qt partitioning tool, usually installed with KDE/Kubuntu that allows resizing LVM and LUKS containers.  If you create a boot flash with Kubuntu, perhaps it will be there and available? After all, any partition changes like that will need to be booted off a flash drive anyway.

**Before starting anything, be certain you backup everything you can't lose. ** That's always the requirement.

---

### Post by #&amp;thj^% on 2023-04-03
> **TheFu said:**
> Anyone using encryption will have excellent backups, so it isn't a big deal.  If you use encryption and don't have excellent backups, you are asking for massive data loss, even if you don't realize it.

I do understand that there is a Qt partitioning tool, usually installed with KDE/Kubuntu that allows resizing LVM and LUKS containers.  If you create a boot flash with Kubuntu, perhaps it will be there and available? After all, any partition changes like that will need to be booted off a flash drive anyway.

**Before starting anything, be certain you backup everything you can't lose. ** That's always the requirement.

+1
More: If you use LVM together with LUKS, you first need to resize LVM logical volumes (which KDE Partition Manager can also do).
```
apt show partitionmanager
Package: partitionmanager
Version: 22.12.3-0ubuntu1
Priority: optional
Section: universe/admin
Origin: Ubuntu
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 5,823 kB
Depends: kio, libc6 (>= 2.34), libkf5configcore5 (>= 5.91~), libkf5configgui5 (>= 5.91~), libkf5configwidgets5 (>= 5.91~), libkf5coreaddons5 (>= 5.91~), libkf5crash5 (>= 5.91~), libkf5dbusaddons5 (>= 5.91~), libkf5i18n5 (>= 5.91~), libkf5jobwidgets5 (>= 5.91~), libkf5kiocore5 (>= 5.91~), libkf5kiogui5 (>= 5.91~), libkf5widgetsaddons5 (>= 5.91~), libkf5windowsystem5 (>= 5.91.0), libkf5xmlgui5 (>= 5.91~), libkpmcore12 (>= 22.12.3~), libpolkit-qt5-1-1 (>= 0.112.0), libqt5core5a (>= 5.15.2~), libqt5gui5 (>= 5.15.2~) | libqt5gui5-gles (>= 5.15.2~), libqt5widgets5 (>= 5.15.2~), libstdc++6 (>= 5)
Suggests: btrfs-progs, dosfstools, hfsplus, hfsutils, jfsutils, ntfs-3g, reiser4progs, reiserfsprogs, xfsprogs
Homepage: https://www.kde.org/applications/system/kdepartitionmanager
Task: kubuntu-desktop, lubuntu-desktop, ubuntustudio-desktop-core, ubuntustudio-desktop
Download-Size: 2,171 kB
APT-Sources: http://archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
Description: file, disk and partition management for KDE
 Partition Manager is a utility program to help you manage the disk devices,
 partitions and file systems on your computer. It allows you to easily create,
 copy, move, delete, resize without losing data, backup and restore partitions.
 .
 Partition Manager supports a large number of file systems, including ext2/3/4,
 reiserfs, NTFS, FAT16/32, jfs, xfs and more. Note that to gain support for a
 specific file system other than ext2/3/4, you should install the corresponding
 suggested package.
 .
 Partition Manager is based on libparted (like gparted) and makes use of the
 KDE libraries for its user interface.


```

---

### Post by TheFu on 2023-04-04
So, LUKS encryption on Ubuntu uses /boot, /boot/efi, and another partition for everything else.  That other partition is 100% used to create a LUKS container.  Then inside that LUKS container are LVM PVs, VGs, and LVs.  This way, only 1 luksopen is required to access everything that isn't under /boot/.  

If you are running low on space in /boot/, then it is unlikely there is enough spare storage that isn't inside the LUKS container (usually sda3 partition), so lots of things need to happen to make space ... which would mean reducing the VG size, reducing the PV size, reducing the LUKS container, then reducing the size of sda3.  It will be ugly, I fear.  It would likely be safest/easiest to take space from the far end, not the beginning, then move the /boot/ partition to that space with 200MB-500MB free to the right of it (I'm thinking of gparted GUI).  Then resizing the /boot/ partition to be larger would be relatively fast.

But if your VG is very full, this can't be done.

So ... the real answer is that a fresh install where you manually resize the partitions to the sizes you want BEFORE allowing the install too far would be best.  I have doubts that the LVM+LUKS install will allow any manual control over what they do.  What I've done previously was to do the default install with LVM+LUKS, then before doing almost anything else on the new system, I reduce the VG, PV, LUKS container and sda3 partition by a "reasonable amount" so that some spare storage is available for later, if it is needed.  I consider using LUKS mandatory for laptops, but I also never have anything important on any laptop, so wiping it and starting over isn't a big deal.  What's 15 minutes for a fresh install anyway?  Nothing.

---

### Post by cainesaj on 2023-04-04
> **deepskydiver said:**
> 
I use encrypted partitions.


I use encrypted partitions, too.

> 
[I]The upgrade has aborted. The upgrade needs a total of 439 M free space on disk '/boot'. Please free at least an additional 50.9 M of disk space on '/boot'. You can remove old kernels using 'sudo apt autoremove' and you could also set COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of your initramfs.
[/I]

You didn't mention if you have followed the suggestion to set [FONT=courier new]COMPRESS=xz[/FONT]. I have.

> 
Having already removed old kernels (and reclaimed nearly 750 Kb!) is there anything I can do or will I have to reinstall?


750 Kilobits is not a lot of space for kernels. Even 750 Kilobytes is not a lot of space for what is stored in [FONT=courier new]/boot[/FONT].
How did you remove "old kernels"? Show as best you can.

When cleaning out files from [FONT=&amp]/boot[/FONT] for an update or upgrade, it should be safe to remove all files related to older kernels, that is presuming that you have booted the most recently installed kernel.

```
 
$ ls -1sh /boot/*-$(uname -r)257K /boot/config-5.15.0-69-generic
111M /boot/initrd.img-5.15.0-69-generic
6.0M /boot/System.map-5.15.0-69-generic
 12M /boot/vmlinuz-5.15.0-69-generic

```

Given the corresponding files for older kernels, identify the packages which own them and remove them carefully so as to not remove the ones for the current kernel.

```
$ dpkg -S /boot/*-5.15.0-67-generic
linux-modules-5.15.0-67-generic: /boot/config-5.15.0-67-generic
dpkg-query: no path found matching pattern /boot/initrd.img-5.15.0-67-generic
linux-modules-5.15.0-67-generic: /boot/System.map-5.15.0-67-generic
linux-image-5.15.0-67-generic: /boot/vmlinuz-5.15.0-67-generic
$ sudo apt autoremove --purge linux-image-5.15.0-67-generic linux-modules-5.15.0-67-generic
...
$ sudo rm -v /boot/initrd.img-5.15.0-67-generic

```

You can enumerate multiple versions in the shell with something like [FONT=courier new]linux-image-5.15.0-{61,65,67}-generic[/FONT].

> 
Am I doomed to do a clean install every 2 years...?


I doubt it if you clean up [FONT=courier new]/boot[/FONT] like I suggest. While I don't remember which LTS release was the original install using the recommended layout, I think it was 16.04 (Xenial Xerus), since when I've updated it with each LTS. That recommended layout included

```
$ df -hT /boot
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda1      ext2  470M  262M  184M  59% /boot

```

> 
how can I avoid continually repeating this if I do a reinstall?


For the one-time effort of a clean install of a new LTS release, you can make better use of your storage on that host so as to avoid this issue and get all the advantages of a fresh install including removing cruft, getting newer defaults and configs, having a more easily supportable platform and that new install smell.

---

### Post by TheFu on 2023-04-04
```
$ du -c /boot/*69*
260K    /boot/config-5.15.0-69-generic
119M    /boot/initrd.img-5.15.0-69-generic
6.0M    /boot/System.map-5.15.0-69-generic
11M     /boot/vmlinuz-5.15.0-69-generic
**136M    total**

```
and
```

$ du -c /boot/*67*
260K    /boot/config-5.15.0-67-generic
119M    /boot/initrd.img-5.15.0-67-generic
6.0M    /boot/System.map-5.15.0-67-generic
11M     /boot/vmlinuz-5.15.0-67-generic
[B]136M    total
[/B]
```So about 150MB per kernel is needed.

If you clean up the installed kernels, 500MB for /boot should be sufficient.
```
$ dft |grep /boot
/dev/nvme0n1p2                              ext4  574M  280M  252M  53% /boot
/dev/nvme0n1p1                              vfat   50M  6.1M   44M  13% /boot/efi

```
That's on a 20.04 system.  I don't keep lots and lots of extra kernels around. Since I patch weekly, sometimes I miss mid-week package churn.

---

### Post by deepskydiver on 2023-04-12
So I thought I'd try this: Create a USB boot disk and boot from that, then run a partition manager and shrink the main data partition and move the /boot partition there.
But even when unencrypted the main partition of over 200Gb cannot be shrunk by more than about 36Mb. Which is helpful.
And the option of "*set COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of your initramfs."* has not yielded much if any gain on the boot partition.
This is a little ridiculous: to force a choice without any option that *prevents *upgrades. It's quite a flaw in the process, unnecessary and avoidable.

So I'm guessing from here that to upgrade I have to boot from a Ubuntu disk, wipe the data partition, resize the boot partition and then install?

---

### Post by TheFu on 2023-04-12
Recent releases have created larger boot partitions to avoid this issue.
```
Filesystem                Type      Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4      232G   42G  179G  19% /
/dev/sda2                 ext4      704M  282M  371M  44% /boot
/dev/sda1                 vfat      511M  6.1M  505M   2% /boot/efi
```

The /boot/ partition above is larger than any boot I've ever created.  OTOH, Every other release, I do a fresh install. Also, I remove old kernels and only have 1 line of kernels installed before doing a release-upgrade.

Perhaps you have junk in your /boot/ that was somehow left over?

The root LV is huge - much too large, IMHO.  A root LV should contain the OS, but little else. 35G is usually the largest I allow.  Then I create LVs for swap, var, home and any specific data areas ... like for VMs or Linux Containers.  It is all about the ability to backup and restore systems efficiently.

---

### Post by deepskydiver on 2023-04-12
> **TheFu said:**
> Recent releases have created larger boot partitions to avoid this issue.
```
Filesystem                Type      Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4      232G   42G  179G  19% /
/dev/sda2                 ext4      704M  282M  371M  44% /boot
/dev/sda1                 vfat      511M  6.1M  505M   2% /boot/efi
```

The /boot/ partition above is larger than any boot I've ever created.  OTOH, Every other release, I do a fresh install. Also, I remove old kernels and only have 1 line of kernels installed before doing a release-upgrade.

Perhaps you have junk in your /boot/ that was somehow left over?

The root LV is huge - much too large, IMHO.  A root LV should contain the OS, but little else. 35G is usually the largest I allow.  Then I create LVs for swap, var, home and any specific data areas ... like for VMs or Linux Containers.  It is all about the ability to backup and restore systems efficiently.

My boot partition is the result of a clean install on an unpartioned HDD. You may think it large, but unfortunately even with no old kernels there is *still *not enough space for the upgrade.
Do you think if I removed all partitions and did a clean 22.04 install it would make enough space in /boot for the next upgrade? I'm skeptical! :)

---

### Post by MAFoElffen on 2023-04-13
I spun up a default install of 22.04 ZFS LUKS2:
```

mikeferreira@ZFS-LUKS2-001:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
NAME               SIZE FSTYPE      LABEL                  MOUNTPOINT                                 MODEL
sr0                3.4G iso9660     Ubuntu 22.04 LTS amd64 /media/mikeferreira/Ubuntu 22.04 LTS amd64 QEMU DVD-ROM
zd0                500M crypto_LUKS                                                                   
 +- keystore-rpool   484M ext4        keystore-rpool         /run/keystore/rpool                        
vda                 30G                                                                               
 +- vda1             512M vfat                               /boot/efi                                  
 +- vda2             1.4G crypto_LUKS                                                                   
   +- cryptoswap     1.4G swap        cryptoswap             [SWAP]                                     
 +- vda3             1.5G zfs_member  bpool                                                             
 +- vda4            26.7G zfs_member  rpool                                                             

```
On LVM LUKS 22.04
```

mafoelffen@ubuntu-22-04-luks-01:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
NAME                    SIZE FSTYPE      LABEL MOUNTPOINT                         MODEL
sr0                    1024M                                                      QEMU DVD-ROM
vda                      25G                                                      
 +- vda1                  512M vfat              /boot/efi                          
 +- vda2                  1.7G ext4              /boot                              
 +- vda3                 22.8G crypto_LUKS                                          
    +- vda3_crypt         22.8G LVM2_member                                          
      +- vgubuntu-root    20.3G ext4              /                                  
      +- vgubuntu-swap_1   2.5G swap              [SWAP]                             

```
So yes, confirmed that it now creates larger boot partitions.

---

