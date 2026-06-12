---
title: "How to upgrade BlueZ to 5.50 on Ubuntu 18.04 on armhf architecture?"
date: 2021-06-07
forum: Installation &amp; Upgrades
---

### Post by pilot8 on 2021-06-07
We have our embedded system running Ubuntu 18.04 on armhf architecture. We use BlueZ 5.48. But we need to upgrade BlueZ to 5.50 as there is a fix that we need in this version. However, 5.48 is the latest version of BlueZ on 18.04. There is no way to upgrade to BlueZ 5.50 via "apt install".


We tried this approach to upgrade BlueZ: we downloaded BlueZ 5.50 armhf deb file and tried to install it. Then we realized it needs libc6 2.28. But the latest version of libc6 on Ubuntu 18.04 is 2.27. So we downlowded libc6 2.28 armhf deb. There are more dependencies such as libtinfo6, locales, libreadline8. We managed to install all of these deb files by using "dpkg -i xxx.deb". Finally we got BlueZ 5.50 working in Ubuntu 18.04. But we found we can't use "apt install" anymore because it complaints "libc6 is broken because it is > 2.27". Is this approach okay? Are there any potential risk by manually installing deb files? 


What is the proper way to upgrade to BlueZ 5.50 on Ubuntu 18.04 armhf architecture? Some suggested to build libc6 and BlueZ by ourselves. I tried to build libc6 and BlueZ. But then I don't know how to create deb file from the build. Plus, even if we are able to build deb file. We will end up "break libc 2.27" limitation when installing them just like we use the downloaded deb files as above. 

Thanks in advance!

---

### Post by ActionParsnip on 2021-06-07
Libc6 is very important in the OS. You may want to upgrade to Focal using a clean install and wipe the install you have. You can then use the newer bluez version.

---

