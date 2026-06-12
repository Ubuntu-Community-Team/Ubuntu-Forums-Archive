---
title: "grub restore with grub 2"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by diehardlinux on 2010-03-10
Grub:
I never knew life could be so simple. I used a combination of two articles for help.

After a while reading this article (chroot article): [http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html#axzz0dRkAz9Oa](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html#axzz0dRkAz9Oa)

I used that article to mount the partitions using a ubuntu live cd (ubuntu 9.04). I then following the instruction on that article to mount the partitions in /mnt and /mnt/boot etc, etc....

I realized, the version of kubuntu I installed used grub2 (kubuntu 9.10).

I used this command similar to this "sudo grub-setup -d /mnt/boot/grub /dev/sde" to restore my boot partition located on sde5

ubuntu help article reference: [https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29](https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29)


hope this helps others looking for help restore their partition after a install.

---

