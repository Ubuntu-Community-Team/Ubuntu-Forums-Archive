---
title: "ubuntu 9.10 pxe install"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by aclhkaclhk on 2010-02-18
i followed the following procedure to setup a pxe install server:
[http://www.howtoforge.com/setting-up...on-ubuntu-9.10]("http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10")

the pxe client (with over 1g ram) displays text installation mode, not graphical installation mode for "install", "expert install" options.

pxelinux.cfg/default
label install
   menu label ^Install
   menu default
   kernel ubuntu-installer/i386/linux
   append initrd=ubuntu-installer/i386/initrd.gz -- quiet

label expert
   menu label ^Expert install
   kernel ubuntu-installer/i386/linux
   append priority=low vga=normal initrd=ubuntu-installer/i386/initrd.gz --


pls advise.         
                                                                                                                               [IMG]http://images.howtoforge.com/forums/images/misc/progress.gif[/IMG]                 [[IMG]http://images.howtoforge.com/forums/images/buttons/edit.gif[/IMG]]("http://www.howtoforge.com/forums/editpost.php?do=editpost&p=219653")

---

