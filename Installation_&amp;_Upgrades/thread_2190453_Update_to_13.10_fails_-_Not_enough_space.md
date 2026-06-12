---
title: "Update to 13.10 fails - Not enough space"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by bonalymac on 2013-11-27
Hi

I'm a complete beginner with Ubuntu. I am computer literate, and build and repair Windows PC's for friends and family, but I struggle big time with Ubuntu.

I have an old PC which I installed Ubunto on and it is used as a family PC for browsing, simple games etc. Today I used the software updater and it ran fine but then suggested I could upgrade from 13.04 to 13.10. When I try it however, I get told I have not got enough space, and need to clean approx 35Mb of space

As far as I am aware, the main disk (there are 2 physical disks) has approx 130Gb available in total, but obviously not in the correct place. I have run the apt-get clean as suggested, I have also emptied the recycle bin, but it still fails.

Can someone help tell me what I need to try next. Thanks

Colin

---

### Post by fantab on 2013-11-27
Post the output of:

```
df -h
sudo parted -l
sudo fdisk -l
```

---

### Post by bonalymac on 2013-11-27
Many thanks for offering your help.

I think this is the listing you wanted


> colin@Bon-99:~$ df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root  145G   26G  112G  19% /
none                     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                     969M  4.0K  969M   1% /dev
tmpfs                    196M  2.0M  194M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     977M  148K  977M   1% /run/shm
none                     100M   44K  100M   1% /run/user
/dev/sda1                228M  202M   15M  94% /boot
/dev/sdb1                280G  202G   79G  72% /media/colin/MM1 - Audio




colin@Bon-99:~$ sudo parted -l
Model: ATA ST3160215ACE (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   160GB  160GB  extended
 5      257MB   160GB  160GB  logical                lvm


Model: ATA Maxtor 6L300R0 (scsi)
Disk /dev/sdb: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  300GB  300GB  primary  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-swap_1: 2080MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  2080MB  2080MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 158GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  158GB  158GB  ext4





colin@Bon-99:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b9318

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2a8d3b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   586110975   293054464    7  HPFS/NTFS/exFAT

Disk /dev/mapper/ubuntu-root: 157.7 GB, 157701636096 bytes
255 heads, 63 sectors/track, 19172 cylinders, total 308011008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 2080 MB, 2080374784 bytes
255 heads, 63 sectors/track, 252 cylinders, total 4063232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table


---

### Post by rbratcher on 2013-11-27
I would like to jump in here too.  I have tried to upgrade from Ubuntu 10.04 LTS with the same result, also deleting files and cleaning.   Here is my info: 

rick@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G   12G  1.5G  90% /
none                  999M  340K  998M   1% /dev
none                 1003M  288K 1003M   1% /dev/shm
none                 1003M   84K 1003M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
/dev/sda3             278G  7.9G  256G   3% /home
rick@ubuntu:~$ sudo parted -l
[sudo] password for rick: 
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      512B    15.0GB  15.0GB  primary  ext3            boot
 2      15.0GB  17.0GB  2010MB  primary  linux-swap(v1)
 3      17.0GB  320GB   303GB   primary  ext3


rick@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b33f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14648437+  83  Linux
/dev/sda2            1824        2069     1962890+  83  Linux
/dev/sda3            2069       38914   295959895+  83  Linux
rick@ubuntu:~$ ^C
rick@ubuntu:~$ 


Thanks

---

### Post by fantab on 2013-11-27
@**bonalymac**:
> dev/sda1                228M  202M   15M  **94%** /boot

I think you have old and unused kernels, you need to clean them first. Lets do it.
```
sudo update-grub
```
Will list all the kernel you have in there. Make a note of 'em.
```
uname -r
```
... will tell you what kernel you are currently using. Make a note of it and compare with the above to see if you are using the latest kernel available to you. If not reboot and check again.
```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```
... will list all the old and unused kernels that the above command will be removing. Check to see it not removing the kernel shown by 'uname -r'. If it does then stop and report back. If not, then
```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```
... will actually remove all the old and unsued kernels from your system.
```
sudo update-grub
```
... to check how did the cleaning go and to update-grub... 
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```
... to bring your system upto date. Now you can upgrade to 13.10.

@**rbratcher**:
> /dev/sda1              14G   12G  1.5G ** 90%** /
You can also follow the above. 
Also in your case it will be good idea to do a clean and fresh install of 12.04 than doing an internal upgrade.

---

### Post by bonalymac on 2013-11-28
Fantab

Perfect. Thank you very very much!

Your instructions worked exactly as you said they would, and my upgrade is now underway, it is just downloading 823M of files, and predictiing 12 mins of download followed by potentially much longer upgrade.

It is great to have resources like this available to stoopid users like me. Windows has it's own foibles, but the visual environment gives the user the impression that it is easier (of course in many ways it isn't really).

So thanks again for your time, and help, it really is appreciated, from a happy noob user

Colin

---

### Post by fantab on 2013-11-28
Glad that you've cleaned the /boot directory and that you are able to upgrade.
If the present issue is solved then mark this Thread as 'Solved' using Thread Tools.

---

