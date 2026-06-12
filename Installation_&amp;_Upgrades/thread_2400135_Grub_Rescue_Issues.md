---
title: "Grub Rescue Issues"
date: 2018-09-03
forum: Installation &amp; Upgrades
---

### Post by opeoluwa5520nigeria on 2018-09-03
After upgrading my system from Ubuntu 16.04 (pre-installed) to Ubuntu 18.04, I ran into the following problem: Anytime I power on, it goes into Grub Rescue, and I cannot go further. Please tell me what to do to address this issue. It's really bad. How I wish that I never upgraded!!!

---

### Post by oldfred on 2018-09-03
Try enter or exit.
  or try 
configfile (hd0,gptX)/boot/grub/grub.cfg  - where gptX is your Linux partition.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

