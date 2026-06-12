---
title: "Cannot boot-repair"
date: 2024-03-07
forum: Installation &amp; Upgrades
---

### Post by eljobe on 2024-03-07
When I attempt to run boot-repair from a live USB, the boot-repair program doesn't know how to repair my linux system.

Here is the pastebin:
[https://paste.ubuntu.com/p/CV4gKTVkym/](https://paste.ubuntu.com/p/CV4gKTVkym/)

It looks to me like the linux system partition /dev/sda2 is just totally hosed. When I mount it, it only shows a "lost+found" entry.

Please advise.

---

### Post by oldfred on 2024-03-07
If you cannot see your system in sda2, Boot-Repair cannot find it to use it to make repairs.
Did you somehow run commands to erase that partition?

Do you have good backups?

Have you run fsck on partition to see if that repairs partition?
To see all the ext4 partitions
Partition must be unmounted:
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sda2
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda2

Have you used  Smart Status to check if drive has issues.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

