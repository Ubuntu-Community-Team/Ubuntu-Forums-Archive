---
title: "Disk encryption with separate home drive"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Ceiber Boy on 2012-04-28
I'm now looking to install Ubuntu 12.04 onto my machine using the alternate iso. To speed up the performance of my machine in thinking of buying an SSD for installing the OS, and use my current HDD for the home directory.

Taking as red that I will back up my data and be left with two clean drives.

Questions:
Will enabling disk encryption encrypt both the SSD and the HDD?
Will I need to encrypt it separately using home folder encryption?

---

### Post by sparklyprgs on 2012-04-30
Enabling encryption ecrypts the whole target drive (except /boot) so the SSD will be encrypted, but not the HDD.
As to the second question, since /home will by default be on your SSD it will be encrypted, but if you manually select to have it on your HDD, you'd need to use home folder encryption - but I've never done such an install so YMMV.

---

### Post by irw on 2012-04-30
The system I am using should work for you:

Using the alternative install CD, I choose manual partitioning.

Boot partition: unencrypted, about 200MB
System partition: Encrypted, then LVM containing the root file system and swap
Home partition: Encrypted, then formatted as Ext4 and mounted as home.

This will initially ask you for two passphrases - one to unlock the system disk and the second to unlock the home partition.
I ge around this by creating a keyfile, then adding this to the home partition with cryptsetup. change /etc/crypttab to use the key file, and it works perfectly.

I don't bother with home folder encryption as offered by the installer - this is separate and different to encrypting the disk or partition.

---

### Post by Ceiber Boy on 2012-04-30
> **irw said:**
> The system I am using should work for you:

Using the alternative install CD, I choose manual partitioning.

Boot partition: unencrypted, about 200MB
System partition: Encrypted, then LVM containing the root file system and swap
Home partition: Encrypted, then formatted as Ext4 and mounted as home.

This will initially ask you for two passphrases - one to unlock the system disk and the second to unlock the home partition.
I ge around this by creating a keyfile, then adding this to the home partition with cryptsetup. change /etc/crypttab to use the key file, and it works perfectly.

I don't bother with home folder encryption as offered by the installer - this is separate and different to encrypting the disk or partition.

Thank you both for your answers to my questions.

The quoted way of setting up the system sounds interesting, I'll have a crack at doing this.

Thanks

---

