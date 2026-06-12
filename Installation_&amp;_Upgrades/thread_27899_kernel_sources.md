---
title: "kernel sources"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by gerald.schnabel on 2005-04-18
Hello,

I want to compile the madwifi wireless driver. For that I have to configure the Kernel Source Path. Does anybody know where the kernel source Path is, or how I can find or download the Kernel Source for Ubuntu?

Thanks for your help.

---

### Post by TravisNewman on 2005-04-18
apt-get install linux-source-<kernel version>

It's easier to use Synaptic and search for "linux-source" and search for your kernel version there and install it.

---

### Post by heimo on 2005-04-18
And if I remember correctly, that will drop a compressed file to */usr/src/*. So *cd /usr/src* and *tar xjvf linux-source.tar.bz* (or what ever the name is) and make a symbolic link from the folder (that was just created) to /usr/src/linux (*ln -s [foldername] linux*). That's the common way to do it.
 
If you haven't installed yet, install also package *build-essential*

---

### Post by az on 2005-04-18
You should use the linux-headers to compile a module.  Package = linux-headers-(version)

You should use the linux-tree if that is not enough and you need to full source preconfigured.  Package= linux-tree-(version)

But the madwifi driver is already made for you in the linux-restricted-modules package...  The module should be loaded by hotplug....

---

### Post by gerald.schnabel on 2005-04-18
thanks, the installation all works fine, but my wireless lan is still not running.
I have a d-link dwl-g520. Now I want to try the ndiswrapper.

thanks for your help

---

