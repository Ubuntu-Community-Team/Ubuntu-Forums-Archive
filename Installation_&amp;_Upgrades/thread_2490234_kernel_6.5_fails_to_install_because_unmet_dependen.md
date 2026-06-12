---
title: "kernel 6.5 fails to install because unmet dependencies libc6 &gt; 2.38"
date: 2023-08-27
forum: Installation &amp; Upgrades
---

### Post by Keith Myers on 2023-08-27
Tried to install the new stable release 6.5.0-generic kernel from the Mainline PPA and got met with the post title error message.

Have installed all of the previous 6.5-rc kernels prior to this with no problems.

Running Ubuntu 22.04.3 distro on a Zen 4 7950X host which uses libc6 2.35.

Currently on the 6.5-rc7 kernel.

What changed?

---

### Post by Doug S on 2023-08-28
The mainline kernel is compiled from the development version of Ubuntu, or 23.10. In the last week it would have gone to a newer version of libc6 (newer compiler, actually), causing issues with older versions of Ubuntu trying to install that kernel. I am still using 20.04, and have these issues for years:

```
Setting up linux-headers-6.5.0-060500 (6.5.0-060500.202308271831) ...
dpkg: dependency problems prevent configuration of linux-headers-6.5.0-060500-generic:
 linux-headers-6.5.0-060500-generic depends on libc6 (>= 2.38); however:
  Version of libc6:amd64 on system is 2.31-0ubuntu9.9.
 linux-headers-6.5.0-060500-generic depends on libssl3 (>= 3.0.0); however:
  Package libssl3 is not installed.
``` 

I have to compile the kernel myself to be able to install it.
See also [the old related bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1926938"), from last time this happened.

---

### Post by j0nny55555 on 2023-08-31
Can confirm #mainline and even 6.4.x now seems to exhibit the same issue:

```
Setting up linux-modules-6.4.13-060413-generic (6.4.13-060413.202308301431) ...
Setting up linux-headers-6.4.13-060413 (6.4.13-060413.202308301431) ...
dpkg: dependency problems prevent configuration of linux-headers-6.4.13-060413-generic:
 linux-headers-6.4.13-060413-generic depends on libc6 (>= 2.38); however:
  Version of libc6:amd64 on system is 2.35-0ubuntu3.1.

dpkg: error processing package linux-headers-6.4.13-060413-generic (--install):
 dependency problems - leaving unconfigured
```

---

### Post by winstonma2 on 2023-09-14
I tried [Jammy LTS Mainline Kernels]("https://launchpad.net/~tuxinvader/+archive/ubuntu/jammy-mainline") and it works for me. Alternatively you can go to the [Jammy LTS Mainline repo]("https://github.com/TuxInvader/focal-mainline-builder/tree/main"), follow their README and build the kernel with less than 5 commands.

For Jammy LTS, you can use the follow command,
```

# Add Jammy LTS repo
sudo add-apt-repository ppa:tuxinvader/jammy-mainline
# Install Kernel 6.5.2
sudo apt install linux-modules-6.5.2-060502-generic linux-headers-6.5.2-060502-generic linux-image-unsigned-6.5.2-060502-generic
```
The second command may not work for you because the repo only keep the latest 2 release, due to the size limit. Please check the repo for the latest release and change your package name accordingly.

---

### Post by ActionParsnip on 2023-09-15
What is in the new kernel that you need so badly or are you wanting to report bugs?

---

### Post by eddy20042 on 2023-09-26
Same here.

In theory there is a meta-package in mainline-jammy:

[FONT=courier new]sudo apt install linux-generic-6.05[/FONT]

but it does not work for me currently (point to 6.5.5 which is absent ATM). This seems to work though:

[FONT=courier new]sudo apt install linux-headers-6.5-060500-generic linux-image-unsigned-6.5-060500-generic linux-modules-6.5-060500-generic
[/FONT][FONT=monospace]
[/FONT]

---

### Post by tips2448 on 2023-10-06
This makes complete sense thanks a lot.

---

### Post by TenPlus1 on 2023-10-08
I use the Mainline app to install the latest 6.5.5 kernel and while it errors, I can easily remove the offending -headers file in Synaptic and it will run fine.

---

### Post by Doug S on 2023-10-09
> **TenPlus1 said:**
> I use the Mainline app to install the latest 6.5.5 kernel and while it errors, I can easily remove the offending -headers file in Synaptic and it will run fine.I have noticed that also, but have never understood why. Does anyone know why it works with the header file uninstalled?

---

