---
title: "How to update Kernal"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by cbennett926 on 2011-08-08
Does anyone know how to update the kernal to 3.0? I am new-ish and have no idea

---

### Post by garvinrick4 on 2011-08-08
Go here and pick out the kernel you want. Choose it and then download the .deb packages
all.deb and headers and image. All three in your 32 or 64 bit architecture. Now click on
them and they will install through Ubuntu software Center in that order I gave you. You will also first have to install
module-init-tools 3.13-1, I will find link for you so is in .deb package and easy to install.
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Below is link for module-init-tools 3.13-1 just click on 32 or 64 bit and in the next page lower
left hand corner will be .deb package that is what you want to download. Click on and will install thru Ubuntu Software center. Install before image of kernel chosen.
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)

##You always want packages already in .deb because easy to install if you get it in source in a tarball (.targz) you have to compile yourself.
##There is also a package named "gdebi" that is a graphical installer of .deb packages.
## maverick and natty will use 3.0 not lucid.

---

### Post by tlu on 2011-08-09
Does anybody know why the [Ubuntu kernel ppa]("https://launchpad.net/~kernel-ppa/+archive/ppa") is no longer maintained? Up to some months ago it was. And it was a much more comfortable way to have updated kernels installed compared to downloading and installing mainline kernels which lack some Ubuntu specific drivers/settings.

---

### Post by cbennett926 on 2011-08-09
What is the safest Kernel?

---

