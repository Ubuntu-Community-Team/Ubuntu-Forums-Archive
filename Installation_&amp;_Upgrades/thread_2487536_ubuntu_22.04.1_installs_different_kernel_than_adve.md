---
title: "ubuntu 22.04.1 installs different kernel than advertised"
date: 2023-06-07
forum: Installation &amp; Upgrades
---

### Post by rughooam on 2023-06-07
Hi,
 I tried installing ubuntu 22.04.1 under vmware 17 workstation

I got the iso ubuntu-22.04.1-desktop-amd64.iso from [https://old-releases.ubuntu.com/releases/jammy/](https://old-releases.ubuntu.com/releases/jammy/)
to make sure linux kernel 5.15 is installed based on the info on this page
[https://ubuntu.com/kernel/lifecycle](https://ubuntu.com/kernel/lifecycle)

but after installation I see kernel 5.19 is installed as shown below
```
amish@6LXWHW3NOV:~$ uname -r
5.19.0-43-generic
amish@6LXWHW3NOV:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy
amish@6LXWHW3NOV:~$


```

 I unchecked the box that said update while installing as well.

I am wondering why is there a kernel mismatch and what I need to do to get the kernel 5.15
Thanks
Amish

---

### Post by QIII on 2023-06-07
Hello.

Given that 5.19 is a more recent version (because you have installed the point release) than 5.15, one has to wonder why you think you want to downgrade to an older kernel version.

---

### Post by Impavidus on 2023-06-08
Some people want the older kernel for stability.

You got the latest kernel of the HWE series for Ubuntu 22.04, so you either installed upgrades during installation or installed them later. The system does that automatically, unless you disable it. If you want the 5.15 kernels, install linux-generic and remove linux-generic-hwe-22.04, then autoremove dependencies of the latter.

---

### Post by rughooam on 2023-06-08
I have tools that are unstable with 5.19 kernel

---

### Post by rughooam on 2023-06-08
I was sure I unchecked update during install which is what puzzles me...

---

### Post by rughooam on 2023-06-14
I tried again this time with 22.04 and the same thing. I definitely unchecked any updates whatsoever during installation
rughooam@6LXWHW3VMAUR:~$ uname -r
5.19.0-43-generic
rughooam@6LXWHW3VMAUR:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy


This is very bizarre. I guess it's time to go figure out how to downgrade the kernel properly

---

### Post by ajgreeny on 2023-06-14
To get the 5.15 series of kernels you either need to install ***linux-generic*** and then remove **linux-generic-hwe-22.04** as already mentioned by impavidus in post #3, or if you really want to start again, and there's no real need to do that, you could reinstall but ensure that you use the original iso file from [https://old-releases.ubuntu.com/releases/22.04/ubuntu-22.04-desktop-amd64.iso](https://old-releases.ubuntu.com/releases/22.04/ubuntu-22.04-desktop-amd64.iso)

This will make sure that you do not end up with the 5.19 kernel series but will use the 5.15 series even after updating the OS.

---

