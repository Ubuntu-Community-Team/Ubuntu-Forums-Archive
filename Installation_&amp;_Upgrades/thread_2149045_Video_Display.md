---
title: "Video Display"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by kat47 on 2013-05-27
Hi...Ive installed ubuntu 12.04.02, i installed using something else option, which should ,on reboot display options to boot ubuntu or windows 7.
I cant see this option because  on reboot a message is displayed on my monitor which says' cannot display this video mode'.
After a while ubuntu boots fine.
Can some one please tell me what may be wrong and how i can enter the boot screen so i can select which OS to boot into.

---

### Post by fantab on 2013-05-27
Try:
gksudo gedit /etc/default/grub

In the file that opens check for the line: "#GRUB_GFXMODE=640x480" change 640x480 to whatever your Monitor's native resolution is. Remove "#" from the beginning of the line. Save the file and Run: *sudo update-grub* from terminal.

Reboot and see if the issue is fixed.

---

### Post by kat47 on 2013-05-27
Yea fixed it...at least it boots in to ubuntu without any error messages....cheers fantab:) But im still not getting boot screen to choose which OS i want to boot in to:confused:.OOPS I deleted my windows7 partition...went to reinstall...built in graphics have gone on my motherboard...SIGH...will have to buy a graphic card now. Could explain earlier problems with monitor.So using other desktop. What a day:D.

---

