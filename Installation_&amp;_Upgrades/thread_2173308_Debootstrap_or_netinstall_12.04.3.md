---
title: "Debootstrap or netinstall 12.04.3"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by bulldozer2003 on 2013-09-09
I would like to debootstrap (or netinstall)  12.04.3 with the new kernel and other improvements. The ISOs are updated  or course, but those cannot be used (see [bug 77589]("https://answers.launchpad.net/bugs/77589"), link below). The archives that debootstrap or netinstall use are still 12.04.0.


 I *could* use the CD if there is a way for me to:
1. skip the partioning step and manually mount the target
2. proceed with the install onto the target
3. skip grub
4. manually enter the chroot and make the necessary changes to make the install bootable


 If you'd like details about why I need to do it this way I can  provide them, but its inconsequential to the ability to do custom  installs with the newer 12.04.3 release sources.
 "debootstrap can't chroot" from CD bug:
[https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589](https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589)


 See the timestamps at [http://us.archive.ubuntu.com/ubuntu/dists/precise/](http://us.archive.ubuntu.com/ubuntu/dists/precise/)  that are still from April 2012. I also did a standard netinstall and  wound up with kernel 3.2, instead of 3.8 included in 12.04.3, even  though /etc/lsb-release claimed it was Ubuntu 12.04.3!


 I suppose I could also do some manual work to upgrade a 12.04.0 install to 12.04.3, but I'm not sure what those step are.


 Thank you.

---

### Post by bulldozer2003 on 2013-09-10
I asked the same question at launchpad ([https://answers.launchpad.net/ubuntu/+source/debootstrap/+question/235376](https://answers.launchpad.net/ubuntu/+source/debootstrap/+question/235376)) and was told:

> [TABLE]
[TR]
[TD][Manfred Hampl (m-hampl)]("https://launchpad.net/%7Em-hampl")          said     on 2013-09-09:[/TD]
[TD="class: bug-comment-index"]        #1[/TD]
[/TR]
[/TABLE]
       For the differences in kernel version for 12.04.0 and 12.04.3 see [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
 The command
sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring
should upgrade your system to the latest versions (even if installed from the 12.04.0 media)





Looking a bit at the 12.04.3 installer CD you can see the installer is doing the same thing with this line in the preseed files:
> d-i    base-installer/kernel/altmeta    string lts-raring

---

