---
title: "Configuring grub on a restored drive"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by jdege on 2010-05-09
I've been running CentOS 5 for some years. I've decided to upgrade to Ubuntu, and with 10.04 just out, this seemed like a good time.


  I'm a tad paranoid, so I started off with a new set of drives - one to install on, one to backup to, and one as a spare. I removed my existing CentOS 5 drives, and did an install, and had no problems. I installed the server version, and used the default full-disk LVM installation.


  Next, I copies my backup scripts over, edited them to work with the new configuration, and did a test backup. That worked fine, as well. Then comes the real test, could I do an install of the backup onto the spare drive? (I won't put anything of importance on a system that doesn't have a reliable backup, and if I've never done a restore, it's not reliable.)


  I booted from into recovery mode from the Ununtu install CD, with the spare drive as /dev/sda, and the backup drive as /dev/sdb. I had no trouble in partitioning, configuring LVM, formatting, making swap, or restoring the file systems. But when I got to restoring grub to the MBR, I ran into problems.


I can't list all the things I've tried, but I'm clearly not getting anywhere.  So I thought I'd ask for help.

My situation:

I've booted off of the install CD, in recovery mode.  My current root is the RAM disk created by the CD boot process.

My restored disk is /dev/sda, with root at /dev/mapper/desktop-root, where VG desktop is on /dev/sda5.  My restored boot partition is /dev/sda1.  Root is ext4, boot is ext2.

I have the restored root mounted at /mnt/restore, and the restored boot mounted at /mnt/restore/boot.

All of the grub executables and configuration files are present in the restored disk image.  How do I get grub to install to the MBR of /dev/sda, using the configuration files that are present at /mnt/restore/boot/grub?

I tried doing "grub-install --root-directory=/mnt/restore /dev/sda", but that complains that it can't find various grub child executables at /usr/bin/etc..  And, of course, they're not there, they exist only in the /mnt/restore directory tree.

So I tried to run a shell that was chroot'ed to /mnt/restore, and when I run grub-install there, I get complaints about /dev/sda not existing.  Which it doesn't, in /mnt/restore/dev, which is where the chroot'ed shell is looking.

Is there something simple I'm missing?

---

### Post by lemming465 on 2010-05-10
You probably need a richer chroot environment.  Try:```
sudo -i
cd /mnt/restore
for f in proc dev sys; do mount -o bind /$f $f; done
chroot .
grub-install /dev/sda
```

---

### Post by jdege on 2010-05-11
I booted off the install CD, and started a shell with the root directory mounted.  update-grub and install-grub /dev/sda then ran fine, but I still couldn't boot.  I dropped into a grub menu, and found that root was pointing at '(desktop/root)', and no kernel or initrd were configured/

So I booted off the install CD again, started a shell with the root directory mounted, and in it explicitly mounted /boot, reran update-grub and install-grub /dev/sda, and then everything worked fine.

---

### Post by lemming465 on 2010-05-11
Yes, if /boot is going to be a separate mount point, you want it mounted when you play with grub.  Otherwise the files go into /boot the root directory, not /boot the mounted filesystem, and the MBR is going to be pointing at the filesystem.  Mounting a filesystem onto a non-empty directory traditionally obscures the contents, which makes the whole thing very confusing.

---

### Post by dino99 on 2010-05-11
may have a look at this guide below

---

### Post by jdege on 2010-05-11
> **dino99 said:**
> may have a look at this guide below
A quick look at it shows it contains references to /boot/grub/menu.lst.

Which doesn't exist, with grub2.

Are you sure it is up-to-date?

---

### Post by oldfred on 2010-05-11
Grub writes a device.map file of all the drives it sees. If you did not have them all plugged in then the device.map may not be correct.

If it complains about a device map or to update it:
sudo grub-mkdevicemap
sudo update-grub

Example with 2 drives:
/boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb

---

