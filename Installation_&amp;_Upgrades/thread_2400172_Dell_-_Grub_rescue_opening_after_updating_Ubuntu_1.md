---
title: "Dell - Grub rescue opening after updating Ubuntu 16.04 to Ubuntu 18.04"
date: 2018-09-03
forum: Installation &amp; Upgrades
---

### Post by opeoluwa5520nigeria on 2018-09-03
Am also having the same problem. I updated my Dell 5520 pre-installed with Ubuntu 16.04 to Ubuntu 18.04. After working normally for one week, it started to go into Grub Rescue after I powered it on. All attempts to correct this error have failed. What to do? Please address this urgently.

---

### Post by oldfred on 2018-09-03
While same issue, the thread you were in is not solved and that user had an HP.
I recently had a grub rescue, but knew my install was in sda3, and this worked:
configfile (hd0,gpt3)/boot/grub/grub.cfg
       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052) 
    
If you do not know partitions you should be able see them with ls and drill down.
Or:
 grub rescue:
If you're in the GRUB rescue shell the commands are different, and you have to load the normal.mod andlinux.mod modules:
grub rescue> set prefix=(hd0,3)/boot/grub
grub rescue> set root=(hd0,3)
grub rescue> insmod normal
grub rescue> normal
grub rescue> insmod linux
grub rescue> linux /vmlinuz root=/dev/sda3
grub rescue> initrd /initrd.img
grub rescue> boot 

If you still cannot boot, use your Ubuntu live installer.

 Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

