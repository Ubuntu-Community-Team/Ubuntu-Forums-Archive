---
title: "Kernel with minimum configuration"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by harry_12345 on 2008-03-28
Hello All

I have to recompile the kernel a lot of time since I have taken Kernel Programming as one of my subject in school.
I need to minimize the kernel compiling time (Presently It takes around 1:30).

 Could you guys provide me with some pointers as to how to minimize the complication time 
I particular I don't want module support, audio support, networking support,... basically a kernel with a minimum configuration

I anyone could provide me with the config file that would be great.

Thanks in advance

---

### Post by fadenb on 2008-05-26
Hi,
ever tried ccache? Or perhaps use distcc to balance the load on more computers (if available)

---

