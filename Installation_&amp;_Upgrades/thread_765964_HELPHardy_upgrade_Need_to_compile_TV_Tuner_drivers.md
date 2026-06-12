---
title: "HELP:Hardy upgrade Need to compile TV Tuner drivers, but &quot;make&quot; points to old kernel!"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by sharris203 on 2008-04-24
I used v4l drivers to compile drivers for my TV Tuner on 7.10. Worked fine. Upgraded to Hardy, and need to re-compile for the new kernel. however, everytime I try to compile, it uses the 7.10 kernel. You can see below. So how do I make the "make" command use the new kernel?? 

```
/usr/src/v4l-dvb-experimental$ sudo make
make -C /usr/src/v4l-dvb-experimental/v4l 
make[1]: Entering directory `/usr/src/v4l-dvb-experimental/v4l'
creating symbolic links...
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/v4l-dvb-experimental/v4l  modules 
```etc.

Does compile but I cannot use it. I'm not using 2.6.22-14. I'm using 2.6.24-16.

---

### Post by sharris203 on 2008-04-25
solved... partially. "sudo make kernel-links" fixed the kernel linking, but after compiling/intalling the v4l drivers, the kernel hangs on loading ntp server on boot. Works ok again if i reinstall the kernel. Ack, I'll stick with the old kernel for now (although my wifi did stop working in it...)

---

