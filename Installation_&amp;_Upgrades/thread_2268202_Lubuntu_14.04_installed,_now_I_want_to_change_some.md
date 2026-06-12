---
title: "Lubuntu 14.04 installed, now I want to change some things..."
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by evoblade on 2015-03-06
I installed Lubuntu 14.04, taking up a whole disk. I used the disk encryption option in the installer. Now I am wishing I left some space on the disk and I would also like to dual boot windows xp. Can I change it or do I need to nuke and pave? I would already have just reinstalled, but I struggled a bit getting YNAB running under WINE and I don't want to blow that away. Plus, I have pretty much everything installed and updated.

---

### Post by kerry_s on 2015-03-06
boot from the live cd & use gparted to resize the partition

---

### Post by evoblade on 2015-03-09
That didn't work. My working drive is encrypted. I have 

/dev/sda1    /boot (200M)
/dev/sda2    (extended partition)
/dev/sda5    / (crypt-luks FS, rest of disk, cannot be resized.)

Is there a way to decrypt my encrypted FS and then resize, or do I have to restart from scratch?

---

### Post by slickymaster on 2015-03-09
> **evoblade said:**
> That didn't work. My working drive is encrypted. I have 

/dev/sda1    /boot (200M)
/dev/sda2    (extended partition)
/dev/sda5    / (crypt-luks FS, rest of disk, cannot be resized.)

Is there a way to decrypt my encrypted FS and then resize, or do I have to restart from scratch?
I would advise you to start over from scratch. It's possible, but it would be a highly time consuming and error-prone procedure.

The encryption is handled by an extra software layer between the file system and the physical hard drive, not the file system itself. You'd have to move the whole file system (or all files) to another partition (with enough free space) or external HDD. Then, remove the encrypted container, and recreate the file system without encryption. Finally, make sure that the new file system is properly recognized by the boot loader and mount -a before rebooting.

---

### Post by Elfy on 2015-03-09
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

