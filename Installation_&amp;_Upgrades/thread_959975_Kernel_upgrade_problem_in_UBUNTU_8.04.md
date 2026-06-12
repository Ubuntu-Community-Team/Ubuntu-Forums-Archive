---
title: "Kernel upgrade problem in UBUNTU 8.04"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by FerJon on 2008-10-26
Hello Guys,

 I am currently using Ubuntu 8.04 in my laptop. I've already updated my system until the kernel version  2.6.24-19. 

 Just recently I updated it with the newer version (Linux 2.6.24-21) but unfortunately there was an unexpected error. I do not know what it is.

 It seems that the new kernel was not registered in the boot list. How can I make this include without causing other error regarding this. 

 Actually I've tried adding it in the mnu.lst of grub but it only prompt an error after logging in.

 How can I work around it? Thanks.

ferJon

---

### Post by tommcd on 2008-10-27
First back up your menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
The run
```
gksudo gedit /boot/grub/menu.lst
```
Scroll down to the ##Debian Automagic Kernels List## section, and copy the whole section for the 2.6.24-19 kernel, including the recovery mode section, and paste it above the 2.6.24-19 entry so that it is first in the list. Leave a space between each section. Then in that section that you just pasted in, change every instance of 2.6.24-19 to 2.6.24-21, including the initrd line. Then save and exit. Reboot and you should now have the option to boot 2.6.24-21 as the first option in your grub menu. If you have trouble, post your menu.lst here and I'll take a look at it.

---

