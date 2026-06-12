---
title: "Xubuntu 22.04 -&gt; 24.04 Upgrade failed to install GRUB"
date: 2024-10-13
forum: Installation &amp; Upgrades
---

### Post by cjsmall on 2024-10-13
I'm on a machine with dual Xeon CPUs and a straight Xubuntu installation.  The primary OS files partition is located on a pair of mirrored SSDs /dev/md0 (sdb1 and sdc1) mounted on /.

I previously ran a test upgrade from 22.04 -> 24.04 on an Asus laptop with only minor problems.  Earlier today i started the upgrade on my primary workstation.  With only a few glitches, the upgrade ran until near the end when it displayed the following:

```

[ Configuring grub-pc ]

GRUB failed to install on the following devices:

/dev/sdb  /dev/sdc

Do you want to continue anyway?  If you do your computer may not start up properly.

Writing GRUB to boot device failed - continue?

  <Yes>        [<No>]
```

I'm unsure how to proceed.  The system is still running and I can ssh to the command-line from my other machine or enter a console with Ctrl-Alt-F2.  Everything looks fine for the devices in /dev.  However, I've discovered that certain critical files are still not installed, one being **/usr/bin/add-apt-repository**.  I was going to install the **boot-repair** tool which is when I discovered that add-apt-repository was missing.  The **update-grub** command is available.

When I was prompted to install a new **/etc/default/grub** I elected to retain the original.  There is a **grub.ucf-dist** file in that directory that is not much different from the current one, so I don't see that this is the source of the problem.

Here is a current list of my /boot directory;

```

-rw------- 1 root root  4379900 Jul 29  2019 System.map-5.0.0-23-generic
-rw------- 1 root root  6289146 Aug  2 07:15 System.map-5.15.0-119-generic
-rw------- 1 root root  6291214 Aug 29 05:23 System.map-5.15.0-122-generic
-rw------- 1 root root  9061992 Aug 30 01:32 System.map-6.8.0-45-generic
-rw-r--r-- 1 root root   224430 Jul 29  2019 config-5.0.0-23-generic
-rw-r--r-- 1 root root   262072 Aug  2 07:15 config-5.15.0-119-generic
-rw-r--r-- 1 root root   262106 Aug 29 05:23 config-5.15.0-122-generic
-rw-r--r-- 1 root root   287493 Aug 30 01:32 config-6.8.0-45-generic
drwxr-xr-x 6 root root     4096 Oct 12 18:23 grub
-rw-r--r-- 1 root root 53540037 Sep 30 13:01 initrd.img-5.0.0-23-generic
-rw-r--r-- 1 root root 70740416 Sep 30 13:01 initrd.img-5.15.0-119-generic
-rw-r--r-- 1 root root 63598294 Oct 12 18:32 initrd.img-5.15.0-122-generic
-rw-r--r-- 1 root root   142796 Apr  8  2024 memtest86+ia32.bin
-rw-r--r-- 1 root root   143872 Apr  8  2024 memtest86+ia32.efi
-rw-r--r-- 1 root root   147744 Apr  8  2024 memtest86+x64.bin
-rw-r--r-- 1 root root   148992 Apr  8  2024 memtest86+x64.efi
-rw------- 1 root root  8711928 Jul 29  2019 vmlinuz-5.0.0-23-generic
-rw------- 1 root root 11704712 Aug  2 07:43 vmlinuz-5.15.0-119-generic
-rw------- 1 root root 11700328 Aug 29 05:47 vmlinuz-5.15.0-122-generic
-rw------- 1 root root 14948744 Aug 30 02:02 vmlinuz-6.8.0-45-generic
```

I'm looking for advice on what to do next.  I would like to complete the upgrade but suspect that I will likely not be able to reboot if I don't address the GRUB problem first.  Any suggestion as to next steps would be greatly appreciated.

Regards.
--
Jeff

---

### Post by oldfred on 2024-10-13
It says grub-pc which is for BIOS boot.
Is install in old BIOS boot mode? Do you have a tiny 1MB unformatted partition with bios_grub partition, if gpt, not old MBR(msdos) partitions?
Or is system really UEFI and it is installing the wrong grub. Without bios_grub partition, grub will not install to gpt partitioned drives. 
UEFI version of grub is grub-efi-amd64. Your fstab would have mount of esp if UEFI.

Post these.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
cat /etc/fstab

---

### Post by cjsmall on 2024-10-13
Yes, I wondered about the grub-pc notation as well.  When I tried to research this problem all references I could find seemed to be to Windows systems with a Linux partition.  This system uses an Asus motherboard and BIOS that precedes UEFI.  The partitions are standard ext4 and there is no separate grub partition.  Here is the info you requested:

**1-> lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint ,uuid,partuuid**
lsblk: ,uuid,partuuid: not a block device

