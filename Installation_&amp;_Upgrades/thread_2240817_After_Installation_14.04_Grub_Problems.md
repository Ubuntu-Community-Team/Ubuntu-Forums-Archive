---
title: "After Installation 14.04 Grub Problems"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2014-08-22
I did an install on sdb of a dual boot system. I just had the install disc overwrite the entire sdb and create partitions for me. [see partitions below]

sba = windows
sdb = ubuntu

Rather than MBR it did it in BIOS the partitioning is GPT

Now when I boot up Grub does not show.
The system brings me to the log in screen for Ubuntu.

How do i fix this?

Here is the partition info:

Looking at the partitions on sdb the first one is FAT32 and the installation set it up as the boot with mount point being /boot/efi 

Here is what my disks look like as currently partitioned.

sudo fdisk -l

```

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd7329376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    48383999    24088576   1b  Hidden W95 FAT32
/dev/sda3        48384000  1611192319   781404160    7  HPFS/NTFS/exFAT
/dev/sda4      1611192366  3907024064  1147915849+   7  HPFS/NTFS/exFAT
Partition 4 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 390702916  sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

```

I searched and found the code to display the partitions on sdb
sudo parted /dev/sdb print
```

Model: ATA WDC WD2002FAEX-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   1419GB  1419GB  ext4
 3      1965GB  2000GB  35.0GB  linux-swap(v1)


```


mount

```

/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=allen)
/dev/sdg1 on /media/allen/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```

---

### Post by oldfred on 2014-08-22
Your Windows install in sda is in BIOS boot mode with MBR(msdos) partitioning.
Your Ubuntu install in sdb is in UEFI boot mode with gpt partitioning.

UEFI and BIOS are not really compatible, you can only choose which system to boot from UEFI menu. And you may have to turn on/off UEFI or BIOS/CSM boot mode. Some auto switch and you can use one time boot key to choose which to boot.

How you boot install media is how it installs. You you must have booted flash drive in UEFI mode. From UEFI you can also boot flash drive in BIOS mode.

Boot-Repair's advanced options can also convert a UEFI install to BIOS install on gpt partitioned drive if you manually add a 1 or 2MB unformatted partition and add the bios_grub flag. Use gparted to create bios_grub, it can be anywhere on drive.

Grub2 has os-prober to find other operating systems. It often incorrectly has been finding installs it cannot boot. But in your case it seems like the UEFI version is correctly not finding Windows as it cannot boot it anyway. And with one bootable system in grub menu, the menu is not normally shown. If you want menu and with UEFI often it is the escape key from UEFI boot screen. With BIOS it is hold shift key from BIOS screen until menu appears.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

    
       If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by LaughingHorse on 2014-08-22
So if I understand correctly, I

Use gparted and create say a 2MB unformatted partition for the bios_grub flag. Rather than another ext4 (is that correct)
I did that with gparted and it has a ! warning in red. I did set the flag to bios_grub

This drive will always only be ubuntu.
sda will only be windows, but I do want to be able to boot either one.

My system default is to look at sdb first, then sda.

"Boot-Repair's advanced options can also convert a UEFI install to BIOS install on gpt partitioned drive"
I took a look at boot repair, but I'm not quite sure how to do that without deleting everyting on the drive.

And there were numerous boxes ticked in the advanced section, so i do not want to change somehting that destroys this again :)

---

### Post by oldfred on 2014-08-22
Gparted always shows an issue with bios_grub partitions as they are unformatted as they should be. It also does the same on encrypted and Window's system reserved which is somewhat like the bios_grub as an unformatted partition. As long as there are not warnings or errors on partitions that should be formatted then it is ok.

I have never converted an install, but many have. Not sure of exact settings as I do not think I have seen anyone post all the details.

If it does say install grub to all drives untick that. You only want grub in sdb, not sda.

Not sure if these screens include your UEFI uninstall and grub-pc install.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by LaughingHorse on 2014-08-22
When I started Boot repair, I got a screen that said:
"EFI detected. Please check the options."

I created a summary before doing any changes:
[http://paste.ubuntu.com/8116072/](http://paste.ubuntu.com/8116072/)

I then took screenshots:

[ATTACH=CONFIG]255731[/ATTACH][ATTACH=CONFIG]255732[/ATTACH][ATTACH=CONFIG]255733[/ATTACH][ATTACH=CONFIG]255734[/ATTACH]

GRUB location
Clicked on  "Place GRUB into" and made it sbd
The box next to "Separate/boot partition: sbd4 is greyed out, so I can not tick that box. 

I wanted it going into sdb5 which is what I set up a partition for, but it looks like that is not an option for me

---

### Post by oldfred on 2014-08-22
You are actually uninstalling grub-efi-amd64 and installing grub-pc for BIOS boot.

You do not want efi. Be sure to uncheck that. 

Did you already create bios_grub partition. That is required before you can have a BIOS install of grub to work. That is just used by grub automatically when you install it to sdb, you do not specify it. 

You also do not want grub installed to all MBRs. Be sure to uncheck that.

You do not have nor want a separate /boot partition. That would be for the rest of grub & kernels. Sometimes required with old systems, servers, RAID or LVM type installs.

---

### Post by LaughingHorse on 2014-08-22
I created a partition that was unformatted and flagged as bios_grub it's appx 2 MB
Unfortunately Boot repair does not seem to be finding it.

---

### Post by LaughingHorse on 2014-08-22
While installing GRUB this screen popped up to continue.

Do I have the correct box ticked?

---

### Post by oldfred on 2014-08-22
Yes you need grub in the MBR of sdb drive.
If you install to a partition it will not boot unless you have another boot loader. And if you install to sda, it may boot if BIOS is set to sda, but then you could not directly boot Windows if you had grub issues.

---

### Post by LaughingHorse on 2014-08-22
OK, just finished the installation and got the following message...

```

Please write on a paper the following URL:
http://paste.ubuntu.com/8117244/
In case you still experience boot problem

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (2000GB) disk!

The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from the start of the disk.
 Your BIOS may not detect them. You may want to retry after creating a /boot partition 
(EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. 
Then select this partition via the [Separate /boot partition:] option of [Boot Repair].
 (https://help.ubuntu.com/community/BootPartition)

```

I ought to do this first before I change the home folder I guess.

---

### Post by LaughingHorse on 2014-08-22
I did not create a /boot partition at the start of the disc. 
But it booted up.

It still did not show the option for windows, though.

And one other thing. On the side panel to launch packages, It always shows the disks on sda (windows and data).
I keep unlocking them from the launcher, and yet, each time I reboot, they are there.
It's weird because I do not show windows in GRUB.

But even if I did, I really don't need them in the Launcher. I can just as easily click on them in Nautilus when I need them

---

### Post by oldfred on 2014-08-22
Windows in grub would be to boot it, not to mount it.
Run this to add to grub menu. The install should have found Windows but sometimes you have to re-run the update.

sudo update-grub

If you want to always have Window mounted then you have to add to fstab, like you will be with /home. But for NTFS the settings are different.

You should also be able to directly boot Windows from one time boot key or UEFI/BIOS, but now keep settings in BIOS/CSM/Legacy or whatever your system calls it.

---

