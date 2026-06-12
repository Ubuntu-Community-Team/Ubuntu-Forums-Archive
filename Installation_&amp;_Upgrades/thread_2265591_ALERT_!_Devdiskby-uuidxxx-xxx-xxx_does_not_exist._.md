---
title: "ALERT ! /Dev/disk/by-uuid/xxx-xxx-xxx does not exist. Dropping to a shell"
date: 2015-02-16
forum: Installation &amp; Upgrades
---

### Post by rogueit on 2015-02-16
Installed 14.04 and after successful install and reboot I get 

```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT ! /Dev/disk/by-uuid/e9399244-24c6-46bd-9786-051806f0f93f does not exist. Dropping to a shell


BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
enter 'help' for a list of built-in commands.

(initramfs)

```

```
$ ls -l /dev/disk/by-uuid
lrwxrwxrwx 1 10 E411-5D60 -> ../../sda1  
lrwxrwxrwx 1 10 e9399244-24c6-46bd-9786-051806f0f93f -> ../../sdb1
lrwxrwxrwx 1 10 df7a3fc6-d2dc-4c85-a445-8bbc02ff7c84 -> ../../sdb5



```

```

fdisk -l

Disk /dev/sda: 146.2 GB, 146163105792 bytes
255 heads, 63 sectors/track, 17769 cylinders, total 285474816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dbc22


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   277092351   138545152   83  Linux
/dev/sda2       277094398   285472767     4189185    5  Extended
/dev/sda5       277094400   285472767     4189184   82  Linux swap / Solaris

```

```
cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=e9399244-24c6-46bd-9786-051806f0f93f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=df7a3fc6-d2dc-4c85-a445-8bbc02ff7c84 none            swap    sw              0       0

```

```

blkid
/dev/sda1: UUID="e9399244-24c6-46bd-9786-051806f0f93f" TYPE="ext4" 
/dev/sda5: UUID="df7a3fc6-d2dc-4c85-a445-8bbc02ff7c84" TYPE="swap" 

```
 
If I type exit at the (initramfs) prompt the boot will complete. So how do I get around that. My first inclination would be to create a script to just simply exit out of that shell. I do not know how to do that though.
What other commands should i run to help identify the problem?

Thanks
Scott

---

### Post by oldfred on 2015-02-16
Is this an older computer or an external drive?
Also is drive sda, or sdb? Some of your info shows either. Did you install as external and now it is internal. May add to confusion and just a grub reinstall will work.

Some very old BIOS or USB external drives do not like large / (root) partitions and show this type of error. Then a / (root) of 25GB and rest of drive as /home or /mnt/data partition works. You can test by shrinking / to less than 100GB and see if it boots. You have to use live installer to shrink /.
Only about half of those I suggest this to, finds it works.

Some find just a full uninstall/reinstall of grub works. If you can boot, you can do that from inside your install, just make sure Internet is working as it has to download new copy of grub and once erased it must install new copy to work again.

Skip the chroot and you need sudo on every line.
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Other updates may help (or not?)

 #if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

   sudo update-initramfs -k all -c
sudo update-grub


 # uninstall both grub legacy & grub2 reinstall grub2 and to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
# check which drive it really is first, sda or sdb:
sudo grub-install /dev/sda
sudo grub-install --recheck /dev/sda

---

### Post by rogueit on 2015-02-16
I believe it may have a RAID card...but I am not familiar enough with linux to find out exactly

---

