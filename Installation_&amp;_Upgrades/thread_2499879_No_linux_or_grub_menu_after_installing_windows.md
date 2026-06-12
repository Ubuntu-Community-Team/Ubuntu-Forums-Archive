---
title: "No linux or grub menu after installing windows"
date: 2024-08-14
forum: Installation &amp; Upgrades
---

### Post by vbdanl-yahoo on 2024-08-14
Hi, after installing windows 10 my grub menu went away and it only boots to windows.
I have to use windows for dual monitors when i rdp into work, at least until i can get remmina to do the same.
i have tried several fixes, but can't seem to get this fixed.  I have also read many posts that were similar, but not quite the same.
i was thinking of using gparted and removing /dev/sda1 and/or reformat it to ext4 instead of HPFS/NTFS/exFAT
and then seeing if i could reinstall grub2.  At the bottom of this it sounds like they suggest doing this and putting in a 200mb /boot partition.
i did run some fixntfs thing and it seemed to work, but i still could not mount /dev/sda1 from the live usb - it says it is busy or held by something..sorry did not write it down.

Thanks for any and all help, i really appreciate it.

Here is the output from Boot Info Summary.
```

boot-repair-4ppa2079                                              [20240814_0154]


============================== Boot Info Summary ===============================


 => Windows is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda4: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


sda6: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


sda7: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb: ___________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.
       dmesg(1) may have more information after failed mount system call.




================================ 4 OS detected =================================


OS#1:   Windows 10 (boot) on sda1
OS#2:   Ubuntu 22.04.4 LTS on sda5
OS#3:   Ubuntu 24.04 LTS on sda6
OS#4:   Windows 10 or 11 on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: 4 Series Chipset Integrated Graphics Controller 4 Series Chipset Integrated Graphics Controller from Intel Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 24.04 LTS, noble, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 786G7 v01.02(1.2) from Hewlett-Packard
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).






============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda2	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda3	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda5	: is-os,	64, apt-get,	grub-pc ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB
sda6	: is-os,	64, apt-get,	grub-pc ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB


Partitions info (2/3): _________________________________________________________


sda1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot
sda2	: isnotESP,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda3	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda5	: isnotESP,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda6	: isnotESP,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda2	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda3	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda5	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	customized,	sda
sda6	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 232.89 GiB, 250059350016 bytes, 488397168 sectors
Disk identifier: 0x56e5fd8d
     Boot     Start       End   Sectors   Size Id Type
sda1  *         2048   1025999   1023952   500M  7 HPFS/NTFS/exFAT
sda2         1026048 290805759 289779712 138.2G  7 HPFS/NTFS/exFAT
sda3       487413760 488370175    956416   467M 27 Hidden NTFS WinRE
sda4       290807806 487413759 196605954  93.7G  5 Extended
sda5       290807808 385014839  94207032  44.9G 83 Linux
sda6       385017856 477177855  92160000  43.9G 83 Linux
sda7       477179904 487413759  10233856   4.9G 82 Linux swap / Solaris
Partition table entries are not in disk order.
Disk sdb: 14.46 GiB, 15522070528 bytes, 30316544 sectors
Disk identifier: 1CF7D054-8DB5-4194-971E-3C8665684807
        Start      End  Sectors  Size Type
sdb1        64 11931883 11931820  5.7G Microsoft basic data
sdb2  11931884 11942023    10140    5M EFI System
sdb3  11942024 11942623      600  300K Microsoft basic data
sdb4  11943936 30314495 18370560  8.8G Linux filesystem


parted -lm (filtered): _________________________________________________________


sda:250GB:scsi:512:512:msdos:ATA WDC WD2500AAKX-7:;
1:1049kB:525MB:524MB:ntfs::boot;
2:525MB:149GB:148GB:ntfs::;
4:149GB:250GB:101GB:::;
5:149GB:197GB:48.2GB:ext4::;
6:197GB:244GB:47.2GB:ext4::;
7:244GB:250GB:5240MB:linux-swap(v1)::swap;
3:250GB:250GB:490MB:ntfs::msftres;
sdb:15.5GB:scsi:512:512:gpt:SanDisk Cruzer Glide:;
1:32.8kB:6109MB:6109MB::ISO9660:hidden, msftdata;
2:6109MB:6114MB:5192kB::Appended2:boot, esp;
3:6114MB:6115MB:307kB::Gap1:hidden, msftdata;
4:6115MB:15.5GB:9406MB:ext4::;


Free space >10MiB: ______________________________________________________________


sda: 238462MiB:238475MiB:13.2MiB


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9500;&#9472;sda1 ntfs     B67033B770337CE5                     56e5fd8d-01                          System Reserved        
&#9500;&#9472;sda2 ntfs     448E19C38E19AF04                     56e5fd8d-02                                                 
&#9500;&#9472;sda3 ntfs     59EB268810F57933                     56e5fd8d-03                                                 
&#9500;&#9472;sda4                                               56e5fd8d-04                                                 
&#9500;&#9472;sda5 ext4     65788683-e57d-4e20-97b0-c9d5175105cc 56e5fd8d-05                                                 
&#9500;&#9472;sda6 ext4     254db3e4-4e17-46d6-914b-fdb0db27af51 56e5fd8d-06                                                 
&#9492;&#9472;sda7 swap     ca819687-4fdd-4c45-a317-2e662ba9a35b 56e5fd8d-07                                                 
sdb    iso9660  2024-04-24-11-29-09-00                                                    Ubuntu 24.04 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2024-04-24-11-29-09-00               1cf7d054-8db5-4194-971f-3c8665684807 Ubuntu 24.04 LTS amd64 ISO9660
&#9500;&#9472;sdb2 vfat     37B6-BC6E                            1cf7d054-8db5-4194-971c-3c8665684807 ESP                    Appended2
&#9500;&#9472;sdb3                                               1cf7d054-8db5-4194-971d-3c8665684807                        Gap1
&#9492;&#9472;sdb4 ext4     bed92933-4bd3-4d80-8deb-00583de9b5a5 265828a9-4520-4ff5-95f1-9f51d37fb482 writable               


Mount points (filtered): _______________________________________________________


                                                               Avail Use% Mounted on
/dev/sda1                                                     467.2M   7% /mnt/boot-sav/sda1
/dev/sda2                                                     101.2G  27% /mnt/boot-sav/sda2
/dev/sda3                                                     456.5M   2% /mnt/boot-sav/sda3
/dev/sda5                                                       9.7G  73% /mnt/boot-sav/sda5
/dev/sda6                                                      23.5G  40% /mnt/boot-sav/sda6
/dev/sdb1                                                          0 100% /cdrom


Mount options (filtered): ______________________________________________________


/dev/sda1                                                     fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda2                                                     fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda3                                                     fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5                                                     ext4            rw,relatime
/dev/sda6                                                     ext4            rw,relatime
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8


====================== sda5/boot/grub/grub.cfg (filtered) ======================


Ubuntu 22.04 jammy (on sda5)   65788683-e57d-4e20-97b0-c9d5175105cc
Windows 10 (on sda1)   B67033B770337CE5
Ubuntu 24.04 LTS (24.04) (on sda6)   254db3e4-4e17-46d6-914b-fdb0db27af51
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sda5/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=65788683-e57d-4e20-97b0-c9d5175105cc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ca819687-4fdd-4c45-a317-2e662ba9a35b none            swap    sw              0       0


======================= sda5/etc/default/grub (filtered) =======================


GRUB_DEFAULT="Ubuntu 22.04 jammy (on /dev/sda5)"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE="1024x768"
GRUB_SAVEDEFAULT="false"
export GRUB_MENU_PICTURE="/home/dan/Documents/Wallpaper/linuxissexy.jpg"
export GRUB_COLOR_NORMAL="light-cyan/black"
export GRUB_COLOR_HIGHLIGHT="yellow/black"


==================== sda5: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 152.523918152 = 163.771310080  boot/grub/grub.cfg                             1
 152.478511810 = 163.722555392  boot/grub/i386-pc/core.img                     1
 183.535152435 = 197.069369344  boot/vmlinuz                                   2
 173.652339935 = 186.457780224  boot/vmlinuz-5.15.0-117-generic                8
 183.535152435 = 197.069369344  boot/vmlinuz-5.15.0-118-generic                2
 173.652339935 = 186.457780224  boot/vmlinuz.old                               8
 155.526973724 = 166.995816448  boot/initrd.img                               86
 158.838088989 = 170.551099392  boot/initrd.img-5.15.0-117-generic            205
 155.526973724 = 166.995816448  boot/initrd.img-5.15.0-118-generic            86
 158.838088989 = 170.551099392  boot/initrd.img.old                           205


===================== sda5: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root   733 Nov 24  2023 10_linux_proxy
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Mar  4  2018 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom
drwxr-xr-x 4 root root  4096 Apr 22  2020 backup
drwxr-xr-x 2 root root  4096 Dec 25  2022 bin
drwxr-xr-x 2 root root  4096 Nov 24  2023 proxifiedScripts


====================== sda6/boot/grub/grub.cfg (filtered) ======================


Ubuntu   254db3e4-4e17-46d6-914b-fdb0db27af51
Windows 10 (on sda1)   B67033B770337CE5
Ubuntu 22.04.4 LTS (22.04) (on sda5)   65788683-e57d-4e20-97b0-c9d5175105cc
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda6/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during curtin installation
/dev/disk/by-uuid/254db3e4-4e17-46d6-914b-fdb0db27af51 / ext4 defaults 0 1
/swap.img	none	swap	sw	0	0


======================= sda6/etc/default/grub (filtered) =======================


GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
export GRUB_MENU_PICTURE="/home/dan/Pictures/linuxissexy.jpg"
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-cyan/black"
==================== sda6: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 207.959140778 = 223.294427136  boot/grub/grub.cfg                             1
 195.719142914 = 210.151829504  boot/grub/i386-pc/core.img                     1
 188.370361328 = 202.261135360  boot/vmlinuz                                   1
 188.370361328 = 202.261135360  boot/vmlinuz-6.8.0-40-generic                  1
 188.370361328 = 202.261135360  boot/vmlinuz.old                               1
 186.761375427 = 200.533499904  boot/initrd.img                                2
 186.761375427 = 200.533499904  boot/initrd.img-6.8.0-40-generic               2
 186.761375427 = 200.533499904  boot/initrd.img.old                            2


===================== sda6: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 10:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5 11:36 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4 10:12 40_custom
-rwxr-xr-x 1 root root   215 Apr  4 10:12 41_custom
drwxr-xr-x 4 root root  4096 Aug 11 20:15 backup


======================== Unknown MBRs/Boot Sectors/etc =========================


Unknown BootLoader on sda3




mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2 




Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would purge (in order to fix grub.d) and reinstall the grub2 of
sda5 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s win-legacy-basic-fix


Final advice in case of suggested repair: ______________________________________




The boot files of [sda5 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. 

```
([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by ActionParsnip on 2024-08-14
Yep, the windows installer is garbage and just writes it's own bootloader. You need to chroot to the installed Ubuntu from live CD/USB then reinstate GRUB to the disk, then add Windows.

---

### Post by yancek on 2024-08-14
You did a Legacy install of Ubuntu which is also what your windows is and the simple solution is to do a Legacy reinstall of Grub to the MBR of the device.  As you can see from boot repair, windows code is installed in the MBR of this device and a standard windows can't boot LInux.  There are methods to do this with earlier versions of windows but I don't know that they will work with windows 10.  I'd do that to see if it works before trying to create a boot partition near the beginning of the drive as that will require modifying the partitions on which you have windows installed and will likely create greater problems if you are not familiar with the process.

---

### Post by vbdanl-yahoo on 2024-08-14
not sure i did what you said to do, but what i did didn't work..
sudo mount /dev/sda6 /mnt  (works)
sudo update-grub  (/usr/sbin/grub-probe: error: failed to get canonical path of '\cow'
i remember someone saying cow errors are because its trying to update the live usb instead of hd..
looked at the grub2 installing instructions closer, and ran the following..
buntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt/$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
root@ubuntu:/# update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
using custom appearance settings
Found background image: /home/dan/Pictures/linuxissexy.jpg
Found linux image: /boot/vmlinuz-6.8.0-40-generic
Found initrd image: /boot/initrd.img-6.8.0-40-generic
Found memtest86+x64 image: /boot/memtest86+x64.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 10 on /dev/sda1
Found Ubuntu 22.04.4 LTS (22.04) on /dev/sda5
Adding boot menu entry for UEFI Firmware Settings ...
done
root@ubuntu:/# 
exit
ubuntu@ubuntu:~$
hopefully this will take care of it.
thanks for your help.

---

### Post by vbdanl-yahoo on 2024-08-14
thanks for your response.  i did what ActionParsnip suggested, and it worked.  am back in business.  thanks yancek !!

---

### Post by vbdanl-yahoo on 2024-08-14
the instructions i wrote above worked and am going again.
Thanks so much !!
looking for how to mark this as Solved..

---

