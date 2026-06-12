---
title: "Upgraded dapper to edgy and now VMWare Server Console broken"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by verucabong on 2007-04-20
Hi Everyone-

I've upgraded from Dapper to Edgy using the recommended method so that I can get myself to Feisty.  In re-setting up my VMWare Server, I've run into a problem.  I upgraded my kernel headers using apt-get and then re-ran /usr/bin/vmware-config.pl

Everything in the config script looked ok until I ran into this:

```
  MODPOST
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

   Shutting down http.vmware: -ne                                     failed

   Starting httpd.vmware:-ne                                          failed

```

Otherwise, the rest of the config script process was ok.  However, now when I try to launch the VMWare Server Console, it says it's starting and then disappears.  I never see the application's window.  Can someone point me in the right direction?

---

### Post by verucabong on 2007-04-20
---FIXED---

I had the double library problem.  

Typed in:

```
sudo apt-get remove libdbus-1-2

```

Admin... close thread please :)

---

### Post by GSMD on 2007-05-14
Another tip is to make sure that /bin/sh points to /bin/bash (and not /bin/dash wihich is a default behaviour).

---

