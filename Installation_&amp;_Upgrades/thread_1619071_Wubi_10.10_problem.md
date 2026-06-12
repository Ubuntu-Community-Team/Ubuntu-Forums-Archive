---
title: "Wubi 10.10 problem"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by kingdm on 2010-11-11
Hi everyone. :)

I tried to download the Ubuntu 10.10 Desktop Edition but it seems it is not like the previous one wherein the Wubi installer is bundled. So, I downloaded a separate Wubi installer and I run it. It seems that in the downloading part of the installation, the installer downloads the 10.04 version. Why is that? Is there no other way to install 10.10 via Wubi? :(

Thanks.

---

### Post by dino99 on 2010-11-11
i hate wubi, so for serious installation:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by cpmman on 2010-11-11
Click on the WubiGuide link in my signature.

You can install any version for which you have the iso - which HAS to be in the same directory as the Wubi.exe so copy the .exe to where your iso 10.10 is located and run it from there.

---

### Post by Frogs Hair on 2010-11-11
You can also use this link and scroll down to Wubi.exe and download it.
 [http://mirrors.xmission.com/ubuntu-cd/10.10/](http://mirrors.xmission.com/ubuntu-cd/10.10/)

---

### Post by kingdm on 2010-11-11
Thanks for your reply guys.

I decided to install Ubuntu on a separate partition.

Thanks once more.

---

