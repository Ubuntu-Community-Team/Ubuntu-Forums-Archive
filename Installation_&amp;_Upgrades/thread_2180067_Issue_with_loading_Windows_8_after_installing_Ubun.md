---
title: "Issue with loading Windows 8 after installing Ubuntu 13.04"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by Harish_Keri on 2013-10-11
Hi,

I installed Ubuntu 13.04 over pre-installed Windows 8 (from Dell). I do have backup and recovery disk for windows 8.
The problem now is that the Windows 8 OS is not recognized by Grub during boot; and I can now only login to Ubuntu.
Also, the recovery disk does not find any issues with Windows OS or the Windows boot loader.

I tried boot-repair, update-grub; but it still is the same. Please find the details in paste bin @ [http://paste.ubuntu.com/6217832/](http://paste.ubuntu.com/6217832/)

Thank you in advance for your help and advise.

---

### Post by oldfred on 2013-10-11
Welcome to the forums.
When you wrote Ubuntu over Windows you erased Windows. Is that not what you wanted?
It still has a couple of Windows boot files in the efi partition as it uses the same efi partition, but you have no Windows install nor any recovery partition on your hard drive.

---

