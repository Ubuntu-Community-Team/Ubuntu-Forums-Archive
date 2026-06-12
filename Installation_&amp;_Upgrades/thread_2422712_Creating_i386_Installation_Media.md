---
title: "Creating i386 Installation Media"
date: 2019-07-11
forum: Installation &amp; Upgrades
---

### Post by 95yj on 2019-07-11
I was wondering if someone could point me to a step by step on how to create installation media from the installer files.  We have a bunch of very old servers with Xeon 32 bit processors that run bind or mail and other Linux utilities and want to upgrade the distro.  Since most Linux distros do not publish i386 ISOs anymore, we will have to build these ourselves.  I found a pile of files and directories at the installer-i386 download sections but do not know which files are needed nor what to do with them to create a bootable ISO or USB.  Have done a lot of searching but cannot find where to go from here, or else I am just looking in the wrong places.

Is there a tutorial available or can someone give step by steps on how to create a bootable installation package?  Thanks in advance

---

### Post by mastablasta on 2019-07-12
how about using Debian or CentOS? : 

[https://www.debian.org/CD/http-ftp/](https://www.debian.org/CD/http-ftp/)
[https://wiki.centos.org/Download](https://wiki.centos.org/Download)

both have i386 version, both have long support period and both are great for servers.

---

### Post by 95yj on 2019-07-12
> **mastablasta said:**
> how about using Debian or CentOS? : 


Hey, that's great.  Thanks for the links.  I will probably go that route.

I would still like to learn how to create the installs.  If anyone has suggestions, I would really appreciate it.

---

### Post by pcfan1234 on 2019-07-15
Why don't you use the Netboot-Installer? You only need internet connection during the installation.
I recommend version 18.04 because 19.04 will be the last version with 32-bit-support.
19.10 won't be available as i386.
[ftp://cdimage.ubuntu.com/cdimage/netboot/18.04.2/index.html](ftp://cdimage.ubuntu.com/cdimage/netboot/18.04.2/index.html)

---

### Post by mastablasta on 2019-07-16
for enterprise server the LTS version is a must. 18.04 free support expires in 2023. but with purchased support this can be extended until 2028.

linux from scratch is a project that teaches you how to set up your own OS. however to me it just takes too long. but if you have time on your hands, go for it. i barely have time to eat and sleep when i get home.

putting together a 32 bit version of ubuntu 20.04 won't be as simple as jamming together a few libraries and other stuff, because they won't be there at all.

if however you are talking about building your own version from minimal iso (as discussed here: [https://askubuntu.com/questions/1127402/is-there-a-32-bit-version-of-ubuntu-18-04-desktop](https://askubuntu.com/questions/1127402/is-there-a-32-bit-version-of-ubuntu-18-04-desktop)) this is a different thing. this means that all components are available in repositories and you just add what you want and need. 

debian calls it netinstall. 

ubuntu minimal: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
an example of modular install and setting up of own OS: [https://www.psychocats.net/ubuntu/minimal](https://www.psychocats.net/ubuntu/minimal)

---

