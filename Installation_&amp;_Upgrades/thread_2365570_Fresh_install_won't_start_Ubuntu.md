---
title: "Fresh install won't start Ubuntu"
date: 2017-07-07
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2017-07-07
Hi all,

All I get is the text line below. And it won't continue.

```
/dev/sdb3: clean, 223914/19558489 files, 3564666/46000000 blocks
``` (with a black background)

I will use the Ubuntu Live USB drive to run some commands to gather more info on the partitions for you to see what's going on.
I will use these commands:

[FONT=&amp]**df –h**[/FONT]
[FONT=&amp]**sudo lsblk -fm**[/FONT]
[FONT=&amp][B]sudo parted -l

[/B][FONT=arial]Hopefully the text line above already tells you enough to know what should be my next step.[/FONT][/FONT]

---

### Post by yancek on 2017-07-07
It's just telling you that a filesystem check was run and found no problems so posting the output of the above commands and some info on your hardware would help.  Did it ever boot successfully?

---

### Post by javierdl on 2017-07-07
Hi yancek,

Thanks for joining the thread :)

Nothing has changed so far.

Here's some drives/partitions info:

I chose sdb3 to install Ubuntu. I had formatted it as Ext4 prior to install.

```


df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.7M  1.6G   1% /run
/dev/sdd         30G  2.5G   28G   9% /cdrom
/dev/loop0      1.4G  1.4G     0 100% /rofs
aufs            7.9G  3.7M  7.9G   1% /
tmpfs           7.9G  152K  7.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs           7.9G  4.0K  7.9G   1% /tmp
tmpfs           1.6G   64K  1.6G   1% /run/user/999
/dev/sdc1       1.9T  679G  1.2T  37% /media/ubuntu/TOSHIBA
ubuntu@ubuntu:~$ lsblk -fm
NAME   FSTYPE  LABEL   UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sdd    vfat    lexar32 59AE-C2F5                            /cdrom     sdd     29.8G root  disk  brw-rw----
sdb                                                                    sdb    931.5G root  disk  brw-rw----
&#9500;&#9472;sdb4 ext4    Files   20314bbe-a51e-4e2e-b6b1-0dabcfa32524            &#9500;&#9472;sdb4 350.7G root  disk  brw-rw----
&#9500;&#9472;sdb2 ext4            3ff8f52b-26d0-415f-b890-9ed186c00c5b            &#9500;&#9472;sdb2 279.4G root  disk  brw-rw----
&#9500;&#9472;sdb5 swap            e863d0f6-0ab2-4f1f-9fa3-55a652b02283 [SWAP]     &#9500;&#9472;sdb5     8G root  disk  brw-rw----
&#9500;&#9472;sdb3 ext4            567a1751-4c64-4a01-a5fe-e4e5e56a78d3            &#9500;&#9472;sdb3   293G root  disk  brw-rw----
&#9492;&#9472;sdb1 vfat            D45B-1044                                       &#9492;&#9472;sdb1   512M root  disk  brw-rw----
loop0  squashf                                              /rofs      loop0    1.4G root  disk  brw-rw----
sdc                                                                    sdc      1.8T root  disk  brw-rw----
&#9492;&#9472;sdc1 ntfs    TOSHIBA A46CE4BB6CE488FE                     /media/ubu &#9492;&#9472;sdc1   1.8T root  disk  brw-rw----
sda                                                                    sda    111.8G root  disk  brw-rw----
&#9500;&#9472;sda4 ntfs            D61C80691C804709                                &#9500;&#9472;sda4 111.2G root  disk  brw-rw----
&#9500;&#9472;sda2 vfat            147B-374C                                       &#9500;&#9472;sda2   100M root  disk  brw-rw----
&#9500;&#9472;sda3                                                                 &#9500;&#9472;sda3    16M root  disk  brw-rw----
&#9492;&#9472;sda1 ntfs    Recovery
                       5E447AFB447AD56D                                &#9492;&#9472;sda1   450M root  disk  brw-rw----
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Patriot Torch LE (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  473MB  472MB   ntfs         Basic data partition          hidden, diag
 2      473MB   578MB  105MB   fat32        EFI system partition          boot, esp
 3      578MB   595MB  16.8MB               Microsoft reserved partition  msftres
 4      595MB   120GB  119GB   ntfs         Basic data partition          msftdata




Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name   Flags
 1      1049kB  538MB   537MB   fat32           EF     boot, esp
 2      538MB   301GB   300GB   ext4            Steam
 3      301GB   615GB   315GB   ext4                   msftdata
 4      615GB   992GB   377GB   ext4
 5      992GB   1000GB  8523MB  linux-swap(v1)         diag




Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start  End     Size    Type     File system  Flags
 1      106MB  2000GB  2000GB  primary  ntfs




Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdd: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  32.0GB  32.0GB  fat32




ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 3B8A37AC-349D-43AC-A50E-221B3D9B64E2


Device       Start       End   Sectors   Size Type
/dev/sda1     2048    923647    921600   450M Windows recovery environment
/dev/sda2   923648   1128447    204800   100M EFI System
/dev/sda3  1128448   1161215     32768    16M Microsoft reserved
/dev/sda4  1161216 234440703 233279488 111.2G Microsoft basic data




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identif


```