2-> **lsblk**  [selected portion of relevant output]
sda           8:0    0   3.6T  0 disk  
&#9492;&#9472;sda1        8:1    0   3.6T  0 part  
sdb           8:16   0 476.9G  0 disk  
&#9500;&#9472;sdb1        8:17   0 445.2G  0 part  
&#9474; &#9492;&#9472;md0       9:0    0   445G  0 raid1 /
&#9492;&#9472;sdb2        8:18   0  31.8G  0 part  
  &#9492;&#9472;md1       9:1    0  31.8G  0 raid1 [SWAP]
sdc           8:32   0 476.9G  0 disk  
&#9500;&#9472;sdc1        8:33   0 445.2G  0 part  
&#9474; &#9492;&#9472;md0       9:0    0   445G  0 raid1 /
&#9492;&#9472;sdc2        8:34   0  31.8G  0 part  
  &#9492;&#9472;md1       9:1    0  31.8G  0 raid1 [SWAP]
sdd           8:48   0   3.6T  0 disk  
&#9492;&#9472;md127       9:127  0   3.6T  0 raid1 
  &#9492;&#9472;md127p1 259:0    0   3.6T  0 part  /x
sde           8:64   0   3.6T  0 disk  
&#9492;&#9472;md127       9:127  0   3.6T  0 raid1 
  &#9492;&#9472;md127p1 259:0    0   3.6T  0 part  /x

**3 -> cat /etc/fstab**  [edietd out comment lines]
UUID=d7121d57-8cf9-42a5-b7c3-75f414ce3e09 /       ext4  errors=remount-ro  0  1
UUID=8e8ce37a-56ec-4624-8790-2705e9d8ac7c none    swap  sw                 0  0
LABEL=md2                   /x     ext4  defaults           0  2
LABEL=backup    /mnt/bak       ext4  rw,suid,dev,exec,noauto,nouser,async  0  2

[B]4 -> cat /etc/lsb-release
[/B]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=24.04
DISTRIB_CODENAME=noble
DISTRIB_DESCRIPTION="Ubuntu 24.04.1 LTS"

I really appreciate the reply.  I hope this info provides some clues as to what is going on.  Do you think I still have a useable grub or has it been mangled at this point?

Another question is, if I answer **Yes** to continue past the current point in order to complete the upgrade, will I still have the option not to reboot at the end, or will the upgrade process just automatically plow ahead and reboot?  I still have control of the running system at this point and don't want to get to a non-booting state.

Thanks!

---

### Post by oldfred on 2024-10-13
Do not know RAID.

But if drive is 3.6TB, then it better be gpt not old MBR. MBR has a hard max of 2TB as it was designed in the 1980's when MB was large, GB was unheard of, so they made it support up to 2TB. Your smaller drives, if MBR, may install grub & boot, but you have to specify grub to install to one of those drives & then set BIOS to boot that drive.

If not gpt, then you converted drive to 2TB or are using some proprietary drive configuration.
With BIOS boot & gpt you must have a 1MB unformatted partition with bios_grub flag or code ef02 if using gdisk.
Grub may have installed before with issues or say it does not install as embedding not possible.

---

### Post by cjsmall on 2024-10-13
First, I've upgraded this system successfully for the past ten years.

Ignore the 4TB hard drives.  These hold user data and have nothing to do with the OS.

The OS resides on a pair of Crucial CT512M55 512GB partitioned SSDs, and I was almost 100% sure that these were initially partitioned as GTP, with:

 sdb1/sdc1 forming 445.2 GB md0 raid 1 mounted on /
sdb2/scd2 forming   31.8 GB md1 raid 1 swap partition

However, here is what I get when, as root, I run:

```
**1 -> gdisk -l /dev/sdb**  [same of course for /dev/sdc]
GPT fdisk (gdisk) version 1.0.10

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdb: 1000215216 sectors, 476.9 GiB
Model: Crucial_CT512M55
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 440FD21F-8A8B-43EB-8DA4-28A810D8CEB8
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1000215182
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       933593087   445.2 GiB   FD00  Linux RAID
   2       933593088      1000214527   31.8 GiB    FD00  Linux RAID
```

So it looks like these disks are actually MBR!  Memory grows dim over time.  Here is output from fdisk:

```
**2-> fdisk -l /dev/sdb**
Disk /dev/sdb: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: Crucial_CT512M55
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00036451

Device     Boot     Start        End   Sectors   Size Id Type
/dev/sdb1  *         2048  933593087 933591040 445.2G fd Linux raid autodetect
/dev/sdb2       933593088 1000214527  66621440  31.8G fd Linux raid autodetect
```

So now what?  Why am I having a problem upgrading this time?  Why is grub not installing just as it always has in the past?  What do you think I need to do next?

Again, thank you very much for helping me nail this down.

---

### Post by oldfred on 2024-10-13
Grub default install is to whatever drive is first.
First is defined by UEFI/BIOS on boot and may not always be the same.

With live installer you can specify drive for reinstall of grub, or use Boot-Repair & its advanced mode (it may default to first drive also with any auto fix).

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

The old BIOS install of grub from live installer just needed mount of / (/boot if separate) and install of grub.
But most instructions now are full chroot.
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
sudo mount /dev/sdXY /mnt  # where sdXY is / partition, 
sudo grub-install --boot-directory=/mnt/boot /dev/sdX  # where sdX is drive like sda, not partition
sudo update-grub
sudo update-initramfs -u -k

