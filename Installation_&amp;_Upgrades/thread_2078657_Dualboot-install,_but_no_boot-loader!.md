---
title: "Dualboot-install, but no boot-loader!"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by Askel on 2012-10-31
I just installed ubuntu next to windows 7 in my new laptop. With choosing automatic partitioning Grub didn't get installet. It came up a window saying it couldn't be installed and that this was a critical error.
So I reinstalled it and this time choose to manually set up the partitions. I didn't delete any partitions, only created new ones and resized the old. 

First I created partition with boot, then one with root, one with home and one with swap. The installation went without any hassle, but when I restarted the computer the bootloader didn't came up. Windows just started automatically.

What did I do wrong?

The partitioning looks like this:
/dev/sda
/dev/sda1 fat16              41mb
/dev/sda2 ntfs                788mb
/dev/sda3 ntfs                90000mb
/dev/sda5 ext4 /boot     500mb
/dev/sda7 ext4 /            39998mb
/dev/sda8 ext4 /home    168733mb
/dev/sda6 swap              19999mb

---

### Post by darkod on 2012-10-31
You can try a fast way to add it from live mode, but most probably you will need the longer way... Lets see.

The short way from live mode and using the partition scheme you gave us, is:
```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and see if it worked. Note that this will overwrite windows bootloader on the MBR and if grub2 files are missing it might not work until you do the longer procedure.

---

### Post by Askel on 2012-10-31
Aiit... guess I'll take the leap then and do it. I'll get back to you about how it ends :guitar:

> **darkod said:**
> You can try a fast way to add it from live mode, but most probably you will need the longer way... Lets see.

The short way from live mode and using the partition scheme you gave us, is:
```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and see if it worked. Note that this will overwrite windows bootloader on the MBR and if grub2 files are missing it might not work until you do the longer procedure.

---

### Post by darkod on 2012-10-31
In case you want to be prepared in advance, or try to longer route right away, here is one of my posts for the full chroot procedure to completely purge grub2 and reinstall it:
[http://ubuntuforums.org/showpost.php?p=11858371&postcount=29](http://ubuntuforums.org/showpost.php?p=11858371&postcount=29)

Note that in your case and since you have separate /boot, instead of the very first line in the first block, you need to do:
```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda5 /mnt/boot
```

After that the procedure is identical, continue with the rest of the commands in the first block, and the other blocks. Only the mounting of the correct root and /boot partitions is different.

---

### Post by Askel on 2012-10-31
Allright. Done it and the bootloader comes up. Ubuntu started without any issues. I bow to your wisdom!

edit: the short version that is.

---