---

### Post by yancek on 2017-07-07
You have windows on the 120GB drive with an EFI partition.  You have Ubuntu on the 1TB drive which also has an EFI partition.  Are you able to boot Ubuntu when you select the 1TB drive on boot or by setting it to first boot priority?  Ubuntu usually installs it's EFI files to the first drive so I would start by mounting sda2 to check for an ubuntu directory and then repeat for sdb1.  If you can boot Ubuntu, open a terminal and run the command:  sudo efibootmgr  That should output some info on boot options and priority.

---

### Post by javierdl on 2017-07-07
> [COLOR=#000000]Are you able to boot Ubuntu when you select the 1TB drive on boot or by setting it to first boot priority? [/COLOR]
I am using [Tux4Ubuntu]("https://tux4ubuntu.blogspot.ca/2016/12/tuxedo-up-for-new-year.html") Boot Loader. Is based on rEFInd. I have it selected as my 1st booting option in the BIOS. I hope this addresses your question.

> [COLOR=#000000]Ubuntu usually installs it's EFI files to the first drive[/COLOR]
Well, I am pretty sure the installer actually asked me where exactly to install the booting files (as opposed to choosing the best place on its own). Unfortunately I don't recall what I chose :(

> [COLOR=#000000]I would start by mounting sda2 to check for an ubuntu directory and then repeat for sdb1. [/COLOR]
Just as long as it's an Ubuntu directory is enough? Or does it have to have certain subdirectories/files?

> [COLOR=#000000]If you can boot Ubuntu, open a terminal and run the command: sudo efibootmgr That should output some info on boot options and priority.[/COLOR]
Would this work from a Live USB? That's the only way I can run Ubuntu so far.

Thanks

---

### Post by yancek on 2017-07-08
I don't know what Tux4Ubuntu is and have never used rEFind so can't help with that.  If you selected to install the efi files for Ubuntu to the 1TB drive, I expect you would need to select that drive under the boot options from the BIOS on boot to boot Ubuntu.  Since the various manufacturers have very different ways to access and change the BIOS settings it is not possible to tell you speifically how to do it. 

On my system, when I mount the efi partition which is sda1, there is an EFI directory with several sub-directories including one name ubuntu.  In the ubuntu directory I have the following and I expect you would or should see them.

> bootx64.efi*  fbx64.efi*  fw/  fwupx64.efi*  grub.cfg*  grubx64.efi*  mmx64.efi*  shimx64.efi*


Boot the Ubuntu from the flash drive and create a mount point for sdb1, the Ubuntu drive EFI partition:  sudo mkdir /mnt/sdb1
Then mount it:  sudo mount /dev/sdb1 /mnt/sdb1  and check for the files.  If they arent' there, repeat the process substituting sda2 in the commands above for sdb1 and check for an ubuntu directory.

You need to boot the flash drive UEFI in order to run the efibootmgr command.  You should see a black screen with white text which tells you it is booting UEFI.  On boot, you should have a specific key for your system for boot options.  When I have a bootable flash drive attached and hit the F9 key on my system for boot options, there are 2 options for the flash by name (Sandisk, Lexar, Toshiba??) and you need to select the one which has UEFI in the option

---

### Post by javierdl on 2017-07-09
Ok, so I did as you advised:

```

 sudo mkdir /mnt/sdb1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/sdb1

```

I guess the directory you're looking for is in sdb1:

```

/mnt/sdb1$ find /mnt/sdb1 -type d -print
/mnt/sdb1
/mnt/sdb1/EFI
/mnt/sdb1/EFI/ubuntu
/mnt/sdb1/EFI/ubuntu/fw
/mnt/sdb1/EFI/Microsoft
/mnt/sdb1/EFI/Microsoft/Boot
/mnt/sdb1/EFI/Microsoft/Boot/bg-BG
/mnt/sdb1/EFI/Microsoft/Boot/cs-CZ
/mnt/sdb1/EFI/Microsoft/Boot/da-DK
/mnt/sdb1/EFI/Microsoft/Boot/de-DE
/mnt/sdb1/EFI/Microsoft/Boot/el-GR
/mnt/sdb1/EFI/Microsoft/Boot/en-GB
/mnt/sdb1/EFI/Microsoft/Boot/en-US
/mnt/sdb1/EFI/Microsoft/Boot/es-ES
/mnt/sdb1/EFI/Microsoft/Boot/es-MX
/mnt/sdb1/EFI/Microsoft/Boot/et-EE
/mnt/sdb1/EFI/Microsoft/Boot/fi-FI
/mnt/sdb1/EFI/Microsoft/Boot/fr-CA
/mnt/sdb1/EFI/Microsoft/Boot/fr-FR
/mnt/sdb1/EFI/Microsoft/Boot/hr-HR
/mnt/sdb1/EFI/Microsoft/Boot/hu-HU
/mnt/sdb1/EFI/Microsoft/Boot/it-IT
/mnt/sdb1/EFI/Microsoft/Boot/ja-JP
/mnt/sdb1/EFI/Microsoft/Boot/ko-KR
/mnt/sdb1/EFI/Microsoft/Boot/lt-LT
/mnt/sdb1/EFI/Microsoft/Boot/lv-LV
/mnt/sdb1/EFI/Microsoft/Boot/nb-NO
/mnt/sdb1/EFI/Microsoft/Boot/nl-NL
/mnt/sdb1/EFI/Microsoft/Boot/pl-PL
/mnt/sdb1/EFI/Microsoft/Boot/pt-BR
/mnt/sdb1/EFI/Microsoft/Boot/pt-PT
/mnt/sdb1/EFI/Microsoft/Boot/qps-ploc
/mnt/sdb1/EFI/Microsoft/Boot/ro-RO
/mnt/sdb1/EFI/Microsoft/Boot/ru-RU
/mnt/sdb1/EFI/Microsoft/Boot/sk-SK
/mnt/sdb1/EFI/Microsoft/Boot/sl-SI
/mnt/sdb1/EFI/Microsoft/Boot/sr-Latn-CS
/mnt/sdb1/EFI/Microsoft/Boot/sr-Latn-RS
/mnt/sdb1/EFI/Microsoft/Boot/sv-SE
/mnt/sdb1/EFI/Microsoft/Boot/tr-TR
/mnt/sdb1/EFI/Microsoft/Boot/uk-UA
/mnt/sdb1/EFI/Microsoft/Boot/zh-CN
/mnt/sdb1/EFI/Microsoft/Boot/zh-HK
/mnt/sdb1/EFI/Microsoft/Boot/zh-TW
/mnt/sdb1/EFI/Microsoft/Boot/Fonts
/mnt/sdb1/EFI/Microsoft/Boot/Resources
/mnt/sdb1/EFI/Microsoft/Boot/Resources/en-US
/mnt/sdb1/EFI/Microsoft/Recovery
/mnt/sdb1/EFI/Boot
/mnt/sdb1/EFI/refind
/mnt/sdb1/EFI/refind/drivers_x64
/mnt/sdb1/EFI/refind/icons
/mnt/sdb1/EFI/refind/keys
/mnt/sdb1/EFI/refind/themes
/mnt/sdb1/EFI/refind/themes/tux-refind-theme
/mnt/sdb1/EFI/refind/themes/tux-refind-theme/icons
/mnt/sdb1/EFI/refind/icons-backup
/mnt/sdb1/EFI/tools
/mnt/sdb1/boot-sav
/mnt/sdb1/boot-sav/log
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sda
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sda1
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sda2
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sda3
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sda5
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sdb
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sdb1
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sdb2
/mnt/sdb1/boot-sav/log/2017-01-27__21h23boot-repair12/sdb4
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sda
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sda1
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sda2
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sda3
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sda4
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sda5
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sdb
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sdb1
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sdb2
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sdb4
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sdb5
/mnt/sdb1/boot-sav/log/2017-05-26__18h41boot-repair22/sdb6
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sda
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sda1
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sda2
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sda3
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sda4
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sda5
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sdb
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sdb1
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sdb2
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sdb4
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sdb5
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sdb6
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sdd
/mnt/sdb1/boot-sav/log/2017-05-26__19h16boot-repair22/sdd1
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sda
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sda1
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sda2
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sda3
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sda4
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sda5
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sdb
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sdb1
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sdb2
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sdb4
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sdb5
/mnt/sdb1/boot-sav/log/2017-05-27__00h00boot-repair41/sdb6
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sda
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sda1
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sda2
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sda3
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sda4
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sda5
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sdb
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sdb1
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sdb2
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sdb4
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sdb5
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sdb6
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sdc
/mnt/sdb1/boot-sav/log/2017-05-29__13h55boot-info42/sdc1
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sda
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sda1
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sda2
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sda3
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sda4
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sda5
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sdb
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sdb1
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sdb2
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sdb4
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sdb5
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sdb6
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sdc
/mnt/sdb1/boot-sav/log/2017-05-29__13h59boot-info36/sdc1
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sda
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sda1
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sda2
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sda3
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sda4
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sda5
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sdb
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sdb1
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sdb2
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sdb4
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sdb5
/mnt/sdb1/boot-sav/log/2017-05-31__21h06boot-repair34/sdb6
/mnt/sdb1/boot-sav/mbr_backups
/mnt/sdb1/System Volume Information


```

Now what? (as in: What's next?)
Is this something **Boot Repair Disk** could repair?
I suppose at the moment the boot files are not pointing to the right location to find the Ubuntu system dir, right?
If then we need to do that somehow.

---

### Post by javierdl on 2017-07-11
According to Boot Rep D, it successfully repaired it.
However, after choosing Ubuntu on the top of the Grub2 list, it shows the word Ubuntu with a dots animation moving from left to right, suggesting that is loading it, but it takes forever. Prior to that it said it encounter a problem with the video card and asked me to choose what to do. I chose to load the default video settings. And that's when the dots animation started.

---

### Post by oldfred on 2017-07-11
I regularlyinstall another copy of Ubuntu into sdb drive. And it invariably overwrites my /EFI/ubuntu folder on sdb. I always select grub to install to sdb, it even says installing to sdb during install, but always overwrites sda. I keep trying every new version to see if fixed, but not thru current 17.10.

What video card? You may need nomodeset?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If you did not have Internet connecting when installing, no updates or extra options would be installed. You will have to do those once you get it working.

---

### Post by javierdl on 2017-07-11
Thank you so much oldfred, I'll look into that :)

---

### Post by javierdl on 2017-07-13
yancek,

I finally got what you asked done:

```

ubuntu@ubuntu:/mnt/sdb1/EFI$ efibootmgr
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0002,0001,0003
Boot0000* ubuntu
Boot0001* refind
Boot0002* rEFInd Boot Manager
Boot0003* UEFI: Lexar USB Flash Drive 8.07


```

The above makes sense, because it has no problem loading the rEFInd boot loader. Which is good.
However, once it loads, I choose Ubuntu and it still only goes as far as a black screen with this line of text:

```

/dev/sdb3: clean, 223914/19558489 files, 3564666/46000000 blocks

```

---

### Post by oldfred on 2017-07-13
Black screen is then most often video issue.
What video card/chip do you have?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

[/URL]
 [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it) 

[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

### Post by javierdl on 2017-07-14
What's new is that I succeeded to get bcdedit in windows to change its bootmgr path to "\EFI\ubuntu\shimx64.efi".

Now when I try to boot into Ubuntu from the rEFInd boot loader instead of showing that line of text showing "[COLOR=#000000][FONT=&quot]/dev/sdb3: clean, 223914/19558489 files, 3564666/46000000 blocks"[/FONT][/COLOR], now it can further. Except not far enough to load Ubuntu.
It's more obvious that the problem is with the video card drivers. 
So I did as oldfred advised: At the Grub2 page I replaced "quiet splash" for "nomodeset". See the attached screen photo I included herein.
I also tried "nouveau.modeset=0", resulting in similar outputting.

What should I try next?

---

### Post by oldfred on 2017-07-14
Does the recovery mode get you to a terminal? Second or third grub  menu entry perhaps under advanced options.
That automatically has nomodeset and does not load the gui.

---

### Post by javierdl on 2017-07-14
I tried it but I did not end up with a Terminal choice :(
What if I just reinstall, but providing you with a clear partitions layout to be sure we're doing things right. Because obviously I underestimated that before.

---

### Post by oldfred on 2017-07-14
Can you just connect the one drive you want Ubuntu on, so seen as sda?
And then in UEFI mode, you must have gpt partitioning and one of the first partitions as the ESP - efi system partition. 
See link below in my signature for general UEFI install instructions and links to any more details you think you might need.

---

### Post by javierdl on 2017-07-15
Ok, I'll unplug the SSD (sda/Win10). And do as you say with the HD.
Thanks oldfred. At least this way, I shall have a better start, and minimize surprises along the way.

---

### Post by javierdl on 2017-07-15
Btw, do you know if it'll be enough unplugging disk 1, or should I also plug disk 2 to the same cable where disk 1 was?
I'm going to have to wait until Monday to continue with this :(

---

### Post by oldfred on 2017-07-15
I have found it important to have hard drives plugged into SATA ports in order. And no gaps.
Not sure if as critical on initial install.

But when I skipped a SATA port, and rebooted, my flash drive filled into the missing port. Or my sdf flash drive on reboot became sdb and every other drive changed up one. System still booted as UUID used, but some commands that use device like /dev/sdc, I had to be careful which drive was which.

Same happened with newer system where I had DVD between SSD & HDD in SATA port order. HDD was sdb, but some grub commands I use HDD was hd2, not hd1 as expected, SSD was hd0 in all cases as in SATA0 port.

So make sure Ubuntu drive is in lowest SATA port, and when replugging in Windows drive make sure it is in same port it currently is in, probably SATA0. but if flash drive becomes sda, then have Ubuntu in SATA0 for install, and then Windows in SATA0, & Ubuntu in SATA1 once set up.

---

### Post by javierdl on 2017-07-17
I just did a backup of my SSD with Win10.
And I'm ready to unplug the SSD and plug the HD in the same sata cable for it to be the only drive plugged while I reinstall Ubuntu. But I wanted to share my partitions layout with you before I do that, in case you think is better I change something. I am aware that the installer will erase things and may change the layout too, that's ok with me. I already backed up whatever needed backing up.

```

Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name   Flags
 1      1049kB  538MB   537MB   fat32           EF     boot, esp
 2      538MB   301GB   300GB   ext4            Steam
 3      301GB   615GB   315GB   ntfs                   msftdata
 4      615GB   992GB   377GB   ext4
 5      992GB   1000GB  8523MB  linux-swap(v1)         diag


```

Not sure this could help, but here it is:

```
 sudo lsblk -fm
NAME   FSTYPE  LABEL   UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sdd    vfat    lexar32 59AE-C2F5                            /cdrom     sdd     29.8G root  disk  brw-rw----
sdb                                                                    sdb    931.5G root  disk  brw-rw----
&#9500;&#9472;sdb4 ext4    Files   20314bbe-a51e-4e2e-b6b1-0dabcfa32524            &#9500;&#9472;sdb4 350.7G root  disk  brw-rw----
&#9500;&#9472;sdb2 ext4            3ff8f52b-26d0-415f-b890-9ed186c00c5b            &#9500;&#9472;sdb2 279.4G root  disk  brw-rw----
&#9500;&#9472;sdb5 swap            e863d0f6-0ab2-4f1f-9fa3-55a652b02283 [SWAP]     &#9500;&#9472;sdb5     8G root  disk  brw-rw----
&#9500;&#9472;sdb3 ntfs    Shared  6E121CD8385C391F                                &#9500;&#9472;sdb3   293G root  disk  brw-rw----
&#9492;&#9472;sdb1 vfat            D45B-1044                                       &#9492;&#9472;sdb1   512M root  disk  brw-rw----
loop0  squashf                                              /rofs      loop0    1.4G root  disk  brw-rw----


```

---

### Post by oldfred on 2017-07-17
You have a large / (root), and then a large data (Steam) partition. 
I typically use a smaller root, but if just using the data partition for Steam games you may need more space.

Only if you choose auto install, would system repartition. You need to only use Something Else install option and choose (change button) the same / partition for new / partition.

Be sure to boot in UEFI mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]
 If dual booting with Windows a shared NTFS data partition is also recommended.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

[URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by javierdl on 2017-07-17
Which one is root? Is it sdb1?
And what size do you normally set it to?

---

### Post by oldfred on 2017-07-17
If you labeled Steam partition sdb2 which is ext4 correctly then that is just another data partition. 
And then only other ext4 partition is sdb4.

I normally use 25 to 30GB for /. But I have all data in /mnt/data that is normally in /home so my /home is tiny, just user settings. I even move some hidden folders that can get larger like Firefox & Thunderbird profiles.

Showing only partitions, not tempfs & other system mounts. But I do not run games or any really large applications.

```
fred@Asusz97:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        24G  8.5G   15G  38% /
/dev/sda1       500M   27M  473M   6% /boot/efi
/dev/sdb4       385G  116G  250G  32% /mnt/data


```

---

### Post by javierdl on 2017-07-17
Alright, so Ubuntu was installed successfully! :)
I am typing this with it.
Good thing is the rEFInd booting files remained there in the same boot partition.
I will replug the Win10 SSD drive and cross my fingers that things are working. Otherwise I hope the needed fixing won't be too complicated.
Wish me luck!

---

### Post by javierdl on 2017-07-17
YEEESSSSS!!!!!
You're a LINUX GENIUS oldfred !!! :)
I loaded both OSs without a glitch!

Thanks a million, once more! 

I'll go now do the Clonezilla backup for the HD drive with Ubuntu

---

### Post by oldfred on 2017-07-17
Not me, you did it. :)

---

### Post by javierdl on 2017-07-18
Linux Genius, and super humble and modest. They just don't come better than this! ;)

---

