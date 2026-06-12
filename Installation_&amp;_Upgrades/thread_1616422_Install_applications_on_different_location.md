---
title: "Install applications on different location"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by shantanu18 on 2010-11-08
A question is arise on my mind about the software installation in ubuntu. Is there any way that i can install applications on any location (directory /partition) ? If we keep the installation file on other drive and just keep the link of that file/folder on root directory (/usr /bin /usr/sahre) then we can save our space of root directory. I found several times that my root partition is full after installing some applications. It is so painful to shrink or reallocation of root partition. Maybe this procedure of software installation will be helpful for the people who are already created low spaced root partition.
If anybody know anything about this issue then please response. I searched in google but can not get any helpful post.
Thanks in advance!

---

### Post by dino99 on 2010-11-08
you might follow a standard installation with 3 partitions:

- /: root, bootable, ext3 or ext4 format, ~ 12 Gb
- swap: ~ 2Gb
- /home: unlimited space to store your apps/data/settings, ext3 or ext4 format

---

### Post by shantanu18 on 2010-11-08
Thanks dino99 for your reply. Actually i just want to know that is there any way to install applications on my desire location?
Thanks again..

---

### Post by dino99 on 2010-11-08
> **shantanu18 said:**
> Thanks dino99 for your reply. Actually i just want to know that is there any way to install applications on my desire location?
Thanks again..

yes of course (if you are ready to fight with links and symlinks :()

---