Full chroot, if BIOS, you do not mount esp:
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Another old BIOS chroot example:
[https://ubuntuforums.org/showthread.php?t=1285089&p=8068512#post8068512](https://ubuntuforums.org/showthread.php?t=1285089&p=8068512#post8068512)

---

### Post by cjsmall on 2024-10-14
Again, thank you for all the good information.

There is nothing I would like to do more than install the boot-repair utility and try to fix GRUB while I still have control of the machine but in following the instructions at [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/), when I get to the steps to:

sudo apt update
sudo apt install -y boot-repair

this fails because the current upgrade is still active.  Here is the output:

```
9-> sudo apt update
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock. It is held by process 2990920 (noble)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Unable to lock directory /var/lib/apt/lists/
```

The upgrade has the lock and it cannot be removed.  Is there any solution to this?  Being stuck in the middle of the upgrade, I've run out of ideas at this end.

As I indicated before, this Asus motherboard and BIOS predate UEFI and I checked the user guide and there was no mention of it anywhere.  Since all my previous upgrades were successful, I'm guessing that somewhere between 22.04 and 24.04 an assumption was made that all systems now supported it and this is why it is failing now.  (The same sort of thing happened with networking between 20.04 and 22.04!)

So I'll wait for any other suggestions you might have.  The next step is to continue the upgrade, reboot and see what happens.  If that fails, then I guess I'm going to have to reinstall the new OS from scratch using a bootable 24.04.1 ISO image on a thumb drive and then reconfigure everything from scratch -- a very unappealing idea!

---

### Post by oldfred on 2024-10-14
You at minimum should have good backup of /home, /etc, and list of installed apps. If any server apps like database or web those from / folders should also be backed up. Since RAID mounts, you may want to make backup of fstab, also. I edit grub, so copy those changes into /home so backed up as part of /home backup. But my system is a home desktop. Data on RAID separately should be backed up. RAID is not backup but for availability.

finish upgrade & then see if you can repair grub. Manually or with Boot-Repair.
Drive order may have changed, so upgrade is trying to install to one of the gpt drives and fails without the bios_grub partition.

#to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions

But you probably were booting from the MBR drives which do not need any added partitions as it uses MBR & space after MBR & before first partition. That space does not exist with gpt, so bios_grub then required.

Do you have this setting for grub to find correct drive to reinstall into? If you do & it is not, then a bug on installer. Not many using BIOS, so probably not well tested with the new installer.
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 
sudo debconf-show grub-pc

---

### Post by hifron on 2024-10-15
for backup list of installed apps(but only for view)
```
apt list|grep '\['installed'\]' >installed_apps.txt
```
reinstall them is more complicated like
```
dpkg ----get-selection
dpkg --set-selections
apt, snap list, flatpak

```

first try to run for pending:
```
dpkg --configure -a
```

it is also possible to remove lock and delete lock file, but installation should propose to get back to old installation - at least with ```
do-release-upgrade -d
```

backup of installed apps **is not fully operable again** because such apps have data, runtime data and configuration and sometimes also non-trivial setup and maybe also runtime configuration together with system setup..., but live-cd should have better option for that but installator changed between versions and if non-trivial setup or maybe even non-kernel addons(like kernel breaking zfs)..., then rebooting and gain new incompatible drivers(or newer filesystem) may brake things, but linux is full of complications, that happens that way... and before reboot you should have fully installed system(which could vary and even include oem install or active directory/entra id/open id login...)...

sometimes is hard but possible to boot from not fully installed system, but therefore is ubuntu-minimal and various boot level configs... and then manually repair broken or not fully installed system or its dependencies like broken gui setup, but that can be hard way to learn something new...

but when encrypted partitions, it is the way to loose data... another problem is long running disks and pc's when electronics could fail and not boot again after shutdown...

---

### Post by hifron on 2024-10-16
raid on 24.04 
[https://bugs.launchpad.net/ubuntu/+source/mdadm](https://bugs.launchpad.net/ubuntu/+source/mdadm)

new installator issue: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/2061964](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/2061964)

---

### Post by cjsmall on 2024-10-16
or22:

Thanks for the additional info regarding failure on raid.  In my case the md0 raid was comprised of sdb and sdc devices and when it came time to install GRUB, I got the message:

**GRUB failed to install to the following devices:  /dev/sdb  /dev/sdc**

After exploring every other option to try and recover from this failure, I finally decided to continue with the upgrade and, as expected, the system was unable to reboot.  So now i am going to have to reformat my SSDs and reinstall 24.04.1 from scratch, reinstall and reconfigure all packages, and then rebuild my mirror.  Wish me luck!  :-)

I certainly hope that these failures cause those responsible for the installer to improve things for the future.  Later, I'll add my comments to the bug thread.

---

### Post by oldfred on 2024-10-16
Just because grub likes to install/reinstall to "first" drive as defined by UEFI/BIOS, best to have boot drive as first drive.
That often is the lowest number SATA port, but external drives & NVMe may change that around.

---

