---
title: "how to install kernel 3.4/3.5 and fglrx drivers 13.1 on ubuntu 12.04.02"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by Jaoyur on 2013-04-08
I have tried to upgrade from kernel 3.2.0-39 to kernel 3.4 ([here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/")) and after that  installing fglrx drivers 13.1 (compatible up to kernel 3.5). 
Here are  the steps I followed:
  
[LIST=1]
[*]Removing (purging) existing drivers
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*   
``` 
[/LIST]
rebooted

[LIST=1]
[*]updated open drivers.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
``` 
[/LIST]
```
sudo apt-get update && sudo apt-get upgrade   
```

rebooted

[LIST=1]
[*]installed some dependencies and then tried to install fglrx drivers:
```
sudo sh amd-driver-installer-*.run --buildpkg Ubuntu/precise  sudo dpkg -i *.deb 
``` 
[/LIST]
  At this point the installation stuck at: 
```
update-initramfs: Generating /boot/initrd.img-3.4.0-0304-generic
``` 
  nothing happens and I have to stop installation and I need to use dpkg-reconfigure -a.
  Can you tell me how install kernel and fglrx drivers in the correct way? Do I need to know anything else to do that?
  Thanks

---

### Post by Jaoyur on 2013-04-09
I found this: [http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23](http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23)
Is it maybe a solution for my problem in order to upgrade to newer kernel (3.5)? 
I mean: maybe those are the steps I have to follow to upgrade without any block during installation, what do you think?
Do I need to remove fglrx before following those steps to upgrade to 3.5 or not?

---

