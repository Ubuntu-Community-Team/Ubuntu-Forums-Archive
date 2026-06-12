---
title: "Can't boot after install alongside Windows"
date: 2019-12-20
forum: Installation &amp; Upgrades
---

### Post by samcramer on 2019-12-20
I removed several partitions and then reinstalled Ubuntu alongside an existing Windows 7 installation.  Now grub tells me "error: no such device: <uuid>".  I'm not sure how to proceed.

I have used a boot repair disk to generate a report which I hope will be helpful: [http://paste.ubuntu.com/p/3crxgBgRVt/](http://paste.ubuntu.com/p/3crxgBgRVt/).

Thanks!

---

### Post by samcramer on 2019-12-20
Duh, "Can't **boot** after install alongside Windows."

---

### Post by deadflowr on 2019-12-20
> **samcramer said:**
> Duh, "Can't **boot** after install alongside Windows."

fixed it for you.

---

### Post by samcramer on 2019-12-20
> **deadflowr said:**
> fixed it for you.

Thanks!

I think the thing causing confusion here is the fact that grub is installed on a different drive than the system I'm booting and the BIOS is configured to boot from that other drive.  I'm making progress after configuring the BIOS settings to boot directly from the drive containing the system I'd like to boot.

---

### Post by oldfred on 2019-12-20
You seem to have some corruption on sda4, ext4 partition.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda4 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda4
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda4 

    
Your grub in sdb, refers to an UUID that does not exist. If fsck works then reinstall grub to sdb.
Do not use Boot-Repair's auto fix as that installs one grub to every MBR. You want to keep syslinux as the Windows boot loader in sda & only install grub to sdb. You can use Boot-Repair's advanced mode or manually install.

---

