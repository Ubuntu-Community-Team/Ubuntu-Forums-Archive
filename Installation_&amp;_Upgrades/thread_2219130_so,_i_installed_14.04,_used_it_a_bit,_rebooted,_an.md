---
title: "so, i installed 14.04, used it a bit, rebooted, and got a grub command line."
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by tylerwilsonthefirst on 2014-04-23
So, I installed ubuntu 14.04 on my new asus laptop, used it a bit, rebooted, and got a grub command line. screenshot: [http://i.imgur.com/c34qOQx.jpg](http://i.imgur.com/c34qOQx.jpg) i tried several commands, boot, linux, normal, continue, no luck. I asked my linux freind, he had no idea. I tried to load bios/uefi so I could maybe switch it back to windows 8 from there, and at least have that, so I turned the computer on holding f2,f8,f10 and f12.  It skipped along to the normal grub bootloader, and I was able to select Windows or Ubuntu again. I loaded ubuntu and all was well. I rebooted to try again, and once again, I got the grub command line. I tried again holding the f keys, and it worked normally again. so... whats going on? how can i fix this so it goes straight to the normal grub bootloader? screenshot here: [http://i.imgur.com/c34qOQx.jpg](http://i.imgur.com/c34qOQx.jpg)

---

### Post by fantab on 2014-04-23
You probably damaged your grub files or lost it from the UEFI. Windows update tends to do that, otherwise not sure how.
The easiest solution is to reinstall Grub. There are two ways to do it:
1. [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") - just run the *Recommended Repair. *Next "*create a bootinfo summary"* and note down the url and post it here (just the url) if you have any problems.
AND
2. Reinstall Grub using Live Ubuntu DVD/USB. [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
   This is very useful if you don't have internet.

EDIT: It is prefered that you use the same version DVD/USB as the Ubuntu installed.

If you have changed the OS order in UEFI then restore it back to Ubuntu.

---

