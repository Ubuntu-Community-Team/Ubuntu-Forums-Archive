---
title: "Attempt to mount ... type vfat in SCSI1 failed"
date: 2021-03-28
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2021-03-28
I'm on an HP ProBook 450 G3
I'm re-partitioning and doing a fresh install of Ubuntu 20.04.2 LTS.

I get the error message 
Error Message:

"The attempt to mount a file system with type vfat in SCSI1 (0,0,0), partition #1 (sda) at /boot/efi failed.

You may resume partitioning from the partitioning table."

I remember from the last time I did a reinstall I had to have an EFI partition which is a GPT disk, flags ESP and Boot. That had something to do with UEFI. So that's what I'm doing. That will be a small partition.
I also wil have:
/dev/sda1, EXT4, / (root), 42GB
/dev/sda2, EXT4, /home, remaining disk space.

```

fdisk -l
Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D8457F12-33C1-4E11-89AD-EE4DF132E8CA

Device         Start        End    Sectors   Size Type
/dev/sda1       2048    2099199    2097152     1G EFI System
/dev/sda2    2099200  106956799  104857600    50G Linux filesystem
/dev/sda3  106956800 1953523711 1846566912 880.5G Linux filesystem

```

How do I resolve the problem which the error message pointed out? I want to complete this install.

I tried
sudo mkfs.vfat -F 32 /dev/sda1 mkfs.fat 4.1
and now the install is progressing. This is the farthest I've gotten so far. I hope that resolved the problem.

---

### Post by webmanoffesto on 2021-03-28
Install failed.
Log file
```
ubuntu@ubuntu:/var/log$ tail -f /var/log/installer/debug
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:17: Warning: Source ID 770 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:133: Warning: Source ID 846 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:17: Warning: Source ID 919 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:133: Warning: Source ID 1002 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e.g. happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This cou



```
What could the problem be?

---

