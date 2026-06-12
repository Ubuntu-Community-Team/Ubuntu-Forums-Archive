---
title: "Re-install over prior distro"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by Jay+ on 2011-10-01
I had a triple boot config that i did a few years ago.  It worked well.

I killed the debian partition and used it for data.  I still have the menu for debian or windows loader in grub 0.97.  

I'd like to install Ubuntu on that drive.  I don't remember if I had to install linux first before xp & vista.  

If i run an Ubuntu install 10.10 or 11.04 will it add the option to grub, install on my target partition and leave the rest as is?

---

### Post by ajgreeny on 2011-10-01
If you choose "Something else" at the disk preparation stage of the new installation, you will be able to see all the current partitions and delete any that you want to and install your new system in those spaces.  It is worth looking at [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") as it will make life much easier in future.  This site is for an earlier version of Ubuntu, but the basic information is still the same;  just a few of the steps, eg the "Something else" already mentioned, are now named differently.

It is easiest if you have XP/Vista installed first and then add whatever linux you are using, as grub will find windows but windows will overwrite grub and not find linux systems.

---

