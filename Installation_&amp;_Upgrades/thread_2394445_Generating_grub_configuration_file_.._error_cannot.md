---
title: "Generating grub configuration file .. error: cannot read `/dev/sda': Input/output err"
date: 2018-06-16
forum: Installation &amp; Upgrades
---

### Post by raj1reddy on 2018-06-16
I am having windows and ubuntu installed. When ever new kernal update happens it takes nearly 12 hours to update grub. (given about my system below) . can any one help me to solve this problem.

Given below command to purge old image :
```
sudo apt-get purge  linux-image-4.13.0-26* linux-image-4.13.0-31*  linux-image-4.13.0-32*  linux-image-4.13.0-36* linux-image-4.13.0-37*  linux-image-4.13.0-38* linux-image-4.13.0-39*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-4.13.0-26-lowlatency' for glob 'linux-image-4.13.0-26*'
Note, selecting 'linux-image-4.13.0-26-generic' for glob 'linux-image-4.13.0-26*'
Note, selecting 'linux-image-4.13.0-31-lowlatency' for glob 'linux-image-4.13.0-31*'
Note, selecting 'linux-image-4.13.0-31-generic' for glob 'linux-image-4.13.0-31*'
Note, selecting 'linux-image-4.13.0-32-lowlatency' for glob 'linux-image-4.13.0-32*'
Note, selecting 'linux-image-4.13.0-32-generic' for glob 'linux-image-4.13.0-32*'
Note, selecting 'linux-image-4.13.0-36-lowlatency' for glob 'linux-image-4.13.0-36*'
Note, selecting 'linux-image-4.13.0-36-generic' for glob 'linux-image-4.13.0-36*'
Note, selecting 'linux-image-4.13.0-37-lowlatency' for glob 'linux-image-4.13.0-37*'
Note, selecting 'linux-image-4.13.0-37-generic' for glob 'linux-image-4.13.0-37*'
Note, selecting 'linux-image-4.13.0-38-lowlatency' for glob 'linux-image-4.13.0-38*'
Note, selecting 'linux-image-4.13.0-38-generic' for glob 'linux-image-4.13.0-38*'
Note, selecting 'linux-image-4.13.0-39-generic' for glob 'linux-image-4.13.0-39*'
Note, selecting 'linux-image-4.13.0-39-lowlatency' for glob 'linux-image-4.13.0-39*'
Package 'linux-image-4.13.0-26-lowlatency' is not installed, so not removed
Package 'linux-image-4.13.0-31-lowlatency' is not installed, so not removed
Package 'linux-image-4.13.0-32-lowlatency' is not installed, so not removed
Package 'linux-image-4.13.0-36-lowlatency' is not installed, so not removed
Package 'linux-image-4.13.0-37-lowlatency' is not installed, so not removed
Package 'linux-image-4.13.0-38-lowlatency' is not installed, so not removed
Package 'linux-image-4.13.0-39-lowlatency' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  bnd findbugs gradle-4.4.1 java-wrappers libbindex-java libcommons-collections3-java libcommons-dbcp-java libcommons-pool-java libecj-java libfelix-osgi-obr-java
  libgeronimo-jta-1.1-spec-java libgoogle-gson-java libgradle-core-java libgradle-plugins-java libjarjar-java libjatl-java libjcifs-java libjcip-annotations-java
  libjetty-extra libjetty-extra-java libjformatstring-java libjna-java libjna-jni libkryo-java libllvm4.0 liblogback-java libmail-java libminlog-java
  libnative-platform-java libnative-platform-jni libnekohtml-java libpolyglot-maven-java libreflectasm-java librhino-java libservlet3.0-java libtomcat7-java
  libtomcat8-java linux-headers-4.10.0-40 linux-headers-4.10.0-40-generic linux-headers-4.10.0-42 linux-headers-4.10.0-42-generic linux-headers-4.13.0-26
  linux-headers-4.13.0-26-generic linux-headers-4.13.0-31 linux-headers-4.13.0-31-generic linux-headers-4.13.0-32 linux-headers-4.13.0-32-generic
  linux-headers-4.13.0-36 linux-headers-4.13.0-36-generic linux-headers-4.13.0-37 linux-headers-4.13.0-37-generic linux-headers-4.13.0-38
  linux-headers-4.13.0-38-generic linux-headers-4.13.0-39 linux-headers-4.13.0-39-generic linux-headers-4.13.0-41 linux-headers-4.13.0-41-generic
  linux-image-4.10.0-40-generic linux-image-4.10.0-42-generic linux-image-4.13.0-41-generic linux-image-extra-4.10.0-40-generic linux-image-extra-4.10.0-42-generic
  linux-image-extra-4.13.0-41-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  linux-image-4.13.0-26-generic* linux-image-4.13.0-31-generic* linux-image-4.13.0-32-generic* linux-image-4.13.0-36-generic* linux-image-4.13.0-37-generic*
  linux-image-4.13.0-38-generic* linux-image-4.13.0-39-generic* linux-image-extra-4.13.0-26-generic* linux-image-extra-4.13.0-31-generic*
  linux-image-extra-4.13.0-32-generic* linux-image-extra-4.13.0-36-generic* linux-image-extra-4.13.0-37-generic* linux-image-extra-4.13.0-38-generic*
  linux-image-extra-4.13.0-39-generic*
0 to upgrade, 0 to newly install, 14 to remove and 14 not to upgrade.
After this operation, 1,667 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 652079 files and directories currently installed.)
Removing linux-image-extra-4.13.0-26-generic (4.13.0-26.29~16.04.2) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic


Generating grub configuration file ...
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
Found linux image: /boot/vmlinuz-4.13.0-45-generic
Found initrd image: /boot/initrd.img-4.13.0-45-generic
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
Found linux image: /boot/vmlinuz-4.13.0-43-generic
Found initrd image: /boot/initrd.img-4.13.0-43-generic
Found linux image: /boot/vmlinuz-4.13.0-41-generic
Found initrd image: /boot/initrd.img-4.13.0-41-generic
Found linux image: /boot/vmlinuz-4.10.0-42-generic
Found initrd image: /boot/initrd.img-4.10.0-42-generic
Found linux image: /boot/vmlinuz-4.10.0-40-generic
Found initrd image: /boot/initrd.img-4.10.0-40-generic
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
Found Windows 8 (loader) on /dev/sda1
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
done
Purging configuration files for linux-image-extra-4.13.0-26-generic (4.13.0-26.29~16.04.2) ...
Removing linux-image-4.13.0-26-generic (4.13.0-26.29~16.04.2) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
dkms: removing: bcmwl 6.30.223.271+bdcom (4.13.0-26-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.271+bdcom
Kernel:  4.13.0-26-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
update-initramfs: Deleting /boot/initrd.img-4.13.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
Generating grub configuration file ...
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
...
--

=========================================================
`sudo parted -l`

Model: ATA APPLE HDD ST500L (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs            boot
 2      368MB   231GB  230GB   primary   ntfs
 3      231GB   234GB  3274MB  primary   ntfs
 4      234GB   500GB  266GB   extended
 7      234GB   328GB  93.8GB  logical   ext4
 5      328GB   492GB  164GB   logical   ext4
 6      492GB   500GB  8577MB  logical   linux-swap(v1)

===============================================
`sudo fdisk -lu`
[sudo] password for praveen: 
Disk /dev/loop0: 162.9 MiB, 170766336 bytes, 333528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 457.6 MiB, 479789056 bytes, 937088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 482.8 MiB, 506269696 bytes, 988808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 86.6 MiB, 90812416 bytes, 177368 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 162.1 MiB, 169943040 bytes, 331920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 483.2 MiB, 506716160 bytes, 989680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 86.6 MiB, 90828800 bytes, 177400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x51750080


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    718847    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda2          718848 450559999 449841152 214.5G  7 HPFS/NTFS/exFAT
/dev/sda3       450560000 456953855   6393856   3.1G  7 HPFS/NTFS/exFAT
/dev/sda4       456955902 976771071 519815170 247.9G  5 Extended
/dev/sda5       640178176 960016383 319838208 152.5G 83 Linux
/dev/sda6       960018432 976771071  16752640     8G 82 Linux swap / Solaris
/dev/sda7       456955904 640178175 183222272  87.4G 83 Linux


Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.


============================================================

 sudo cfdisk

                                                                             Disk: /dev/sda
                                                         Size: 465.8 GiB, 500107862016 bytes, 976773168 sectors
                                                                   Label: dos, identifier: 0x51750080


    Device                 Boot                           Start                  End              Sectors              Size            Id Type
>>  /dev/sda1              *                               2048               718847               716800              350M             7 HPFS/NTFS/exFAT                
    /dev/sda2                                            718848            450559999            449841152            214.5G             7 HPFS/NTFS/exFAT
    /dev/sda3                                         450560000            456953855              6393856              3.1G             7 HPFS/NTFS/exFAT
    /dev/sda4                                         456955902            976771071            519815170            247.9G             5 Extended
    &#9500;&#9472;/dev/sda5                                       640178176            960016383            319838208            152.5G            83 Linux
    &#9500;&#9472;/dev/sda6                                       960018432            976771071             16752640                8G            82 Linux swap / Solaris
    &#9492;&#9472;/dev/sda7                                       456955904            640178175            183222272             87.4G            83 Linux
    Free space                                        976771072            976773167                 2096                1M







 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;  Partition type: HPFS/NTFS/exFAT (7)                                                                                                                                &#9474;
 &#9474;      Attributes: 80                                                                                                                                                 &#9474;
 &#9474;      Filesystem: ntfs                                                                                                                                               &#9474;
 &#9474;Filesystem label: System Reserved                                                                                                                                    &#9474;
 &#9474; Filesystem UUID: ECB672B8B67282BE                                                                                                                                   &#9474;
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
===================================================
`sudo lshw -C disk`
  *-disk                  
       description: ATA Disk
       product: APPLE HDD ST500L
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0007
       serial: S2XMJ9AD523955
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=51750080
  *-cdrom
       description: DVD-RAM writer
       product: DVD RAM UJ897
       vendor: hp
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
```

