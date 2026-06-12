---
title: "install ubuntu from ubuntu terminal?"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by shishtpal on 2013-11-18
hii,:)
there is any way to install ubuntu from ubuntu terminal, in ubuntu live mode.
suppose, i do not want to use default ubuntu installer.:(
can I install ubuntu by just extracting the content of filesystem.squashfs.
for ex-
#unsquashfs -f -d /mnt/sda5 ./filesystem.squashfs
and than add a grub4dos menu entry for booting..
#
title  ubuntu
root (hd0,4)
kernel /boot/vmlinuz root=UUID=bla.bla.bla... ro splash
initrd /boot/initrd.lz
boot


#but when i try this method, ubuntu-13.04 works well but, here i log-on system with a temporary user profile.
thanks...

---

### Post by ibjsb4 on 2013-11-18
I do not understand what your up to, but ..

A command line install can be done with the mini iso.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=command+line+install+mini+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=command+line+install+mini+iso&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2013-11-18
There is this?
 HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by shishtpal on 2013-11-18
thanks for reply, but 
here i want to say that, i want to install ubuntu without touching the ubuntu installer.
i just extract the live filesystem to any partition,, and than i just create a grub4dos config file to boot ubuntu from that partition, but the problem is that, when i boot ubuntu creates a temp. profile for me, instead of a live user as if i boot from live usb.
may be this is because of configuration errors , so if i create a user and password and define the swap partition just after extracting the live filesystem, may be problem will be solved,
extracting ubuntu live filesystem takes only 1 minute, whereas installing ubuntu from its default installer takes 15 minutes.
i thinks manual way is best and i can learn from it.
thanks..

---

### Post by sudodus on 2013-11-19
If you want to learn linux from scratch try this link

 [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Or something much easier, but still more manual than with the desktop installer: Install from the Ubuntu ***mini.iso***. See for example this link

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

