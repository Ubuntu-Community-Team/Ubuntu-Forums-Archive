---
title: "New Karmic release problem"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by SK Linux on 2009-12-05
Hi.
   I just upgraded to the 15 release earlier today, and it asked me to restart after it had been installed. When I tried to log back in, though, it brought me to the grub 1.97 command line, and I have not been able to get back into ubuntu. I tried the following commands:

set root=(loop0)      (the partition where I keep ubuntu)

linux /boot/vml <tab> linuz(and so on)-15-generic root=sda2 ro

initrd /boot/initrd <tab> ........-15-generic

boot


  I should note that for the middle command, I am not totally sure of the name of the ubuntu partition (I think it is sda2), but I tried every possible combination anyway. Also, I am currently dual booting Windows XP pro and ubuntu with the windows bootloader being accessed before grub (the default wubi installation).
                       Thanks

---

### Post by jctweb on 2009-12-05
The latest update (through update manager) also stopped pre-loading gnome-panel.  I have to manually start it.

---

### Post by presence1960 on 2009-12-05
> **SK Linux said:**
> Hi.
   I just upgraded to the 15 release earlier today, and it asked me to restart after it had been installed. When I tried to log back in, though, it brought me to the grub 1.97 command line, and I have not been able to get back into ubuntu. I tried the following commands:

set root=(loop0)      (the partition where I keep ubuntu)

linux /boot/vml <tab> linuz(and so on)-15-generic root=sda2 ro

initrd /boot/initrd <tab> ........-15-generic

boot


  I should note that for the middle command, I am not totally sure of the name of the ubuntu partition (I think it is sda2), but I tried every possible combination anyway. Also, I am currently dual booting Windows XP pro and ubuntu with the windows bootloader being accessed before grub (the default wubi installation).
                       Thanks
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by SK Linux on 2009-12-06
I managed to fix it--I reinstalled ubuntu! This time I did not use Wubi--I used the Live CD and have had no further problems. I wonder why it only affects Wubi installations?

---

