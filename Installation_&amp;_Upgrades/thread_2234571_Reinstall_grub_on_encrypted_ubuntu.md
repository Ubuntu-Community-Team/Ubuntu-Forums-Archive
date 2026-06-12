---
title: "Reinstall grub on encrypted ubuntu"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by hojjat on 2014-07-15
I have two partitions on this machine: /dev/sda1 which contained my boot loader, and /dev/sda2 which is an LVM encrypted partition. Inside that there is /dev/sda5 which is the / (root) for my machine.

I accidentally deleted /dev/sda1 and now GRUB complains that "ELF header smaller than expected" and fails to boot. I am trying to figure out how to reinstall GRUB so it would boot from /dev/sda1, but then load the root from the encrypted volume. Any advice is appreciated.

---

### Post by hojjat on 2014-07-15
I just tried boot-repair but it didn't solve my problem. Here is its logs: [http://paste.ubuntu.com/7799232/](http://paste.ubuntu.com/7799232/)

---

### Post by oldfred on 2014-07-15
Did Boot-Repair ask for your passphrase to mount your encrypted partitions?
That would have to be done.

If you totally erased sda1, you have to go back into fstab and update the /boot entry with new correct UUID for sda1.

You then should be able to run Boot-Repairs full uninstall and reinstall of grub, but also add a command to install the most recent kernel.

Run these also when chrooted into your install with Boot-Repairs uninstall & reinstall of grub, # is comment do not copy nor type anything after #.
       apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

update-grub

---

