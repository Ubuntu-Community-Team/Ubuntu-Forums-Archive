---
title: "Help: Going to format and re install windows."
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by sarin_cv on 2009-11-22
Hi..I am going to format windows partition and reinstall it. I need to take precautions since It will overwrite my boot loader. what is the procedure to backup and restore grub?

---

### Post by darkod on 2009-11-22
Not sure of any procedure but the procedure to restore grub or grub2 from ubuntu liveCD are rather simple. You boot with the ubuntu CD, type few lines of code and that's it.

---

### Post by hal10000 on 2009-11-22
You can backup your current mbr to a file. All you have to know is where you installed your grub. e.g. if you installed it into the mbr of your first harddrive (/dev/sda), the command would be this:
```
sudo dd if=/dev/sda of=/home/your_username/mbr.backup bs=512 count=1
```
This command stores the mbr  /dev/sda in your home directory under the name mbr.backup

To restore it back to the mbr of /dev/sda, the command is:
```
sudo dd if=/home/your_username/mbr.backup of=/dev/sda bs=512 count=1
```

---

### Post by oldfred on 2009-11-22
It is probably saver to reinstall. While it may be good to have a backup of the MBR, if you change partitions in anyway or the partition number/UUID's change because of the changes, your copy of the MBR will not be correct. 

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by sarin_cv on 2009-11-23
I selected the default option to save boot-loader during install. I think it was in hd0.

---

