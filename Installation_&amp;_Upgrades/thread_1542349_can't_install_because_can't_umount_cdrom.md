---
title: "can't install because can't umount /cdrom"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by francoise_peace on 2010-07-30
Hello, I managed to boot from hard disk, everything works ok. But Gparted has a bug, it works in Live Hard Disk, but not when I click the install icon because it can't umount /cdrom. But I solved that by formatting ext4 and swap area from gnome-panel Live Hard Disk and only put mount point / after click on install.

But problem stroked back:  install is not possible because it wants to umount itself before installing, wich cannot be possible. I'm installing it in a new place /dev/sda5. Live Hard Disk is booting from /dev/sda3.

ubuntu@ubuntu:~$ df -h | grep sda
/dev/sda3             2.0G  726M   1.3G  36% /cdrom
/dev/sda1              43G   17G   26G  41%  /media/Windows
/dev/sda2              21G  250M   20G   2%  /media/Documents
/dev/sda5              47G  180M   45G   1%  /media/Ubuntu

I'm not putting error messages because they're in french. it just says: can't continue because can't unmount /cdrom.

---

### Post by honkyusa on 2011-06-06
read Note#2 at the bottom of this link.



[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

