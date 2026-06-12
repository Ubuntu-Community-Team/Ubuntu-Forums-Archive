---
title: "windows menu does not exist in grub menu list"
date: 2016-10-04
forum: Installation &amp; Upgrades
---

### Post by zahereel-i on 2016-10-04
Hi, I had install ubuntu 14.04.5 on my laptop which has windows 8.  I shrinked my D:/ drive..... where I keep my data to install ubuntu. Then after successfully installing ubuntu using the something else ...option. The system boots up without popping up the grub menu. To fix the issue I followed  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) this guide and installed Boot-repair on my sda (my ubuntu is on extended partition...sda5).... Yup the grub menu came out on boots up ....but.. there is no menu for windows 8... I am puzzled... can someone help pls...:confused: . The web address from boot-repair for the fix attempt I made is given at [http://paste.ubuntu.com/23274117/](http://paste.ubuntu.com/23274117/)

Tq

---

### Post by yancek on 2016-10-04
Your problems is noted about half way down the boot repair output page.   No Linux system will mount a windows hibernated partition  due to the  risk of damage to the partition.  You need to shut down hibernation or  fastboot in the BIOS and may have to find some way to boot into windows  to turn off hibernation.  I don't use windows/UEFI so hopefully someone  with a little more familiarity will post.  If you had fully shut down  windows and turned off hibernation before your install, I doubt you'd  have this problem.
> The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting)

---

### Post by Mark Phelps on 2016-10-04
One more thing ... you will not get a "Windows Menu" in GRUB.  

Windows creates its own boot menu when it detects more than one thing it can use for booting, or more than one Windows OS. That menu will NOT be seen in GRUB.

What you will see is a separate entry in GRUB for each partition that contains Windows boot loader files.

---

### Post by zahereel-i on 2016-10-04
Thanks Yancek and Mark Phelps 4 yr reply.... I ams till figuring out how to boot my window thru fastboot.....

---

