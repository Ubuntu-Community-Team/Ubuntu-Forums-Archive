---
title: "Install to UFS"
date: 2024-10-22
forum: Installation &amp; Upgrades
---

### Post by open4junk on 2024-10-22
I am trying to repurpose an hp 15-fd00xx which uses universal flash storage (128GB). I have verified with hp support that this pc does use UFS.
I installed ubuntu 20.04 and everything seemed to have installed normally.
However, it does not boot and it drops back to initramfs prompt during the b oot process.
I have rebooted with the live usb and can see the ubuntu files on the 128GB flash storage.
I have searched the internet and found one posting on askubuntu.com about booting Ubuntu 22.10 off Universal Flash Storage but I do not know how to do the first instruction which is: 'Mount the root partition of your Ubuntu installation to /mnt'
The remainder of the instructions look to be simple enough to follow.
I am just an average user trying to learn more about linux, so any help with the above issue would be most appreciated.

thx

---

### Post by grahammechanical on 2024-10-22
I will start the discussion.

What install options did you use? Erase disk and install Ubuntu? What partitions did the installer create?

Regards

---

### Post by open4junk on 2024-10-22
Yes, I selected erase disk and install Ubuntu. Partitions sdb1 (efi) and sdb2 (root).

---

