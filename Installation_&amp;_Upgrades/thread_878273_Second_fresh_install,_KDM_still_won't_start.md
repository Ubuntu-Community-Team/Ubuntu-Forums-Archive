---
title: "Second fresh install, KDM still won't start"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2008-08-02
I had [this problem](http://ubuntuforums.org/showthread.php?t=632663) after upgrading my laptop to Hardy but nobody was able to help me. I eventually got round to reformatting the machine and installing Gutsy from CD. I then immediately used adept to upgrade to Hardy. During the upgrade, there were three error messages related to configuring -linux-generic-something and once the install finished ad rebooted I was right back to square one - KDM will not start up, I get a black screen and have to Ctrl-F1, log in, delete a .tmp file and startx manually.

It's driving me nuts, to be honest, and I can't understand how a clean install can be so bad. It's also amazing that nobody has ever had this problem or can offer any hints on it...

So, just in case someone has an idea...

---

### Post by pickarooney on 2008-08-02
There's some problem with linux-ubuntu-module-(uname-r)-generic but I can't understand the error beyond a missing file called /boot/System.map...

---

### Post by redraiderbum on 2008-08-02
So on a fresh install KDM is not working?  When you installed did you choose to have kubuntu erase all partitions on the disk and use entire disk for installation?

---

### Post by pickarooney on 2008-08-03
I left /home intact and formatted the rest.

---

### Post by pickarooney on 2008-08-04
Today I edited xorg.conf and replaced nvidia with nv. As a result, Kubuntu booted up correctly, but with a limited graphics driver. Also, every time I try to install anything apt-get tries to remove linux-ubuntu-modules-2.6.22-15-generic first and when it fails the package I'm trying to install is ignored. How do I get rid of this messed up package and replace it by a working one and most of all how do I install anything else as long as this keeps giving errors?

---

### Post by pickarooney on 2008-08-05
Fixed it by editing some file (can't find the link that helped me with this) which in turn allowed me to remove the borked modules package, install envy and get proper grpahics drivers configured.

Finally, victory!

---

