---
title: "Kernel Updating"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by friartuc on 2010-02-03
I have kernel 2.6.31-18-generic installed with Ubuntu 9.10. On the kernel website the latest kernel version is 2.6.32.7.

If one was to install this kernel would there be any conflicts? I'm trying to do away with all the work arounds and get my vodafone 3g usb dongle to work with network manager.

Thanks

---

### Post by tommcd on 2010-02-03
Have you read the changelogs for the newest kernel? Do the changelogs say that your vodafone will work in the newest kernel? That should be your first step in evaluating the advantages of upgrading to the latest kernel.

You can simplify the kernel upgrade process by installing the .deb Ubuntu kernel packages for your system (i386 or AMD64) from the Ubuntu ppa kernels site:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
The 2.6.32.7 kernel is at the bottom:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.7/)
You can also use Kernel-Check in Ubuntu to automatically upgrade the kernel:
[http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html](http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html)
There can be no guarantees that the new kernel would not introduce new problems. You should still be able to boot your older kernel(s) if problems arise though.
Be sure to run:
```
sudo update-grub
``` 
after installing a new kernel so you can boot it.

And welcome to the Ubuntu forums!

---

### Post by friartuc on 2010-02-03
Thanks a million .. will check it out!

---

### Post by snowpine on 2010-02-03
2.6.31.x is (and always will be) the officially-supported kernel for Ubuntu 9.10. You are free to install a different kernel, at your own risk, if you feel it will be advantageous. Tommcd's links are spot on.

---

### Post by rajun198 on 2011-10-15
What is the benefit of updating a kerenel?

---

### Post by sirkeith on 2011-10-15
Updated drivers is one big advantage. When I bought a new laptop several issues on installing Ubuntu. Went the ppa route and after 2 kernel updates the issues were gone.

erited to add: No guarantees though, sometimes a new mainline kernel will introduce a new problem.

---

### Post by tommcd on 2011-10-16
> **rajun198 said:**
> What is the benefit of updating a kerenel?
The brand new Ubuntu 11.10 uses the new 3.0 kernel: [https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#Linux_3.0_Kernel](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#Linux_3.0_Kernel)
So if you need or want the newest kernel I would just do a clean install of Ubuntu 11.10. That would be the simplest and most trouble free method to get the newest kernel, drivers, and apps for Ubuntu.

---

