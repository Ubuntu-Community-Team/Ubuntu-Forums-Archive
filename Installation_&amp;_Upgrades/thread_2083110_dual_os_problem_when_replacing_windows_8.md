---
title: "dual os problem when replacing windows 8"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by coolguysraju on 2012-11-11
Hi,
I have two os as primary window 8, 90 days trial version and ubuntu 12.10  winsows 8 in 64 bit and ubutu 12.10 in 32 bit and i have installed update software and update of ubuntu by using slow internet connection. My question is that after 90 days i have to replace windows 8, 90b days trial by windows 8 full activation,during the change of window 8, i have to format my windows, in that case is ubuntu 12.10 also to be reinstall or not, if to be reinstall then how to get my update and software back to new installed ubuntu withouting downloading in new ubuntu installtion.

---

### Post by oldfred on 2012-11-11
Windows should reinstall to the NTFS partition with the boot flag or the two partitions. Then all you have to do is reinstall the grub2 boot loader to the MBR.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

But if you want Ubuntu to be 64 bit you have to do a total reinstall. You then want to fully backup /home. If a separate partition it is a bit easier to do the clean install. You may want a few settings from /etc if you manually made any system settings (video, networking, grub). And if you have added a lot of applications you may want to export a list of all installed apps to make it easy to reinstall.

---

