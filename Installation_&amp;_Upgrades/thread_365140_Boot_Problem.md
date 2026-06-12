---
title: "Boot Problem"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by marco.garcia on 2007-02-19
i am a absolute linux newbie and I installed ubuntu on my new hd a week ago and, I installed windows xp on the same hd later. now windows boots without giving the option to boot ubuntu. 

What do I have to do now?

Thanks a lot,

marco

---

### Post by mikewhatever on 2007-02-19
By installing Windows, you overwrote the MBR. Here is the fix: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

There is a lot of stuff, so I suggest Recovering GRUB Manually section.

---

### Post by erkki70 on 2007-02-19
Hi,
You should have a look here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Good luck ;-)

---

### Post by marco.garcia on 2007-02-20
Hi thanks for the answers. I followed the instructions and when it came to the part of setup (hd0,1) it did nothing windows was still booting so I wrote setup (hd0) and now only linux boots without giving me the option to boot windows.

---

### Post by mikewhatever on 2007-02-20
You probably need to manually add the Windows boot entry to GRUB menu. It is not too hard and the important thing is that GRUB is now restored. To edit GRUB menu, type in the terminal
sudo gedit /boot/grub/menu.lst

then add the following entry to the very end of the menu
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


This assumes you have one HDD and Windows is on the first partition. If you have a different setup, post the output of 
sudo fdisk -lu

---

