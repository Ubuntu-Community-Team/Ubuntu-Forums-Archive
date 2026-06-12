---
title: "How to uninstall..."
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by Linussi on 2011-08-17
Hello. 
I burned a Kubuntu CD. When I try to boot with it, PC get stuck. 
So I installed Kubuntu from Synaptic, and now when I boot I get the Kubuntu loading logo, and then Log in view from Ubuntu. 

So now my questions are:
1. Do I have Kubuntu installed?
2. How can I uninstall Ubuntu?
3. If I have both installed, how can I boot to Kubuntu instead? 

Thank you,

---

### Post by lmarmisa on 2011-08-17
Open a terminal, type these commands and post the results:

```

lsb_release -a
sudo fdisk -l
sudo parted -l
mount
sudo swapon -s

```

---

### Post by sanderd17 on 2011-08-17
In general, you can select your DE (desktop environment) from your login screen. Normally the moment where you have to fill in your password.

I don't know what login manager you are using now (default ubuntu or KDE) so I can't give exact locations where to look.

---

### Post by Linussi on 2011-08-18
Thank you for your reply's. 
I am currently at work and cannot access my PC. 
Anyway, I found the Options button in the Log in view, and there was KDE plasma showing. 
If I log in to that, can I uninstall Ubuntu from there somehow? 
I dont undertsand why my cd is not working. It can boot from it, and I see the screen with options Start Kubuntu etc. But the PC hangs every time I try to start it. I have burned 2 cd:s, one on a mac and one on Ubuntu. Both fail the same way. 

Any ideas?

---

### Post by sanderd17 on 2011-08-18
For the CD, check the md5 sum, or try a live USB (you can create one with the ubuntu program called "usbcreator").

To uninstall Ubuntu, I would not do that. Basically, Ubuntu is the Linux kernel, and on top of that you have your programs.

Those programs are user programs like LibreOffice, but also xorg, the program that is the bases of any modern desktop environment.

When you work with the package manager, it keeps track of dependancies. So if you want to install package A, but package A needs B, than the package manager will also install B. Not only that, but the package manager will also remember that B was automatically installed. So if you decide to remove A, B will also be removed.

Now, the ubuntu-desktop package depends on a lot of other packages. As you can see here: [http://packages.ubuntu.com/natty/ubuntu-desktop](http://packages.ubuntu.com/natty/ubuntu-desktop) . So if you remove the ubuntu-desktop, it will also remove the "automatic installed" packages that ubuntu-desktop needs. Off coarse, the package manager will look if they aren't needed somewhere else, but since the ubuntu-desktop package has a very huge amount, the chance is big that the package manager will also remove packages that you still want (but maybe are not strictly needed).

Figuring out what packages should or should not be removed is a lot of work.

---

### Post by Linussi on 2011-08-18
In DOS I cannot select USB as a startup option. I only have CD or HDD. 
I am running out of ideas.

---

### Post by sanderd17 on 2011-08-18
In DOS?

How can you see boot options in DOS? You should be in your BIOS.

Anyway, how old is your computer? Older computers don't have the ability to boot from an USB.

And did you check the MD5 sum of the CD?

---

### Post by Linussi on 2011-08-18
Of course I meant bios. My pc is around one year old, and the checksum is a match.

---

### Post by Linussi on 2011-08-18
Here are the results: 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c5e1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18693   150145024   83  Linux
/dev/sda2           18693       19458     6142977    5  Extended
/dev/sda5           18693       19458     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Model: ATA WDC WD1600JD-00H (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  154GB  154GB   primary   ext4            boot
 2      154GB   160GB  6290MB  extended
 5      154GB   160GB  6290MB  logical   linux-swap(v1)


Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4


Model: ATA ST3320620AS (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  320GB  320GB  ext4

/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb on /media/TERA type ext4 (rw,noexec,nosuid,nodev,commit=0)
/dev/sdc on /media/MEGAHYPER type ext4 (rw,noexec,nosuid,nodev,commit=0)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/linus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=linus)


Filename                Type        Size    Used    Priority
/dev/sda5                               partition    6142972    252    -1

---

### Post by sanderd17 on 2011-08-20
Sorry for the late response (my mail notifications don't wok anymore)

your output says thay sdb doesn'y have a valid partition table. I guess this is your USB. Try to create one fat32 partition on it with gparted and use usbcreator again to put a live system on it.

---

