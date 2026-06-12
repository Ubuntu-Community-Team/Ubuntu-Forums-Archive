---
title: "ubuntu update trashes ubuntu on usb installation"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by AlanRick on 2010-01-10
I've installed ubuntu 9.10  on a U3 usb stick using the tools and instructions on pendrivelinux.com. Everything worked perfectly,(and easily :D ) including the wlan.

But after updating using the ubuntu update manager (torrented iso seems to be 72 days old) it fails to boot:

The command prompt displays loads of *could not load sr0* or sd1... and then finally
```
unable to find a medium containing a live file system [initramfs]
```

Possible reasons for failure are dialog boxes displayed during the update (hardy updates used to be fully automatic so I'm not used to prompts):

1. At some point the update asks whether it should replace a file and I select "no" (the filename is app....).

2. Later there is a grub wizard with two check-boxes (maybe because the USB is U3 (I.e. displays as two partitions f: and g: when I view it in Windows). One is sda and the other sdb. I leave both unchecked before continuing the wizard since I don't want to mess up my hard-disk, too.

Now the usb no longer starts ubuntu :( 

I can probably get away with doing a fresh reinstall and never applying the ubuntu security fixes since it's only a usb. But I'd prefer keep the system up-to-date so if anyone does have an idea of how to get the update to work .... I'd be very very grateful.

Alan

---

### Post by phillw on 2010-01-10
Hi, U3 pendrives seem to be a recurring pain.

If you boot from hard-dive
sda should be your hard drive
sdb should be your pen drive.

If you boot from pendrive
sda should be your pen drive
sdb should be your hard drive

With both plugged in ```
 df -H 
``` will quickly confirm it, just look at the sizes

as you selected no where for grub to put itself on - it couldn't. That's the most likely cause of the boot failure.

If you head over here --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  you'll be able to re-install grub onto your pendrive and it should be back booting happily.

If you're nervous of Update Mananger 'touching' your hard disk, then un-mount it. Again, ```
 df -H 
``` will let you know what is mounted - You won't want your hard drive mounted while you do updates.

/edit - if you boot from the LiveCD (needed to restore grub) - use the df -H to check which is hard drive & which is pen drive - if you do an ls of the main partition in your pendrive, you'll see your casper-rw stuff - that will confirm you have the correct device

Regards,

Phill.

---

### Post by AlanRick on 2010-01-10
Many thanks Phill.
I'll give it another go using the dh command you suggested.

It also occurs to me that grub 2 might be the evil (rather than u3) so I might resort to putting hardy on the usb instead.

---

### Post by AlanRick on 2010-01-10
Just for the record (and memory) this is what I see when I boot from the 8GB usb stick:
```
Filesystem             Size   Used  Avail Use% Mounted on
aufs                   2.3G    93M   2.0G   5% /
udev                   1.1G   271k   1.1G   1% /dev
/dev/sdb1              8.1G   3.4G   4.7G  42% /cdrom
/dev/loop0             701M   701M      0 100% /rofs
none                   1.1G   279k   1.1G   1% /dev/shm
tmpfs                  1.1G    13k   1.1G   1% /tmp
none                   1.1G    91k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sr1               7.0M   7.0M      0 100% /media/U3 System
/dev/sr0               687M   687M      0 100% /media/JACK
```
Looks like  sr0 is the dvd drive so this can be ignored.
There is no hard-drive showing up (confirms sda) and the u3 drive is sr1.
Looks like the usb space for the pen-install is sdb1 so I guess I select sdb from the grub wizard.

---

### Post by efflandt on 2010-01-10
USB with U3 is probably not optimum for booting Linux.  I tried making a bootable USB live/install Ubuntu system on a 2 GB Sandisk Mini-Cruzer with U3 and it seemed to take twice as long to boot (2 minutes) as regular USB flash (about 60 sec) or even much longer than 2 GB microSD in a USB card reader (about 70 sec).  Maybe some of your problems (or at least maybe boot delays) are due to U3 in firmware showing up as an sr device (cdrom) even if you totally wipe its writable flash.

I don't think your drive order would normally change unless you boot from a different computer.  I have a regular installation of 64-bit Ubuntu on a WD Passport, and the main hard drive in the computer is always sda.  But on various laptops the USB drive is typically sdb, and when I boot it from my desktop with built-in USB card reader, the USB drive is always sdf.  But it all works due to UUID identifying the USB drive.

I just noticed after I posted that you seem to be running live/install iso, not a regular system.  While you can add programs and settings to a persistent system, it is probably a bad idea to try to remove or update anything, since that will not be available during boot until after the persistent file system is mounted later on in the boot process.  So I doubt if you can update your kernel or initscripts.  If you want to be able to update things, you should install a regular system to USB, including grub2 (make sure you put that on USB in last Advanced button of install).

---

### Post by C.S.Cameron on 2010-01-10
Doing an update using update manager on a 'persistent' thumbdrive will quickly fill a 8G thumbdrive persistence file.
Also the kernel is frozen as it is just an image and will not update. 
If you want to be able to update and upgrade your pendrive you should consider a full install.

---

### Post by AlanRick on 2010-01-11
Thank you both for the warnings - I won't update or take it further since it works enough already.
I've also discovered that one (new) computer can't boot from the usb so I've learnt that U3 is a bad idea for boot-usb's, anyway.

---

### Post by dannyboy79 on 2010-01-11
hold up here. i used the tutorial on pendrivelinux and a karmic iso to create a 4gb casper-rw image which gets put on the usb stick which is formatted as fat32 and i did updates and what not with no problem. so it's not the updates, i am guessing it more the u3 (what is u3 anyway?) i will have to say though that some of my most important changes I have made are not being saved but other changes are like app installs and what not. those are getting saved but my changes to fstab and /etc/hostname  are not being saved. what gives????

my mount command shows this:
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type tmpfs (rw,relatime,mode=755)
/dev/sdc1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/sdc1 on /casper-rw-backing type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,errors=remount-ro)
/dev/loop1 on /cow type ext2 (rw,noatime,errors=continue)
aufs on / type aufs (rw,noatime,si=79268fb2)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
none on /lib/init/rw type tmpfs (rw,nosuid,relatime,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)

ne1 see anything wrong with there? when I issue df -h to see how much space remains i get this:
df: cannot read table of mounted file systems: Input/output error
so I am guessing something is wrong.
whgen I check dmesg i see these errors:
[    6.604059]  sdc: sdc1
[    6.609061] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.609066] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    7.490823] aufs 2-standalone.tree-30-20090727
[    7.504996] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    7.704029] end_request: I/O error, dev fd0, sector 0
[    7.728026] end_request: I/O error, dev fd0, sector 0
[    8.144317] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[    8.934337] aufs test_add:242:exe[1035]: uid/gid/perm //filesystem.squashfs 0/0/0755, 0/0/0777
 
and this:

[   93.165416] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[   93.166245] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[   93.204966] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[   93.210270] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[   93.220604] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[   93.228076] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  631.280036] kjournald starting.  Commit interval 5 seconds
[  631.280409] EXT3 FS on sda1, internal journal
[  631.280415] EXT3-fs: mounted filesystem with writeback data mode.
[  631.281532] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  631.282107] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  685.537173] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  685.539533] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  721.195701] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  726.898971] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  739.143532] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  739.143569] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  739.327796] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  741.015655] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  742.665076] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  742.665113] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  746.744016] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  748.275680] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  801.664100] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[  801.664124] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[  801.664245] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[  810.349147] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  810.350912] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  810.353541] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  810.360789] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  810.363106] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  810.367831] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  850.110159] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  903.482917] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  925.858973] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  964.585804] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  968.049649] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  968.874997] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  968.876467] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  973.519693] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[  975.327460] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[ 1001.797321] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[ 1001.797358] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[ 1001.903791] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[ 1003.803169] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[ 1003.883635] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[ 1012.368224] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[ 2194.315047] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055
[ 2236.946528] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 533055

---

