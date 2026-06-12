---
title: "CPIO Error while installation/upgrading"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by rmauersb on 2008-04-03
Hello,

I am Linux newbie and using an Ubuntu Dapper 6.06 on an intel-based
laptop. for installation and upgrading of packages I am using the Synaptics Package Manager (SPM). so far i did not have any problems with it, neither with installation nor upgradings. 

recently (for whatever reason) i get a strange error during installation/upgrading processes in SPM and I have no idea how to solve this issue. Due to this error, packages are not installed properly, although SPM indicates that the component is installed (marked in green).

It looks as follows:

---
E: cpio: subprocess post-installation script returned error exit status 2
E: initramfs-tools: dependency problems - leaving unconfigured
E: udev: dependency problems - leaving unconfigured
E: hal: dependency problems - leaving unconfigured
E: linux-image-2.6.15-28-386: dependency problems - leaving unconfigured
E: xfce4-session: dependency problems - leaving unconfigured
---  

I tried with a re-installation of the cpio-package which brought no improvement, a complete removal and new installation nearly messed up my entire system and now also throws out a couple of "dependency errors" (see above).

My question is how I can solve this cpio issue and if there is a way to "repair" these dependency problems.

Detailed help would be much appreciated!

Thanks in advance!

---

