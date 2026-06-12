---
title: "lost my Grub Win7 menu item [dual boot]"
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by Scott_Bale on 2014-09-12
I had dual boot working until this morning. I was able to boot (via Grub) into either ubuntu 12.04 or Windows 7.

boot-repair output: [http://paste.ubuntu.com/8328101/](http://paste.ubuntu.com/8328101/)

The last time I was able to boot into Windows 7 was yesterday. Last night, while booted into ubuntu I did a dist-upgrade including a kernel upgrade (3.13.0-32-generic to 3.13.0-35-generic it appears). This morning the GRUB option for Win7 was no longer available. I can boot into ubuntu (current or previous versions) with no problem.

Any help appreciated.

---

### Post by yancek on 2014-09-12
I'm not sure this will solve your problem but, the simplest thing to try is to boot Ubuntu and open a terminal and run:  sudo update-grub
Are both systems on the same hard drive?  Did you check the grub.cfg file on Ubuntu to verify you still had a windows menuentry?

---

### Post by Scott_Bale on 2014-09-12
Thanks for quick reply. Yeah I had tried sudo update-grub, no luck. Yes I had checked the /boot/grub/grub.cfg file - the menuentry is gone. I assume that file got regenerated due to dist-upgrade. (I may have hand-edited it at some point in the past to add the windows menuentry, although I don't recall doing that.)

---

### Post by Dennis N on 2014-09-12
Your boot info script shows sda2 failed to be mounted (line 23 - unknown filesystem) so the Windows installation may still be there. Your boot entry is missing because the windows bootloader on sda2 can't be accessed. /etc/grub.d/11_win7 generates its entry (see line 1076).

Unrelated, but you have a large number of kernels installed (see lines 1137 - 1181). You might consider removing the old kernels.

Someone with more expertise with Windows boot repair will have to respond with a solution to the Windows problem which may be repairable.

---

### Post by yancek on 2014-09-12
Given the incredibly large number of kernels you have, are you sure that windows is not on the menu?  With all those kernels you could not possibly see all the entries unless you use the down arrow key when you see the Grub menu to get to the end of it.  There actually is a windows entry in grub.cfg beginning on line 1076.  Do you have 11_win7 file in the /etc/grub.d directory?  If you don't see the windows at the end of the boot menu, try running:  sudo os-prober, then sudo update-grub.  Watch the output.

   > (I may have hand-edited it at some point in the past to add the windows menuentry, although I don't recall doing that.) 		

If you do that and don't put an entry in the /etc/grub.d directory in one of the files, it will not be there after running update-grub.

---

