---
title: "Confused on Install"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by JtrickZ on 2013-05-17
Hi guys, I am building a new linux build and am having a hard time grasping how to properly install ubuntu server or desktop in my application. 

The build will be setup as a comprehensive server, both media(file), web, and yes even a little minecraft. 

My plan is to raid10 4 2tb HDDs and keep ubuntu on the 128gb ssd.
How would I install and configure the raid array to be untouched by anything but the samba share?
I'm not sure if this is in the right area, my fault if it isn't. 

Thanks in advance! 

JJ

---

### Post by linuxtechguy on 2013-05-17
You would choose a specific mountpoint for it when setting up or adding the drive later.

---

### Post by JtrickZ on 2013-05-19
Thank You!

So I would use the alternate install disk, and setup the raid device, what would I mount it to?

How would I keep the Ubuntu install on only the SSD? 
Would Samba be able to access the Raid array?

Thanks again LinuxTechguy!

---

### Post by jamesisin on 2013-05-19
When you install Ubuntu you will get partitioning options.  Simply select to install Ubuntu on the SSD and Ubuntu will do the rest.  If you are concerned about being confused when doing the installation of Ubuntu, you can detach the other drives until you have finished your installation (and thereby avoid the risk of installing Ubuntu on the wrong drive).

Once you have Ubuntu installed, you can auto-attach to the RAID using *mount* via *fstab*.

Samba is for sharing across your network.  Once you have the RAID mounted you could then create any appropriate network shares (using Samba or NFS or whatever you'd like).

---