---

### Post by oldfred on 2018-06-16
Please use code tags on long or terminal output. Easy to add with Forum's advanced editor and # icon.

Seem like two issues. One is too many kernels and another related to reading drive.
Have you run fsck on the ext4 partitions, are you mounting Windows with fast start up on, or checked Smart Status (upper right icon in Disks aka Gnome Disks)?

       To see all your ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by raj1reddy on 2018-06-17
marking as solved:
Solved with below steps.

try deleting some of the initrd images:

try deleting some of the initrd images:


sudo rm /boot/initrd.img-3.13.0-3*
sudo rm /boot/initrd.img-3.13.0-4*
sudo rm /boot/initrd.img-3.13.0-5*
and the linux images:


sudo rm /boot/vmlinuz-3.13.0-3*
sudo rm /boot/vmlinuz-3.13.0-4*
sudo rm /boot/vmlinuz-3.13.0-5*
Then use apt-get to purge them:


sudo apt-get purge linux-image-3.13.0-3* linux-image-3.13.0-4* linux-image-3.13.0-5*
Then, make sure the upgrade went properly by running the following commands:


sudo apt-get update
sudo apt-get upgrade
If you get no errors, run the following:


sudo apt-get update
sudo apt-get dist-upgrade
When that is done, run:


cat /etc/apt/sources.list.d | grep wily
it should return wily.


