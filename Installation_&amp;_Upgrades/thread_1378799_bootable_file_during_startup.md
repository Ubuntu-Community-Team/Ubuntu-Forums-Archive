---
title: "bootable file during startup"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by ravi12355 on 2010-01-11
first I installed the linux ubuntu then i installed window7 in my laptop. During startup it is not showing bootable file like 
Linux ubuntu 9.04
other OS
windows7.
could anyone tell me where such a file is located how can i change those settings.

---

### Post by presence1960 on 2010-01-11
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by shredder12 on 2010-01-12
I think since you installed windows 7 after installing Ubuntu. It has overwritten your mbr. So, I guess you will be directly get booted into windows 7 without any option for booting into Ubuntu.. 
If that's true then you probably have to fix your mbr. This link might help you out. 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by presence1960 on 2010-01-12
> **shredder12 said:**
> I think since you installed windows 7 after installing Ubuntu. It has overwritten your mbr. So, I guess you will be directly get booted into windows 7 without any option for booting into Ubuntu.. 
If that's true then you probably have to fix your mbr. This link might help you out. 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That is why I asked him to run the boot info script so I can give exact commands to restore GRUB.

---

