---
title: "GRUB installation failed 'grub-efi-amd64-signed'"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by nick106 on 2014-04-22
The grub-efi-amd64-signed package failed to install into /target/.

Trying to install Ubuntu 14.04 from a USB pen drive to a virgin raid set up similar to ([https://wiki.debian.org/Multi%20HDD/SSD%20Partition%20Scheme](https://wiki.debian.org/Multi%20HDD/SSD%20Partition%20Scheme)).

Boot from usb into 'try ubuntu' to install mdadm to get the raid spun up. It is 100% booting in EFI mode (the nice black minamilist screen)

when it stops the following are mounted.
```

/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdd1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
tmpfs on /var/lib/polkit-1/localauthority/90-mandatory.d type tmpfs (rw)
/dev/md1 on /target type ext4 (rw,errors=remount-ro)
/dev/md0 on /target/boot type ext2 (rw)
/dev/sdb1 on /target/boot/efi type vfat (rw)
/dev/md4 on /target/home type ext4 (rw)
/dev/md7 on /target/mnt/bulk type ext4 (rw)
/dev/md6 on /target/mnt/vm type ext4 (rw)
/dev/md5 on /target/mnt/work type ext4 (rw)
/dev/md2 on /target/var type ext4 (rw)
/cdrom on /target/cdrom type none (ro,bind)
/proc on /target/proc type none (rw,bind)
/sys on /target/sys type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/run on /target/run type none (rw,bind)

``` 

/proc/mdstat has the following

```

Personalities : [raid1] 
md6 : active raid1 sdc4[0] md60[1](W)
      183239424 blocks super 1.2 [2/2] [UU]
      
md4 : active raid1 sdb3[0] md40[2](W) sdc3[1]
      5235584 blocks super 1.2 [3/3] [UUU]
      
md1 : active raid1 sdc2[0] md10[1](W)
      20939520 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdc1[0] sda1[1]
      358336 blocks [3/2] [UU_]
      
md5 : active raid1 sdb4[0] md50[1](W)
      183239424 blocks super 1.2 [2/2] [UU]
      
md7 : active raid1 sda8[0]
      500213568 blocks super 1.2 [2/1] [U_]
      bitmap: 4/4 pages [16KB], 65536KB chunk

md60 : active raid1 sda7[0]
      183370624 blocks super 1.2 [2/1] [U_]
      bitmap: 2/2 pages [8KB], 65536KB chunk

md50 : active raid1 sda6[0]
      183370624 blocks super 1.2 [2/1] [U_]
      bitmap: 2/2 pages [8KB], 65536KB chunk

md40 : active raid1 sda5[0]
      5239744 blocks super 1.2 [2/1] [U_]
      bitmap: 1/1 pages [4KB], 65536KB chunk

md3 : active raid1 sda4[0]
      67075968 blocks super 1.2 [2/1] [U_]
      bitmap: 1/1 pages [4KB], 65536KB chunk

md2 : active raid1 sda3[0]
      15720320 blocks super 1.2 [2/1] [U_]
      bitmap: 1/1 pages [4KB], 65536KB chunk

md10 : active raid1 sda2[0]
      20956032 blocks super 1.2 [2/1] [U_]
      bitmap: 1/1 pages [4KB], 65536KB chunk

unused devices: <none>

```

The output from sudo parted -l is
```

Model: ATA ST1000LM014-1EJ1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      1049kB  368MB   367MB   ext2         hdd_p_boot  raid
 2      368MB   21.8GB  21.5GB               hdd_p_root  raid
 3      21.8GB  38.0GB  16.1GB               hdd_p_var   raid
 4      38.0GB  107GB   68.7GB               hdd_p_swap  raid
 5      107GB   112GB   5370MB               hdd_p_home  raid
 6      112GB   300GB   188GB                hdd_p_work  raid
 7      300GB   488GB   188GB                hdd_p_VM    raid
 8      488GB   1000GB  512GB                hdd_p_bulk  raid


Model: ATA INTEL SSDMCEAC24 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      1049kB  578MB   577MB   fat32        ssd_p_efi   boot
 2      578MB   22.1GB  21.5GB               ssd_p_root  raid
 3      22.1GB  27.4GB  5369MB               ssd_p_home  raid
 4      27.4GB  215GB   188GB                ssd_p_work  raid


Model: ATA INTEL SSDMCEAC24 (scsi)
Disk /dev/sdc: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      1049kB  368MB   367MB   ext2         ssd_p_boot  raid
 2      368MB   21.8GB  21.5GB               ssd_p_root  raid
 3      21.8GB  27.2GB  5369MB               ssd_p_home  raid
 4      27.2GB  215GB   188GB                ssd_p_VM    raid


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdd: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  8011MB  8007MB  primary  fat32        boot, lba


Model: Linux Software RAID Array (md)
Disk /dev/md0: 367MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  367MB  367MB  ext2


Model: Linux Software RAID Array (md)
Disk /dev/md1: 21.4GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  21.4GB  21.4GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md2: 16.1GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  16.1GB  16.1GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md3: 68.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  68.7GB  68.7GB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md4: 5361MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  5361MB  5361MB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md5: 188GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  188GB  188GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md6: 188GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  188GB  188GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md7: 512GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  512GB  512GB  ext4


                                                                            Error: /dev/md10: unrecognised disk label

                                                                            Error: /dev/md40: unrecognised disk label

                                                                            Error: /dev/md50: unrecognised disk label

                                                                            Error: /dev/md60: unrecognised disk label



```

The /dev/mdX0 are child raids nested inside thier higher /dev/mdX parents which is probably why they have unrecognised disk labels.

I've tried both installing with no network to stop updates and installing with network. In both cases the same error :(

I have previously successfully installed Debian through to being able to boot, but then X fails to start due to some oddities with my GPU. Somone on the suppliers site posted that he had installed Ubuntu with no problems and the fact I can get the LiveCD working (enough to type this) makes me feel that if I can cure this I'll be able to get Linux up and running on this laptop.

It's only day four of the new machine so I'm in a reasonably chipper mood still.

Thanks in advance for your help, and If You need anything else posted just ask.

Nick(c)

---

