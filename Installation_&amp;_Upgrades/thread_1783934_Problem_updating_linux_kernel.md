---
title: "Problem updating linux kernel"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by Fabled One on 2011-06-16
When I installed the kernel image I got 
```
Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169
```I can boot/log in fine, but when I try to install video drivers (ATI Catalyst11.6 from AMD site) I get that same error.

When I try sudo apt-get update, I get:
```
W: Failed to fetch http://ppa.launchpad.net/chasedouglas/linux-firmware/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/chasedouglas/linux-firmware/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```I have Ubuntu 11.04. I started with driver:  2.6.38-8-generic. 

Here are the steps I followed to install the kernel v2.6.39-rc4:

[LIST=1]
[*]Downloaded files from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-rc4-natty/")
[*]using sudo dpkg -i, installed the following in order:
[LIST]
[*]*linux-headers...all.deb*
[*]*linux-headers..generic..64.deb*
[*]*linux-image....64.deb*
[/LIST]
 
[*]Restart
[/LIST]
I originally got the firmware error after installing *linux-image....64.deb*.

I already tried fixing it according to [this]("http://askubuntu.com/questions/25732/possible-missing-firmware-lib-firmware-rtl-nic-rtl8168d-2-fw-for-module-r8169-wi"):

[LIST]
[*]I added the **ppa:chasedouglas/linux-firmware**
[/LIST]
But that now just gives me the```
 W: Failed to fetch http://ppa.launchpad.net/chasedouglas/linux-firmware/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found


```When I apt-get update.

Anyone know what I broke?

---

### Post by echo6 on 2011-07-02
It would appear that the latest kernel doesn't provide the realtek firmware.

Debian have recognised it is a bug, [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561309](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561309)

You could manually extract the needed files from the deb package found here
[http://pkgs.org/debian-sid/debian-nonfree-i386/firmware-realtek_0.28_all.deb.html](http://pkgs.org/debian-sid/debian-nonfree-i386/firmware-realtek_0.28_all.deb.html)

n.b. You will get a conflict error if you try to install this package as it tries to replace a file which is already installed in the linux-firmware package.

My guess is that linux-firmware needs updating to include these missing files.

---

### Post by dino99 on 2011-07-02
you should try with the latest 3.0.3 kernel

---

