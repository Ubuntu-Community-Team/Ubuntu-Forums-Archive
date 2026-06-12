---
title: "hwe kernel on 18.04: how did it get here and can I remove?"
date: 2019-04-11
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2019-04-11
I am running a clean install of Xubuntu 18.04 (from xubuntu-18.04-desktop-amd64.iso) 
on 2 laptops (one with nvidia graphics, one with intel graphics) and on 3 VMs.

apt list --installed linux-image* on my laptops gives me:
> linux-image-4.15.0-46-generic/bionic-updates,bionic-security,now 4.15.0-46.49 amd64 [installed,auto-removable]
linux-image-4.15.0-47-generic/bionic-updates,bionic-security,now 4.15.0-47.50 amd64 [installed,automatic]
linux-image-4.18.0-16-generic/now 4.18.0-16.17pop0~18.04.1 amd64 [installed,local]
linux-image-4.18.0-17-generic/bionic-updates,bionic-security,now 4.18.0-17.18~18.04.1 amd64 [installed,automatic]
linux-image-generic/bionic-updates,bionic-security,now 4.15.0.47.49 amd64 [installed,automatic]
linux-image-generic-hwe-18.04/bionic-updates,bionic-security,now 4.18.0.17.67 amd64 [installed,automatic]
(I keep one old vsn of every kernel just in case)

1. 	I did not ask for or install the hwe kernel, why is it installed?
	It is installed on both my laptops but not my VMs?!

2.	Install instructions for the hwe kernel say:
> sudo apt install --install-recommends linux-generic-hwe-18.04 xserver-xorg-hwe-18.04
	but while linux-generic-hwe-18.04 is installed xserver-xorg-hwe-18.04 is not.  	
	How is this possible?

	uname -a shows  on both laptops:
> 4.18.0-17-generic #18~18.04.1-Ubuntu SMP
	so I am running the hwe kernel, so why does it work without the corresponding xserver-xorg-hwe-18.04 ?
	
3. 	(How) can I safely uninstall the hwe kernels and just use the standard ones?
I can select the standard kernels from grub and boot to them ok.

---

### Post by ajgreeny on 2019-04-11
When did you install the system, and did you use the 18.04.2 point release, or the original 18.04 or 18.04.1 version?

The two latter versions I mention above used the original 4.15 kernel series and only with the 18.04.2 point version did you get the 4.18 kernel series which would update itself automatically, along with other system upgrades; that may be why you are seeing the hwe kernels in your system.

Before you start uninstalling any of those 4.18 kernels please show us the output of ```
dpkg -l linux-generic
``` which will allow us to see which kernels, if any, can be safely removed.

---

### Post by undecidable on 2019-04-11
Thanks for the fast response.

I installed the original 18.04, from the xubuntu-18.04-desktop-amd64.iso medium
though over time it has upgraded to 18.04.2.  
From lsb_release -a
> No LSB modules are available
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:        18.04
Codename:       bionic

The output of dpkg -l linux-generic
> ii  linux-generic        4.15.0.47.49    amd64           Complete Generic Linux kernel and headers

---

### Post by ajgreeny on 2019-04-11
The output you show from **dpkg -l linux-generic** is exactly what I get on my Xubuntu 18.04 also installed from the original .iso image but I do not have any 4.18 kernels installed in my system.

There does not appear to be any reason for the update system to have installed the 4.18 kernel series so I wonder if you have added it yourself to overcome a problem that you had at some point in the past.

However, once again, before removing any kernels let's see the output of ```
dpkg -l linux-image*
``` just to see the full list of those installed at present.

---

### Post by undecidable on 2019-04-11
No, I did not have any problem 
that caused me to manually install the hwe kernel.  
Most of my problems get solved by coffee, not kernels. 

The output of   dpkg -l linux-image*
> un  linux-image          <none>          <none>          (no description available)
rc  linux-image-4.15.0-4 4.15.0-45.48    amd64           Signed kernel image generic
ii  linux-image-4.15.0-4 4.15.0-46.49    amd64           Signed kernel image generic
ii  linux-image-4.15.0-4 4.15.0-47.50    amd64           Signed kernel image generic
ii  linux-image-4.18.0-1 4.18.0-16.17pop amd64           Signed kernel image generic
ii  linux-image-4.18.0-1 4.18.0-17.18~18 amd64           Signed kernel image generic
ii  linux-image-generic  4.15.0.47.49    amd64           Generic Linux kernel image
ii  linux-image-generic- 4.18.0.17.67    amd64           Generic Linux kernel image
un  linux-image-unsigned <none>          <none>          (no description available)
un  linux-image-unsigned <none>          <none>          (no description available)
un  linux-image-unsigned <none>          <none>          (no description available)
un  linux-image-unsigned <none>          <none>          (no description available)
un  linux-image-unsigned <none>          <none>          (no description available)

This is similar to the output of 
apt list --installed linux-image*
shown in the original post.

However one thing suddenly does stand out, the "pop" in the line:
> ii  linux-image-4.18.0-1 4.18.0-16.17pop amd64           Signed kernel image generic

I mentioned the hwe kernels are only on the laptops (both system76) and not the VMs. 
This is a clean install from Ubuntu medium 
but i did install of course the system76-driver.  
Now PopOS is the system76 OS, so I wonder if it is possible that the system76-driver updating 
caused the install of the hwe kernels
but not the linux-generic-hwe-18.04 xserver-xorg-hwe-18.04  ?

---

### Post by undecidable on 2019-04-11
In fact that may be the answer. 
Just checked the dependencies
Output of
```
 aptitude show system76-driver
```

> Package: system76-driver          
Version: 19.04.7~1553705208~18.04~446bbf4~dev
State: installed
Automatically installed: no
Priority: extra
Section: utils
Maintainer: System76, Inc. <dev@system76.com>
Architecture: all
Uncompressed Size: 457 k
Depends: python3:any (>= 3.4~), dconf-gsettings-backend | gsettings-backend, at, gir1.2-gtk-3.0,
         gir1.2-notify-0.7, gnome-shell-extension-system76-power, linux-generic (>= 4.18) |
         linux-generic-hwe-18.04, pm-utils, python3-dbus, python3-evdev, python3-gi, python3-systemd,
         system76-dkms, system76-firmware-daemon, system76-io-dkms, system76-power, system76-wallpapers,
         xbacklight

So, it seems an update to the system76 driver caused the install of the hwe kernel.  
Doesn't explain how i missed it.  
maybe just age and infirmity :P

---

### Post by ajgreeny on 2019-04-11
Good news that at least we now know how and why it happened!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 
It is a great help to other users searching the forum.

---

### Post by undecidable on 2019-04-12
yes, about to, just wanted to see if you had any comment first.
Thanks for your help.  
Answering your questions got us to the answer.

---

