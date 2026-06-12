---
title: "how to get ubuntu to see and mount fat32 partion on dif drive"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by madtrapper on 2006-02-21
ok well i am new to linux sick of uncle bill so here i am.i have 2 to hard drives hda1 has winxp ntfs and a second partion with fat32 fdisk shows fat32 as hda5. hdb has ubuntu and elive on it.. if i type

sudo mkdir /media/windows
then type
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
in terrminal win xp mounts and i can veiw files but as it is ntfs can't write to it or copy from it.so made the fat32 partion hoping i could write to it and copy from it as linux dosn't have drivers for my cannon printer/scanner. but nothing i do seems to work to get it mounted. appreciate any help .thanks

---

### Post by aysiu on 2006-02-21
Do this: ```
sudo umount /dev/hda5
sudo mkdir /fat_partition
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` If there's a line that has /dev/hda5 in it, replace it with this one (if there isn't a line, just add this one): ```
/dev/hda5 /fat_partition vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X), confirm (y), and exit (Enter). Finally ```
sudo mount -a
```

---

