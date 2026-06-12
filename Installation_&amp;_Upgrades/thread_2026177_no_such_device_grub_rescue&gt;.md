---
title: "no such device: grub rescue&gt;"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by keromina on 2012-07-14
I just tried installing ubuntu on a usb drive using windows installer. During the installation process there was a message that said you will have to manually install boot loader but i continued with the installation anyway. Now once I open my computer i get an error message: 
no such device: d9884ff6-...
grub rescue>

How can I solve this issue? Please I'm in urgent need.

---

### Post by coffeecat on 2012-07-15
Welcome to the forum.

Just to be sure I have understood you correctly - you used the wubi installer to try to install a wubi version of Ubuntu to an external USB drive? (I'm not sure whether that is possible.) Is that correct? Or do you mean that you used Windows to create a bootable USB version of Ubuntu? If so, what Windows app did you use?

The message you are getting is the grub bootloader saying that it cannot find a certain partition with the quoted UUID, except that the UUID appears to be truncated.

Question: do you get that message when you try to boot with the USB drive plugged in, or do you get that message when you try to boot Windows without the USB drive plugged in? Can you still boot Windows?

---

### Post by keromina on 2012-07-15
I get this error message regardless of wheter or not the usb drive is plugged in. I cannot boot windows any longer. The installer i used was the one found on the ubuntu download page with instructions to download onto the computer hard drive, but when i saw the option on the scroll down list for my usb hard drive i downloaded to that instead.

---

### Post by coffeecat on 2012-07-15
Was this the page you downloaded the installer from?

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

If so, you did use the wubi installer, but somehow you've managed to install the grub bootloader to the mbr of your main hard drive, which is not appropriate for a wubi install.

You will need to re-install the Windows boot code to the mbr in order to boot Windows. This is fairly easily done but requires either a Microsoft installation disc (a manufacturer's OEM restore disc will not do) or an Ubuntu live CD. I can take you through how to re-install the Windows bootloader with an Ubuntu CD, but first, which version of Windows are you running? Do you have a Microsoft installation CD/DVD for the version of Windows you have. If you are running Windows 7 and do not have a Microsoft disc, have you access to another installation of Windows 7?

---

### Post by keromina on 2012-07-15
Yes that's the page. I am running windows 7 but have lost the installation discs. Also I cannot acquire access to another installation of windows7 for some time. However, I have made an Ubuntu live cd.
Thank you very much..

---

### Post by coffeecat on 2012-07-16
> **keromina said:**
> However, I have made an Ubuntu live cd.
Thank you very much..

That's helpful. Before you re-install the Windows mbr (or equivalent), I suggest you run the boot info script so that we can see exactly what the situation is with your setup and partitions. I'm somewhat concerned that grub in your mbr is looking for a partition that it cannot see, and I think we need to see precisely what is going on. Boot up the live Ubuntu CD, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page, but see the comment below - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar. Run the boot info script with the external USB drive with Ubuntu on plugged in.

There is a currently uncorrected error in the command on that instruction page. The script file is now called bootinfoscript, not boot_info_script.sh. Once you have moved it to the live desktop, the command should be:

```
sudo bash ~/Desktop/bootinfoscript
```

I'll give you a link to how to install Windows boot code to the mbr, but I suggest you delay using that until we have seen the output of bootinfoscript.

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

Each of those three methods works well.

---

### Post by keromina on 2012-07-20
the code 
 
```
sudo bash ~/Desktop/bootinfoscript
```
 
is not working for me. I get a message saying 'NO SUCH FILE OR DIRECTORY'

---

### Post by coffeecat on 2012-07-20
> **keromina said:**
> the code 
 
```
sudo bash ~/Desktop/bootinfoscript
```
 
is not working for me. I get a message saying 'NO SUCH FILE OR DIRECTORY'

You need to extract the downloaded tar.gz and then move the bootinfoscript file to the desktop.

---

### Post by YannBuntu on 2012-07-20
Hello
See also [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by keromina on 2012-07-23
> **coffeecat said:**
> You need to extract the downloaded tar.gz and then move the bootinfoscript file to the desktop.

I did that but for some reason I still kept getting the same error. 

I went ahead and used yannabuntu's boot repair, and this is the boot info summary from there:

[http://paste.ubuntu.com/1102910/](http://paste.ubuntu.com/1102910/)

Now when I boot my computer it gives me an option between booting to windows or ubuntu, and then it automatically chooses windows after a few seconds. I was wondering how I can restore the original windows mbr and take off this feature. 

Thank you again.

---

### Post by coffeecat on 2012-07-23
First thing - I'll repost your output from boot repair because your Ubuntu Pastebin page may expire before this is solved. To be honest I can't remember how long pastebin stuff is kept, but to be sure it's still available, here it is:

```
 Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info 20 July 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of 
    /dev/mapper/isw_cegegijada_Volume0 and looks at sector 1 of the same hard 
    drive for core.img. core.img is at this location and looks in partition 
    256 for /boot/grub.

isw_cegegijada_Volume01: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

isw_cegegijada_Volume02: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cegegijada_Volume03: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: isw_cegegijada_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_cegegijada_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cegegijada_Volume01              2,048    27,418,623    27,416,576  27 Hidden NTFS (Recovery Environment)
/dev/mapper/isw_cegegijada_Volume02   *     27,418,624    27,623,423       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_cegegijada_Volume03         27,623,424   250,079,231   222,455,808   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_cegegijada_Volume0p1 3C66A91466A8D046                       ntfs       Recovery
/dev/mapper/isw_cegegijada_Volume0p2 1030D60E30D5FAA4                       ntfs       System Reserved
/dev/mapper/isw_cegegijada_Volume0p3 52ACD6EEACD6CC1B                       ntfs       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_cegegijada_Volume0
isw_cegegijada_Volume0p1
isw_cegegijada_Volume0p2
isw_cegegijada_Volume0p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_cegegijada_Volume01


Unknown BootLoader on isw_cegegijada_Volume02


Unknown BootLoader on isw_cegegijada_Volume03



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/isw_cegegijada_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cegegijada_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cegegijada_Volume02: No such file or directory
hexdump: /dev/mapper/isw_cegegijada_Volume02: No such file or directory
hexdump: /dev/mapper/isw_cegegijada_Volume03: No such file or directory
hexdump: /dev/mapper/isw_cegegijada_Volume03: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-07-20__15h01 ===================
boot-repair version : 3.18-0ppa42~precise
boot-sav version : 3.191-0ppa60~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa10~precise
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 357 not upgraded.
dpkg-preconfigure: unable to re-open stdin: No such file or directory

BLKID BEFORE RAID ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Ubuntu 12.04 LTS i386" TYPE="iso9660"
/dev/sda: TYPE="isw_raid_member"
/dev/sdb: TYPE="isw_raid_member"
/dev/mapper/isw_cegegijada_Volume0p1: LABEL="Recovery" UUID="3C66A91466A8D046" TYPE="ntfs"
/dev/mapper/isw_cegegijada_Volume0p2: LABEL="System Reserved" UUID="1030D60E30D5FAA4" TYPE="ntfs"
/dev/mapper/isw_cegegijada_Volume0p3: UUID="52ACD6EEACD6CC1B" TYPE="ntfs"
dmraid -si -c:
dmraid -ay:
RAID set "isw_cegegijada_Volume0" already active
RAID set "isw_cegegijada_Volume0p1" already active
RAID set "isw_cegegijada_Volume0p2" already active
RAID set "isw_cegegijada_Volume0p3" already active
dmraid -sa -c: isw_cegegijada_Volume0
grub-probe: error: out of memory.
grub-probe: error: out of memory.
grub-probe: error: out of memory.
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , i686)
CPU op-mode(s):        32-bit, 64-bit
[dmraid -sa -c] isw_cegegijada_Volume0
[dmraid -sa -c] isw_cegegijada_Volume0
[dmraid -sa -c] isw_cegegijada_Volume0
ls: cannot access /sys/block/mapper/isw_cegegijada_Volume0/: No such file or directory
Disk /dev/sdb doesn't contain a valid partition table

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Ubuntu 12.04 LTS i386" TYPE="iso9660"
/dev/sda: TYPE="isw_raid_member"
/dev/sdb: TYPE="isw_raid_member"
/dev/mapper/isw_cegegijada_Volume0p1: LABEL="Recovery" UUID="3C66A91466A8D046" TYPE="ntfs"
/dev/mapper/isw_cegegijada_Volume0p2: LABEL="System Reserved" UUID="1030D60E30D5FAA4" TYPE="ntfs"
/dev/mapper/isw_cegegijada_Volume0p3: UUID="52ACD6EEACD6CC1B" TYPE="ntfs"

Windows not detected by os-prober on mapper/isw_cegegijada_Volume0p3.

sfdisk: ERROR: sector 0 does not have an msdos signature
/dev/sdb: unrecognized partition table type
No partitions found
Disk /dev/sdb doesn't contain a valid partition table

=================== dmesg | grep EFI :
BIOS is probably not EFI-compatible, and probably not setup in EFI-mode for this live-session.
[    3.835362] EFI Variables Facility v0.08 2004-May-17



=================== PARTITIONS & DISKS:
mapper/isw_cegegijada_Volume0p1	: mapper/isw_cegegijada_Volume0,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	no-grldr,	boot/bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/mapper/isw_cegegijada_Volume0p1, .
mapper/isw_cegegijada_Volume0p2	: mapper/isw_cegegijada_Volume0,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	no-grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/mapper/isw_cegegijada_Volume0p2, .
mapper/isw_cegegijada_Volume0p3	: mapper/isw_cegegijada_Volume0,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/mapper/isw_cegegijada_Volume0p3, .

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes
sdb	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes
mapper/isw_cegegijada_Volume0	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes

=================== parted -l:


                                                                          
Error: Can't have a partition outside the disk!


                                                                          
Error: /dev/sdb: unrecognised disk label

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cegegijada_Volume0p3: 114GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
1      0.00B  114GB  114GB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cegegijada_Volume0p2: 105MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
1      0.00B  105MB  105MB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cegegijada_Volume0p1: 14.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  14.0GB  14.0GB  ntfs


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_cegegijada_Volume0: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  14.0GB  14.0GB  primary  ntfs         diag
2      14.0GB  14.1GB  105MB   primary  ntfs         boot
3      14.1GB  128GB   114GB   primary  ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
grub-mount on /var/lib/os-prober/mount type fuse.grub-mount (rw,nosuid,nodev)
/dev/mapper/isw_cegegijada_Volume0p1 on /mnt/boot-sav/mapper/isw_cegegijada_Volume0p1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/mapper/isw_cegegijada_Volume0p2 on /mnt/boot-sav/mapper/isw_cegegijada_Volume0p2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/mapper/isw_cegegijada_Volume0p3 on /mnt/boot-sav/mapper/isw_cegegijada_Volume0p3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-2 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-3 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-4 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dm-0 dm-2 dm-3 dm-4 dri dvd dvdrw ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb serial sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 v4l vga_arbiter video0 zero
ls /dev/mapper:  control isw_cegegijada_Volume0 isw_cegegijada_Volume0p1 isw_cegegijada_Volume0p2 isw_cegegijada_Volume0p3
ls /mnt/boot-sav/mapper/isw_cegegijada_Volume0p3: wubildr.mbr wubildr WirelessDiagLog.csv Windows Contents Sample VAIO Entertainment VAIO Users Update test.xml Temp Information Volume System RHDSetup.log $Recycle.Bin (x86) Files Program Files Program ProgramData PerfLogs pagefile.sys MSOCache MemeoSendAddin Intel hosts hiberfil.sys Settings and Documents Config.Msi bdlog.txt _AcroTemp a23ac562e59d88c25da83f
Disk /dev/sdb doesn't contain a valid partition table

=================== df -Th:

Filesystem                           Type             Size  Used Avail Use% Mounted on
/cow                                 overlayfs        1.9G  220M  1.6G  12% /
udev                                 devtmpfs         1.8G   12K  1.8G   1% /dev
tmpfs                                tmpfs            739M  960K  738M   1% /run
/dev/sr0                             iso9660          702M  702M     0 100% /cdrom
/dev/loop0                           squashfs         673M  673M     0 100% /rofs
tmpfs                                tmpfs            1.9G   28K  1.9G   1% /tmp
none                                 tmpfs            5.0M  4.0K  5.0M   1% /run/lock
none                                 tmpfs            1.9G  176K  1.9G   1% /run/shm
grub-mount                           fuse.grub-mount  1.9G  220M  1.6G  12% /var/lib/os-prober/mount
/dev/mapper/isw_cegegijada_Volume0p1 fuseblk           14G   13G  829M  94% /mnt/boot-sav/mapper/isw_cegegijada_Volume0p1
/dev/mapper/isw_cegegijada_Volume0p2 fuseblk          100M   26M   75M  26% /mnt/boot-sav/mapper/isw_cegegijada_Volume0p2
/dev/mapper/isw_cegegijada_Volume0p3 fuseblk          107G   63G   44G  59% /mnt/boot-sav/mapper/isw_cegegijada_Volume0p3

=================== fdisk -l:

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc1de34f9

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27418623    13708288   27  Hidden NTFS WinRE
/dev/sda2   *    27418624    27623423      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27623424   250079231   111227904    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/isw_cegegijada_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0xc1de34f9

Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cegegijada_Volume0p1            2048    27418623    13708288   27  Hidden NTFS WinRE
/dev/mapper/isw_cegegijada_Volume0p2   *    27418624    27623423      102400    7  HPFS/NTFS/exFAT
/dev/mapper/isw_cegegijada_Volume0p3        27623424   250079231   111227904    7  HPFS/NTFS/exFAT

Disk /dev/mapper/isw_cegegijada_Volume0p1: 14.0 GB, 14037286912 bytes
255 heads, 63 sectors/track, 1706 cylinders, total 27416576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cegegijada_Volume0p1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p1p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p1p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p1p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_cegegijada_Volume0p2: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cegegijada_Volume0p2p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p2p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p2p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p2p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_cegegijada_Volume0p3: 113.9 GB, 113897373696 bytes
255 heads, 63 sectors/track, 13847 cylinders, total 222455808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cegegijada_Volume0p3p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p3p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p3p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cegegijada_Volume0p3p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order


Disk /dev/sdb doesn't contain a valid partition table
Partition outside the disk detected.

=================== Recommended repair
recommendedrepair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on .
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/ set  boot on

                                                                          
Warning: Unable to open /dev read-write (Is a directory).  /dev has been opened
read-only.

                                                                          
Warning: Unable to open /dev read-write (Is a directory).  /dev has been opened
read-only.

                                                                          
Error: /dev: unrecognised disk label

Boot successfully repaired.

You can now reboot your computer.

pastebinit  packages needed
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dpkg-preconfigure: unable to re-open stdin: No such file or directory
cp: cannot create regular file ` /var/log/boot-sav/log/2012-07-20__15h01boot-repair55/sources_': No such file or directory

```

Second: it looks as though you have a RAID array, and I have little or no experience of RAID. I would normally post the very easy way of re-installing Windows boot code to the mbr using an Ubuntu CD - in fact I have already posted a link in post #6 - but I'm not 100% sure this would be appropriate with RAID. I'll ask someone else to have a look.

**EDIT**: in fact near the end of your boot repair output is evidence of boot repair attempting one of the mbr repairs and failing.

---

### Post by oldfred on 2012-07-23
I really do not know RAID either and Boot_Repair automatically adds the dmraid driver to see RAID partitions that the liveCD does not normally see.

But script is reporting issues with sdb.

> /dev/sdb: unrecognized partition table type
No partitions found
I do not know the details to repair a broken RAID.

---

### Post by darkod on 2012-07-23
> **keromina said:**
> I did that but for some reason I still kept getting the same error. 

I went ahead and used yannabuntu's boot repair, and this is the boot info summary from there:

[http://paste.ubuntu.com/1102910/](http://paste.ubuntu.com/1102910/)

Now when I boot my computer it gives me an option between booting to windows or ubuntu, and then it automatically chooses windows after a few seconds. I was wondering how I can restore the original windows mbr and take off this feature. 

Thank you again.

So, it can boot into windows if you let it boot by default?

In that case, you can make a rescue cd and use that to repair the bootloader, in other words to install win7 bootloader to the MBR of the array.

You never mentioned that you are running raid from the start. I am not sure if wubi would work correctly on a raid, it should, but can't say for sure especially since I don't use wubi.
In case you do want to install ubuntu as dual boot (not wubi), you will need to shrink one of the ntfs partitions first to make unallocated space, and then use the alternate install cd to install ubuntu, not the standard live cd. This is very important for raid. There are ways to make it work with the live cd, but additional steps are needed to install grub2. The choice is yours.

---

### Post by YannBuntu on 2012-07-28
Hello

- the RAID seems correctly activated:

```
dmraid -ay:
RAID set "isw_cegegijada_Volume0" already active
RAID set "isw_cegegijada_Volume0p1" already active
RAID set "isw_cegegijada_Volume0p2" already active
RAID set "isw_cegegijada_Volume0p3" already active
```

- the "Recommended repair" is failing because os-prober detects no OS. I'll have to improve B-R for this case.

- to remove the grub menu, you can restore a generic MBR in the MBR of the array. Eg run Boot-Repair, click "Advanced options", tick the "Restore MBR" option, go to the "MBR options" tab, select: "Restore the MBR of: mapper/isw_cegegijada_Volume0" and "Partition booted by the MBR: mapper/isw_cegegijada_Volume0**p2**"
apply.

(@coffeecat: for information i have never seen any paste.ubuntu.com URL disappearing. For example [here]("http://paste.ubuntu.com/663531/") is one which was created in August 2011.)

---

