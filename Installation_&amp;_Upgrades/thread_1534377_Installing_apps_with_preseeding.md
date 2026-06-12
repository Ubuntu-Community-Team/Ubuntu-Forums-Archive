---
title: "Installing apps with preseeding"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by CrayonOfDoom on 2010-07-19
So I've got a nice preseed.cfg file that successfully installs 10.04  without any user interaction (completely headless) via PXElinux.  I have  a few questions though.  I'm working on having different preseed files  that pre-install a few packages based on user selection at the ubuntu  netboot screen and I'd like to know if I'm doing it right.  at the end  of my preseed.cfg, I've added the following (as an example, the list is  larger than one install)

```
d-i preseed/late_command string apt-get -y install  subversion
```Is this the correct format for having the preseed  install subversion automatically before finishing the install?  i.e.  having subversion ready to configure and use the second an end-user  boots into ubuntu the first time.  Will these apt-get's use a local apt mirror if it's configured to use one in the preseed?

Another question is:
Is there a detailed guide on how to create sub-menus in the menu.cfg/text.cfg that loads from the pxelinux.cfg/default file?

Thanks for the help!

---

### Post by CrayonOfDoom on 2010-07-21
Update:  The late_command prevented the preseed from even running, so I tried to modify the following lines:
```
d-i pkgsel/include string openssh-server build-essential
```
was modified to:
```
d-i pkgsel/include string openssh-server build-essential java-6-jdk java-6-bin subversion postgresql libapache2-svn
```
But threw an error during install claiming that an installation step failed.  Still looking at how to include java, subversion and postgresql automatically with my headless install.

---

### Post by Darkness Des on 2010-07-21
The names of the Java packages are wrong. It's sun-java6-whatever.

---

### Post by CrayonOfDoom on 2010-07-22
After doing a bit of research I sort of got it...
```
d-i preseed/late_command string chroot /target apt-get -y install openjdk-6-jdk subversion libapache2-svn postgresql
```

Yielded an "Error Code 100" upon running the late_command, however it *appears* based on my package manager that the installs worked.  Where can I find info on what the error code means?

---

