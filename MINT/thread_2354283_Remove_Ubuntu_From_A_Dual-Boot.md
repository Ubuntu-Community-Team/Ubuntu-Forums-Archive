---
title: "Remove Ubuntu From A Dual-Boot"
date: 2017-03-01
forum: MINT
---

### Post by 4george2 on 2017-03-01
I'm new to Linux. I have an 80GB hard drive. A few days ago I installed Mint 18 from a live DVD. Today, also from a live DVD, I installed Ubuntu 16.04 using the defaults to have it and Mint on the same drive. After using Ubuntu for awhile I don't want to keep it. I need step-by-step help on how to remove Ubuntu and be able to return to Mint as it was originally on the drive.

---

### Post by ian-weisser on 2017-03-01
Run update-grub in Mint.
Run parted or gparted in Mint to remove the Ubuntu partition.

Those are all Mint actions, not Ubuntu actions.
If you need help doing them, please seek Mint-specific support.

---

### Post by ajgreeny on 2017-03-01
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by oldfred on 2017-03-01
Make sure you install Mint's version of grub to MBR first.
Boot into Mint and run this:
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub 

Then you will have to use a live installer, either Mint or Ubuntu or gparted's own ISO to remove partitions. You may have to swapoff or unmount swap as live installers in live mode mount swap.
You can only edit partitions that are unmounted, so you cannot use gparted in your working install on same drive.

---

### Post by 4george2 on 2017-03-01
Thank you.

---