EDIT


Because windows seems to be in a hibernated state, run the following command to fix that:


sudo ntfsfix /dev/sdXX
where sdXX is the drive and partition number of the drive partition that was "left in an unsafe state". Example sdc1.


Then, run:


sudo update-grub
sudo rm /boot/initrd.img-3.13.0-3*
sudo rm /boot/initrd.img-3.13.0-4*
sudo rm /boot/initrd.img-3.13.0-5*
and the linux images:


sudo rm /boot/vmlinuz-3.13.0-3*
sudo rm /boot/vmlinuz-3.13.0-4*
sudo rm /boot/vmlinuz-3.13.0-5*
Then use apt-get to purge them:


sudo apt-get purge linux-image-3.13.0-3* linux-image-3.13.0-4* linux-image-3.13.0-5*
Then, make sure the upgrade went properly by running the following commands:


sudo apt-get update
sudo apt-get upgrade
If you get no errors, run the following:


sudo apt-get update
sudo apt-get dist-upgrade
When that is done, run:


cat /etc/apt/sources.list.d | grep wily
it should return wily.


EDIT


Because windows seems to be in a hibernated state, run the following command to fix that:


sudo ntfsfix /dev/sdXX
where sdXX is the drive and partition number of the drive partition that was "left in an unsafe state". Example sdc1.


