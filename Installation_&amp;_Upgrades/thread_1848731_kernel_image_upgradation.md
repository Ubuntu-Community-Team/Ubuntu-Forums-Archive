---
title: "kernel image upgradation"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by zainlodhi on 2011-09-23
I upgraded my kernel image to 2.6.38-11 and removed the older kernel images after upgradation. The previous versions of kernel images are successfully removed but when i press the tab button after writing the command 'sudo apt-get remove linux-image-' it shows me the names of the previous kernel images. And when i try to remove the previous versions again it gives me the message that the previous versions are already removed. These are just the names which are appearing again and again. Guys help me out?

---

### Post by zvacet on 2011-09-23
Try with removing old linux-headers too.

---

### Post by Frogs Hair on 2011-09-23
I find the package cleaner on Ubuntu Tweak very nice for removing old kernels . It has some other nice features as well .[http://blog.ubuntu-tweak.com/2011/01/13/ubuntu-tweak-0-5-11-bug-fixed-release-for-ubuntu-11-04-natty.html](http://blog.ubuntu-tweak.com/2011/01/13/ubuntu-tweak-0-5-11-bug-fixed-release-for-ubuntu-11-04-natty.html)

---

### Post by garvinrick4 on 2011-09-23
Maybe update-grub so new config file without removed kernels.
```
sudo update-grub
```You can run and watch it being made and see what is there
```
sudo grub-mkconfig
```Below shows you kernels  in as a menu entry
```
grep menuentry /boot/grub/grub.cfg
```## Ubuntu-tweak is cool for a lot of things as in previous post.
Here is ppa for tweak, previous post gave you .deb build.
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)

---

