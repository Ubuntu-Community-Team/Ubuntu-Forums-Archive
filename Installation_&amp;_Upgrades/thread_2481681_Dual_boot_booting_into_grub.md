---
title: "Dual boot booting into grub"
date: 2022-12-06
forum: Installation &amp; Upgrades
---

### Post by min2op on 2022-12-06
I have had a dual boot laptop for a while and normally on startup it would load into a dual boot menu. For some reason yesterday it started by loading into grub and now i cannot access my ubuntu os at all says i need to load the kernal first i have tried to set the prefix but i have no partition that exists such as (hr0,1)/boot/grub to set it too.


I tried ubuntu on a live image and have the used boot repair for the paste bin below.
[https://paste.ubuntu.com/p/mt2C8xzkQZ/](https://paste.ubuntu.com/p/mt2C8xzkQZ/)


Any help would be appreciated

---

### Post by tea for one on 2022-12-06
Line 67 - 1 OS detected
Line-69 - OS#1:   Windows 10 or 11 on nvme0n1p3
Line 139 - nvme0n1p6 615653376  997859327 382205952 182.3G Linux filesystem

It looks like your Ubuntu system was on nvme0n1p6 but there is no file system on this partition as shown by lines 154 and 169.

Were you using Windows 10 to manage partitions?
Do you have data backups from both systems?

---

### Post by min2op on 2022-12-06
No it was windows 11 and i have no data back ups for ubuntu

---

### Post by min2op on 2022-12-06
No to both questions

---

### Post by min2op on 2022-12-06
Ive tried to view files from windows using linux reader but its  having none of it

---

### Post by oldfred on 2022-12-06
Do not attempt to read Linux data from Windows. Tools that try that are very unreliable.
If you want shared data, create a separate NTFS data partition and make sure to always have Windows fast start up off, so hibernation flag not set on that partition.

You can try fsck to see if it will repair. Otherwise it is reinstall & restore from backup.
And that is why you must have good backups.

From Ubuntu live installer.
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p6
sudo e2fsck -f -y -v /dev/nvme0n1p6

---

