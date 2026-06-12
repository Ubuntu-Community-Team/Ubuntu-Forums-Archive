---
title: "HDD/SSD cloning so that OS distinguished between the two drives"
date: 2021-11-14
forum: Installation &amp; Upgrades
---

### Post by Zlobomir on 2021-11-14
Hello,

I used the search option and couldn't find a similar topic.
I have two disks in my PC, the first one is the Ubuntu installation, the second one is an empty unformatted drive. I intend to clone the first drive to the second one, for backup and recovery in case the first drive fails.
However, I have done a similar setup before and, since both drives are always connected, after the cloning I ended with the OS being unable to distinguish between the drives, reading/writing to both of them.
How can I clone the drive, avoiding the above situation? Manually disconnecting the drives is not an option, especially because the first one is a nvme disk.
Thank you in advance.

Best regards,

---

### Post by oldfred on 2021-11-14
You cannot reboot with both drives connected as duplicate UUIDs & GUIDs are not allowed.
You can go thru and edit UUID & GUID(partUUID) entries & reinstall grub to use those new UUIDs.

It may just be faster to do a new install & restore from your normal backup. It also then proves backup has everything you need when you still have original to get more info from,  if needed. 

My new install from ISO  and booted with grub loopback into RAM takes about 10 minutes to install to NVMe & 12 min to SSD. Bit longer for my HDD and very long to my flash drives. Downloading apps from backed up list time will depend on Internet speed. Copy of /home also will depend on how much data, but my full backup (data, configuration, apps list but not system) from NVMe to USB3 SSD is very quick.
Total time for new install & configuration is typically less than an hour total. It also then cleans out all the old logs & other cruft that builds up over time.

---

### Post by MAFoElffen on 2021-11-14
Before I even vistied te thread, from the title, I knew the would be an issue with UUID & GUID...

There are two ways around that... One is to set up the second as a second member of a RAID1 or... as "a pseudo mirrored drive." 

In the second option, you create the partitions as a duplicate sizes as the first... Install to Drive two, with drive one disconnected and make it unique, then after the install, connect the original drive as the primary drive.

Then run timed jobs to rysync the changes from the first drive to mirror those changes on the second drive. With this option, exclude the system config files (hostname, other files).  

The very first time will be a long time, as it will copy "everything" over, except the excluded files. Anything after that will be less, as it will just sync what has changed. So will end up being incremental changes. 

You end up with a fail-over system drive, that is up-to-date, up to the point of where the last rsync job was run...

---

### Post by Zlobomir on 2021-11-14
Thank you for your prompt and detailed replies. I decided to make an image of the entire NVME drive to an external USB drive with Lazesoft. It took about an hour and 3-4 minutes for 161 GB of data (image size). If (when) the NVME fails, i will just restore to the new one from the image.

---

### Post by TheFu on 2021-11-14
If the UUIDs are still the same, at each boot, you'll never know which partitions are used by the OS.  UUIDs need to be unique if the storage is in the same physical machine. There's no way around that.  And if you mount (/etc/fstab) using the UUID (which is the default), then you'll need to ensure that is modified between the 2 disks.  Also, whenever grub-update runs, it will find both OSes and may not clearly differentiate which is which in the grub menu.

I don't know what I'd do.  I don't clone disks for emergency restore purposes.  I start with a minimal fresh OS install, then restore from backups that which was harmed.  There are many different solutions, but that depends on the volume managers and file systems used.  ZFS, BTRFS, LVM+ext4 ... each have different ways to deal with these things.  If you don't use any volume manager, well ... I don't have any recommendations. Sorry.

---

### Post by C.S.Cameron on 2021-11-15
GParted has an option for changing partition UUID's. You need to confirm that the UUID's shown in /etc/fstab and /boot/grub/grub.cfg match the new UUID.

---

### Post by TheFu on 2021-11-15
> **C.S.Cameron said:**
> GParted has an option for changing partition UUID's. You need to confirm that the UUID's shown in /etc/fstab and /boot/grub/grub.cfg match the new UUID.

Yep. That's handy of you have a GUI.  I always have to look up the command on systems without any GUI.  tune2fs works for ext2/3/4 file systems.  I suspect other file systems have the capability in their tools.  Another option is to mount using a LABEL= rather than the UUID=.  Then most of the partition tools can be used to edit the LABEL for each partition to ensure they are unique. Plus, humans can understand a label much better than a UUID inside the /etc/fstab.

But if btrfs is being used, the main volume and all subvolumes have the same label and the same UUID, so the *subvol=* option is still required.

For LVM LVs, I use the /dev/{vgname}/{lvname} as the mount device. This gets automatically generated by the mapper daemon at boot, so on the new, cloned disk, just rename the VG and it will be unique. For example:
```
UUID=9CE4-930A          /boot/efi vfat   utf8,umask=007,gid=46 0       1
/dev/vgubuntu/root /         ext4   noatime,errors=remount-ro 0 1
/dev/vgubuntu/home /home     ext4   noatime,errors=remount-ro 0 1
/dev/vgubuntu/swap_1 none    swap   sw      0       0
```

Or another example:
```
UUID=2471d686-fde5-4680-a75a-46c99c8b5550 /boot    ext2 defaults 0     1
/dev/hadar-vg/root        /     ext4    noatime,errors=remount-ro 0  1
/dev/hadar-vg/libvirt-lv  /var/lib/libvirt ext4 noatime,errors=remount-ro 0 2
/dev/hadar-vg/lxd-lv      /var/lib/lxd     ext4 nofail,noatime,errors=remount-ro 0 2
/dev/hadar-vg/swap_1      none          swap  sw       0     0
/dev/vg-hadar/lv-backups  /Backups         ext4 nofail,noatime,errors=remount-ro 0 2

```
Isn't that UUID ugly compared to the LVM device names?

Lots-o-options.

---

