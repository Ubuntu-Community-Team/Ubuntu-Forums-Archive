---
title: "Two HD's partitions to One HD"
date: 2018-07-25
forum: Installation &amp; Upgrades
---

### Post by chris_sj on 2018-07-25
I have ubuntu 14 installed on one hard drive and windows on another drive. How would I put both partitions on a single drive and have grub boot from either one.

Thanks,
Chris

---

### Post by oldfred on 2018-07-26
Why?
One drive is often the standard type of install as many users only have one hard drive. 

But with two drives often better to keep both systems on separate drives.
If one drive is SSD, then perhaps better to have both systems on SSD, but store data on HDD.
Post this:
sudo parted -l

Often easier to just reinstall Ubuntu and copy data usually /home to new install. You may want list of installed apps, and perhaps some settings from /etc if you manually edited system files like grub, NFS, or others. Or have server type data web, database etc.
Good way to test that your backup of Ubuntu will let you fully restore it to new drive as you still have old install to find anything you missed.

---

### Post by chris_sj on 2018-07-26
never mind, I'll figure it out on my own.

---

