---
title: "download packages"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by kamtaot on 2009-11-30
Hi there,

My organization has chosen to install ubunutu in 45 systems to all dev team. I could able to install the OS and installed the required softwares browsing the Ubuntu Software Centre. This has to be copied to other 44 systems. There are couple of solutions for this like making an image and dumping it in the hard disk is one. But I want to do the installation and install the softwares separately. So I want to know the location where the softwares will be downloaded by Ubuntu Software centre so that I can copy all of them in a disk and keep it ready.

Thanks in advance

---

### Post by mac9416 on 2009-11-30
Hey, kamtaot,

After installing packages on one Ubuntu computer using Software Center, you can copy the downloaded package files from the /var/cache/apt/archives directory onto a flash drive. Then you can move those to the /var/cache/apt/archives on all the other machines and install them like normal (Software Center will see the package files in the cache and not try to download them).

Note that you will need super-user priveleges to copy the files from the cache. You can use the file manager as root by running 'gksu nautilus'.

Hope that helps!

---

### Post by kamtaot on 2009-12-01
Thanks a ton!!! You solved my problem in seconds...

---

