---
title: "GRUB Issues..."
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Job_314 on 2008-03-05
Hey guys, I've never had this issue, and it's actually quite weird. I decided to install Vista and Ubuntu on my old desktop, to setup a home LAN. 

I installed Vista, everything worked fine, but after I installed Ubuntu, I don't even see a GRUB menu... it boots straight into Vista without giving me an option. It seems as though Linux has copied files to the partition on my HD, but somehow it isn't replacing Vista's boot manager with GRUB. 

Any suggestions?
Thanks.

---

### Post by dgray_from_dc on 2008-03-05
You may want to use the Live CD to try and reinstall grub.

---

### Post by mikewhatever on 2008-03-05
Try this --> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by dstew on 2008-03-05
Yes, see the link in mikewhatever's post. One thing in that linked page that might not be clear is to use the result of the find /boot/grub/stage1 command as the argument of the root command. So, if find /boot/grub/stage1 returns (hd0,2) then the root command should be root (hd0,2)

---

