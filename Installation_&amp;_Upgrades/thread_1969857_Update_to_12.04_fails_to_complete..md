---
title: "Update to 12.04 fails to complete."
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Nolind on 2012-04-30
I've updated from 11.10 to 12.04  but the update froze at the point illustrated below. Everything is working fine but I can't get the update to complete or run the update manager. It advises a partial update.  It then advised me to do the following and this was the result. It hung at the same point as the initial upgrade.  





olin@nolin-desktop:~$ sudo apt-get install -f
[sudo] password for nolin: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
nolin@nolin-desktop:~$ sudo dpkg --configure -a
Setting up memtest86+ (4.20-1.1ubuntu1) ...
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Generating grub.cfg ...
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found linux image: /boot/vmlinuz-3.0.0-19-generic
Found initrd image: /boot/initrd.img-3.0.0-19-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found memtest86+ image: /boot/memtest86+.bin
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
grub-probe: error: cannot seek `/dev/sdb'.
Found Microsoft Windows XP Professional on /dev/sda2
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
done

---

### Post by Nolind on 2012-05-01
Can anyone help please.....or is this an ongoing issue and you need time to scratch heads?

---

### Post by darkod on 2012-05-01
What is /dev/sdb? It seems to have issues with it.

---

### Post by Nolind on 2012-05-01
/dev/sdb is  a hard disc drive. One that has nothing to do with ubuntu.  I use it for backup when running windows. (Dual boot)

---

### Post by darkod on 2012-05-01
It doesn't matter if it has anything to do with ubuntu or not. The grub2 update for example scans all disks. It looks like it is getting stuck exactly during the grub2 update since it is reporting the ubuntu kernels found in between those error messages.

I would suggest disconnecting that /dev/sdb disk, and try again with dpkg. See how it goes. Connect the disk later.

And it's recommended you run a SMART test on that disk.

---

### Post by Nolind on 2012-05-01
Thanks Darkod. I disconnected the disk and ran update manager and all is well. I don't think Ubuntu likes the way that disk is formatted. Smart tests all o.k but in disk utility I didn't know what type of disk it was ....so I told it.....and for good measure created an extended partition in Linux format so perhaps next upgrade it may be able to mount it properly.

---

