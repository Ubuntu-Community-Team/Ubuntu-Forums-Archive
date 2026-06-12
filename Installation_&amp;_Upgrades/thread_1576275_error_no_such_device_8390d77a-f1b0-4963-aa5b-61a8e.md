---
title: "error: no such device: 8390d77a-f1b0-4963-aa5b-61a8e3c4e203"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by keisaachi on 2010-09-17
Hi,

I tried to install ubuntu on an Acer Netbook, and, after the installation, a message such as the following appeared.

error: no such device: 8390d77a-f1b0-4963-aa5b-61a8e3c4e203
grub rescue>

Please help

Thank you much!

---

### Post by Fafler on 2010-09-17
For some reason, your harddrive UUID has changed. Reboot and just before this happens, press shift or ESC to get to the grub menu. Press E for edit and change the part of the commandline from root=8390d77a-f1b0-4963-aa5b-61a8e3c4e203 to root=/dev/sda1 and follow to instructions to boot the system. I'm not sure if Ubuntu fixes this itself after booting successfully, so get back to me if the problems persists.

---

### Post by Rubi1200 on 2010-09-17
Hi,
if this is a Wubi install, see here for the error you are receiving:
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

and also here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> **[COLOR=Red][SIZE=3]Important Note to Wubi (Windows Ubuntu) Users: Grub Update results in "No Such Disk":[/SIZE][/COLOR] **
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that Grub 2 was installed in the MBR and/or on the  Windows partition. To correct this, restore the Windows bootloader using  this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by keisaachi on 2010-09-17
Thank you all.

I pressed Esc or Shift, but it didn't get me anywhere.  

I also found a link "How to fix boot manager in ubuntu"
[http://www.ehow.com/how_6503785_fix-boot-manager-ubuntu.html](http://www.ehow.com/how_6503785_fix-boot-manager-ubuntu.html)

but I can't mount neither reinstall the boot manager.

To be more clear about my situation...
My netbook had Window XP, and when I installed ubuntu, I chose to erase the whole disc and just install ubuntu.

I'm new to ubuntu.  Base on my research, I understand that I need to fix GRUB boot manager, but I don't know how.

Please help. 

Thank you!

---

### Post by Rubi1200 on 2010-09-17
Hi,
before you go ahead and try something please boot the computer with the Ubuntu CD and choose to try not install.

Then, post the results of the bootscript linked to at the bottom of my post.

If there is a problem with GRUB, the results should tell us.

Thanks.

---

