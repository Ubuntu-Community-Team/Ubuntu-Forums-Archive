---
title: "Compiling issues with bluetooth driver"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by Blackbug on 2015-11-15
Hello,

I am using Ubuntu16.04 edition. I am trying to install bluetooth driver from my RT-3920 bluetooth. I am following this thread [http://askubuntu.com/questions/324115/ralink-bluetooth-not-working-in-ubuntu-13-04](http://askubuntu.com/questions/324115/ralink-bluetooth-not-working-in-ubuntu-13-04). However, I am missing linux headers or firmware code. While I am running 'make' command on the downloaded code ( as guided by the link ), I am receiving following error:

```
~/Downloads/Drivers/rtbth-3.9.3$ makemake -C /lib/modules/3.16.0-45-generic/build M=/home/kk/Downloads/Drivers/rtbth-3.9.3 modules
make[1]: *** /lib/modules/3.16.0-45-generic/build: No such file or directory.  Stop.
Makefile:24: recipe for target 'all' failed
make: *** [all] Error 2

```

I do understand that the header files for the kernel version 3.16.0.45 which this bluetooth driver code is trying to look are missing. But, I dont know how to get them. My kernel info is as below:

```
3.16.0-45-generic #60~14.04.1-Ubuntu
```

When I tried to donwload source for the kernel using apt-get i got following error:

```
~/Downloads/Drivers/rtbth-3.9.3$ sudo apt-get source linux-headers-3.16.0-45
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux-lts-utopic' as source package instead of 'linux-headers-3.16.0-45'
E: Unable to find a source package for linux-lts-utopic

```

Please suggest.

Thanks

---

### Post by Blackbug on 2015-11-15
I manually downloaded a debian file for the said linux header, and now I can compile. Thanks

---

