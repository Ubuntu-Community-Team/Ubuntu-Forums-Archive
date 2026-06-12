---
title: "Cannot boot ubuntu - grub2 / device.map"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by skewbie on 2010-08-25
Hi

I used to have 2 HDDs for ubuntu: 1 x 80GB and 1 x 500GB

The 500GB disk was my /home directory and is now used exclusively for Windows 7. I have now moved /home to the 80GB drive and have modified /etc/fstab to point /home to /home rather than /dev/sdb1. 

However, I cannot boot into ubuntu. I have tried using Super Boot Disk cd-rom but still no joy. I think I need to fix grub and have tried by booting into a Live-CD and following a tutorial I found on the forums but it complains about not being able to find a device.map

I guess this has something to do with the fact that the 500GB HDD is now gonoe but am not sure how to resolve this issue. I found an article about how to recreate this file but the command failed.

Any advice would be appreciated.

Kind regards

Steve

---

### Post by mikewhatever on 2010-08-25
What's Super Boot disk and why did you use it? What is the problem exactly? 'Can not boot Ubuntu' is really not a whole lot of info, unless you provide details.

---

### Post by Rubi1200 on 2010-08-25
Please boot the computer with the LiveCD and post the results of the bootscript linked to at the bottom of my post.
Thanks.

---

