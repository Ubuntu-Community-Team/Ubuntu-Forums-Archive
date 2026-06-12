---
title: "Nvidia-glx deb seems to be corrupt"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by LaneLester on 2006-12-06
It's probably something wrong on my system... or in my head. I just installed an nvidia card in place of my ati. I switched to the gross vesa driver to be sure I would still have video. But there seems to be something wrong with the deb.

I tried three ways to install it, and I deleted the archived .deb each time to be sure I was getting a fresh copy.

Automatix2 says this: An apt-based error occured and installation was unsuccessful

Synaptic said this: E: /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb: subprocess pre-installation script returned error exit status 2

And when I tried to install it with dpkg, I got this:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted nvidia-glx 1.0.8776+2.6.17.6-1 [4066kB]
Fetched 4066kB in 12s (322kB/s)
(Reading database ... 100391 files and directories currently installed.)
Removing fglrx-control ...
Removing fglrx-kernel-2.6.17-10-generic ...
Removing xorg-driver-fglrx ...
Stopping atieventsd: done.
rmdir: /usr/lib/fglrx: Directory not empty
Selecting previously deselected package nvidia-glx.
(Reading database ... 100283 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by PILGU on 2006-12-06
Have you tried

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

After that download and installation is completed, run

sudo dpkg-reconfigure xserver-xorg

during the configuration of the wizard make sure to select "Nvidia" in place of "nv".
When you are asked about your monitor and presented with a Simple, Medium, Advanced selection, choose medium if you know your monitors max resolution and refresh. If you don't know this information choose simple. Either way, select the appropriate setting for your monitor and continue.
if at bootup the invidia logo appears, than driver is running ok!

---

### Post by LaneLester on 2006-12-06
Thanks for the reply. Yes, I had tried that command. Here is what it gives me:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted nvidia-glx 1.0.8776+2.6.17.6-1 [4066kB]
Fetched 4066kB in 12s (322kB/s)
(Reading database ... 100391 files and directories currently installed.)
Removing fglrx-control ...
Removing fglrx-kernel-2.6.17-10-generic ...
Removing xorg-driver-fglrx ...
Stopping atieventsd: done.
rmdir: /usr/lib/fglrx: Directory not empty
Selecting previously deselected package nvidia-glx.
(Reading database ... 100283 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Lane

---

### Post by jpmorelli on 2006-12-06
You can look for some information in this web:

[http://albertomilone.com/wordpress/]("http://albertomilone.com/wordpress/")

This blog is from Alberto Milone, he is one developer of graphics hardware for Ubuntu.
I have a nvidia card in my system and envy package works perfect for me !

---

### Post by kerry_s on 2006-12-06
Use synaptic(status>installed) & remove all the fglrx stuff you have installed first, then try & install nvidia. It looks like it's having trouble reconfiguring them.

---

### Post by LaneLester on 2006-12-07
Thanks for all the suggestions! Alberto Milone's envy installer did the trick for me.

Lane

---

