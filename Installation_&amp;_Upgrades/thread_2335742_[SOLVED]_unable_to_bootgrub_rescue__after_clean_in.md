---
title: "[SOLVED] unable to boot/grub rescue  after clean install"
date: 2016-08-31
forum: Installation &amp; Upgrades
---

### Post by saou on 2016-08-31
My old laptop was running xubuntu 14.04 LTS.  I did a fresh install (erase entire disk) of linux mint xfce 18 (based on 16.04); upon reboot I got "grub rescue".  I installed boot repair disk on unebootin and performed recommended repairs.  Upon reboot I can now see the boot manual but I still can't boot into linux.  Here's the log of boot repair:
  [http://paste.ubuntu.com/23117738/](http://paste.ubuntu.com/23117738/)

After I shutdowned the laptop and reboot I now get grub rescue.  I have not attempted to repair the boot loader again.  When I typed "ls" in grub rescue I got
   (hd0), (hd0,msdos5), (hd0,msdos1)
Only (hd0,msdos1) turns anything useful:
   ls  (hd0,msdos1) -->  Filesystem is ext2
which is weird since it is supposed to be ext4?

Note: Before I tried linux mint, I tried xubuntu 16.04 and linux mint 17.2 (based on 14.04) and even the ubuntu minimal install iso; I got the same grub rescue error.  I did not try to repair boot loader in those installations.

--------------------------------------------------------

Solution:   I stumbled upon a strange solution (?) to my grub problem based on the "ext2" message mentioned at the end of my question + the last post in 

   [https://askubuntu.com/questions/571295/how-to-solve-grub-rescue-and-or-mounting-hard-drive-problem](https://askubuntu.com/questions/571295/how-to-solve-grub-rescue-and-or-mounting-hard-drive-problem)

Specifically, I restalled linux mint 18 xfce from scratch again, but this time I repartitioned the disk using ext2 instead of ext4.   After installation and upon reboot I still got grub rescue.  Run boot disk repair again and that seems to solve the problem and remains so after a couple of reboot.  

What's strange is that in my previous 14.04 installation the HDD was (auto)partitioned using ext4.

---

