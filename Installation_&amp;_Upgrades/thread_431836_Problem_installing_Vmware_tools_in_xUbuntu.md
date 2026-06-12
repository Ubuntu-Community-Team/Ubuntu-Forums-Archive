---
title: "Problem installing Vmware tools in xUbuntu"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by albatroz2k on 2007-05-03
I am following these steps for installing VMWare tools
[http://www.devjoker.com/asp/ver_contenidos.aspx?co_contenido=76](http://www.devjoker.com/asp/ver_contenidos.aspx?co_contenido=76)
in a xUbuntu 6.10 installation, but I get this error...
E: Couldn´t find package linux-headers-uname -r

Any suggestions?

---

### Post by bernied on 2007-05-03
You need to install the kernel headers that correspond to your current kernel. You can find out what your currently running kernel is with
```
uname -r
```
Once you know this, you can install the headers for it. Use your package manager to do this, just find the package called linux-headers- followed by whatever your kernel version is (the result of 'uname -r'). There is a flashy way of putting this all in one command, but I don't know it.

While you're using your package manager, you should check whether you have installed the package called build-essential - this will be needed by the vmware installer later to compile your network bridging modules.

Then you can resume your install of vmware.

EDIT: You don't actually have to stop the vmware installer when you get problems like this, if I remember correctly, just open a new terminal, fix the problem, then resume the installer on the other terminal. This happens to me several times whenever I install vmware. Probably because I didn't read the documentation before I started.

---

