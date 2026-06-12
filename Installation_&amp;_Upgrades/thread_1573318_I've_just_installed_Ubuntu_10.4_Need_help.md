---
title: "I've just installed Ubuntu 10.4 Need help"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by wfcxblindx on 2010-09-12
Previous settings
grub dual boot
8.04 ubuntu
windows 7/xp

Hello ladies/gentle mens,

I've just upgraded 8.04 to 10.4
Once Installation was completed It ask me to restart; 
I've restart; 

grub boots up; I have the same settings as mention above, but on the list is still shows up 8.04 ubuntu, when i click on 8.04 it says it can't find it, since it was upgraded.  Do i need to make some changes on grub?

I'm new on ubuntu. 

Thank you in advanced, I will gratefully appreciate it. 

Alex
AKA wfcxblindx

---

### Post by Rubi1200 on 2010-09-12
Can you boot into Ubuntu (the upgraded version)?

If yes, run this command in the terminal (Applications > Accessories)
```
sudo update-grub
```Reboot.

If no, then do you have an Ubuntu CD?

If yes, boot the computer with it and post the results of the bootscript linked to at the bottom of my post.

---

### Post by wfcxblindx on 2010-09-13
Ubuntu 8.04 LTS, Kernel 2.6.24-28generic
Ubuntu 8.04 LTS, Kernel 2.6.24-28generic (recovery mode)
Ubuntu 8.04 LTS, memtest86+
Other operating systems:
Windows 7/ Windows XP SP3

----------------------------------------------------------------------------

Starting Up...
mount: mounting none on /dev failed: no such device
udevd[898]: error getting socket: Invalid argument

error initializing ntlink socket
udevd[898]: error initializing netlink socket

libudev: udev_monitor_newq_from_netlink: error getting socket: invalid argument
Segmentation fault
Gave UP waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
     - Check rootdelay= (did the systme wait long enough?)
     - check root= (did the system wiat for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/ec95405c-e84b-4895-bc98-72bb1a203c51 does not exist. Dropping to a shell!


Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

---

### Post by Rubi1200 on 2010-09-13
Hmm, clearly something went wrong with the upgrade. If you backed up all important data, it might be better just to go for a fresh install of 10.04.

---

### Post by planet81 on 2010-09-13
why not just install Grub using live CD 9.04
you need live CD ubuntu 9.04 :)

first, you must booting via live cd, do not install.. 
on terminal live cd

[FONT=Courier New]sudo grub
root (hd0,0)
setup (hd0)
quit
exit[/FONT]

just work for me :)

---

### Post by Rubi1200 on 2010-09-13
> **planet81 said:**
> why not just install Grub using live CD 9.04
you need live CD ubuntu 9.04 :)

first, you must booting via live cd, do not install.. 
on terminal live cd

[FONT=Courier New]sudo grub
root (hd0,0)
setup (hd0)
quit
exit[/FONT]

just work for me :)

The OP states that he tried to upgrade to 10.04 which uses GRUB2. Reinstalling legacy-GRUB (9.04 and earlier) does not make any sense right now.

@ wfcxblindx
If you have an Ubuntu CD, boot the computer and post the results of the bootscript linked to at the bottom of my post please.

---

### Post by wfcxblindx on 2010-09-21
Never mind; i've installed 10.4. It's all good, thanks for your help guys.

---

### Post by Rubi1200 on 2010-09-21
You are more than welcome :)

Good luck and enjoy!

---

