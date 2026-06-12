---
title: "Ubuntu 10.04 LTS Hardware Move"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by fingon.palantir on 2012-01-23
I´ve moved a working Installation of Ubuntu 10.04 LTS Alternate to another hardware by using rsync.
At first I´ve made a normal Ubuntu 10.04 LTS Alternate Installation on the new Hardware, after that i´ve booted a Linux LiveSystem and copied / without /proc /dev /boot on the new /.
After a reboot the Server boots up without any problems. But when I make a Kernelupdate the Server doesen´t boot anymore with the GRUB message:

```
Gave up waiting for root device. Common problems:

- Boot args (cat /proc/cmdline)
- Check root delay...
- Check root...
- Missing modules (cat /proc/modules); ls /dev)

ALERT /dev/md0 does not exist. Dropping to a shell..
```

At the moment I don't have any idea what to do. The old system doesen´t exist for any tests.

---

### Post by Cheesemill on 2012-01-23
If you still have the drive from the old machine just image it to the new one.

No need to reinstall and copy select files over.

---

### Post by oldfred on 2012-01-23
Were/are you running RAID or LVM?

> /dev/md0

You normally have to update grub & fstab with new partitions or UUIDs. UUID is also stored in a few other places for updates and may have reverted to the old one?

Post boot info script. Use the beta version.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

Or download & run directly:
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

---

### Post by oldfred on 2012-01-23
Reinstall drive or UUID is saved in several places. I generally prefer clean install, copy of /home and maybe a few settings from /etc but not the files in /etc.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

ls  /dev/disk/by-id/
more /var/cache/debconf/config.dat  | grep /dev/disk

UUID in grub, fstab &
more /etc/initramfs-tools/conf.d/resume

---

