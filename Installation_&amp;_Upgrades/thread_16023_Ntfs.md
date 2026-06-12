---
title: "Ntfs"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by dado on 2005-02-18
how to read data from ntfs?
I mean how to mount ntfs partition
I have kernel that i get with ISO image v4.10
Thanks

---

### Post by Adrenal on 2005-02-18
[QUOTE=dado]how to read data from ntfs?
I mean how to mount ntfs partition
I have kernel that i get with ISO image v4.10
Thanks[/QUOTE]
 Assuming its not sata, and assuming it is on the first sector of your hdd
sudo mkdir /mnt/cdrive
sudo mount /dev/hda1 /mnt/crdrive -t ntfs -r -o uid=(your usename)

---

### Post by Jorge on 2005-02-18
You can read this Wiki article:

[AutomaticallyMountMSWindowsPartitions](http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions) 

I hope this will help you. Be carefull of using the read-only option (ro) or you will destroy your NTFS partition data

Jorge

---

### Post by hndrcks on 2005-02-18
To make this permanent, do two steps:

Create a directory in /mnt for the ntfs folder

sudo mkdir /mnt/data

The edit file /etc/fstab and add a line like this

/dev/hda1       /mnt/data ntfs umask=0222 0 0

where /dev/hda1 points to the ntfs partition and /mnt/data points to the mount point.

From the linux-ntfs page [http://linux-ntfs.sourceforge.net/info/ntfs.html#4.9](http://linux-ntfs.sourceforge.net/info/ntfs.html#4.9)

"umask is a filter of permissions, so it works in the opposite way to chmod. Full permissions are equivalent to 777 (rwxrwxrwx). A umask of 0222 (-w--w--w-) leaves 555 (r-xr-xr-x)."

---

### Post by dado on 2005-02-18
Thank you! :grin:

---