Then, run:


sudo update-grub

============================
thanks "oldfred",
I will try to do what you say also
Marking as solved.

---

### Post by raj1reddy on 2018-06-17
marking as solved:
Solved with below steps.

try deleting some of the initrd images:

try deleting some of the initrd images:


sudo rm /boot/initrd.img-3.13.0-3*
sudo rm /boot/initrd.img-3.13.0-4*
sudo rm /boot/initrd.img-3.13.0-5*
and the linux images:


sudo rm /boot/vmlinuz-3.13.0-3*
sudo rm /boot/vmlinuz-3.13.0-4*
sudo rm /boot/vmlinuz-3.13.0-5*
Then use apt-get to purge them:


sudo apt-get purge linux-image-3.13.0-3* linux-image-3.13.0-4* linux-image-3.13.0-5*
Then, make sure the upgrade went properly by running the following commands:


sudo apt-get update
sudo apt-get upgrade
If you get no errors, run the following:


sudo apt-get update
sudo apt-get dist-upgrade
When that is done, run:


cat /etc/apt/sources.list.d | grep wily
it should return wily.


EDIT


Because windows seems to be in a hibernated state, run the following command to fix that:


sudo ntfsfix /dev/sdXX
where sdXX is the drive and partition number of the drive partition that was "left in an unsafe state". Example sdc1.


Then, run:


sudo update-grub
sudo rm /boot/initrd.img-3.13.0-3*
sudo rm /boot/initrd.img-3.13.0-4*
sudo rm /boot/initrd.img-3.13.0-5*
and the linux images:


sudo rm /boot/vmlinuz-3.13.0-3*
sudo rm /boot/vmlinuz-3.13.0-4*
sudo rm /boot/vmlinuz-3.13.0-5*
Then use apt-get to purge them:


sudo apt-get purge linux-image-3.13.0-3* linux-image-3.13.0-4* linux-image-3.13.0-5*
Then, make sure the upgrade went properly by running the following commands:


sudo apt-get update
sudo apt-get upgrade
If you get no errors, run the following:


sudo apt-get update
sudo apt-get dist-upgrade
When that is done, run:


cat /etc/apt/sources.list.d | grep wily
it should return wily.


EDIT


Because windows seems to be in a hibernated state, run the following command to fix that:


sudo ntfsfix /dev/sdXX
where sdXX is the drive and partition number of the drive partition that was "left in an unsafe state". Example sdc1.


Then, run:


sudo update-grub

============================
thanks "oldfred",
I will try to do what you say also
Marking as solved.

---

### Post by oldfred on 2018-06-17
You should almost never use rm to delete any installed file. That confuses dpkg as it will have it in the list of installed apps and not be able to correctly remove it.
Also the file in /boot is only part of where kernels may be. Using dpkg will house clean everything.
But occassionly if /boot a separate partition and full, you may have to manually delete a file to make room for dpkg to work. May then be better to reinstall kernel that was rm'd and correctly delete with dpkg so fully cleaned up.

       Use dpkg -S to see which .dkms files were not placed by the package manager
dpkg -S /full/path/to/file
Only use rm on files not in dpkg
dpkg -S /lib/modules | sed s/:.\*//
uname --kernel-release
 Did you also check /var/cache/apt/archives? You may have the old .deb's taking up space.
 /var/cache/apt/archives
kernel house clean
/usr/src/*
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this)
in /boot by version: abi, config, initrd.img, vmlinuz

---

