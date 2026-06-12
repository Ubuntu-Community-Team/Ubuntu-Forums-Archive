---
title: "Change kernel"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by asai on 2010-08-05
Hi,
Is it possible to install a different kernel?

I have now a Generic kernel, but wants a Server kernel instead.
Is this possible? If so, how?

---

### Post by davidmohammed on 2010-08-05
yes -  and instructions [here]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds").  Why do you need to?

---

### Post by asai on 2010-08-05
Hi, thanks for your reply.

According to this: [https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases") the server edition of Hardy is supported until april 2013... :)

---

### Post by davidmohammed on 2010-08-05
that is true - if you are running Hardy server.  If you are running Hardy desktop, then the change of kernel doesnt mean that you get extra support - it still ends next year.

---

### Post by asai on 2010-08-07
I am running Hardy Server, with Generic kernel...:)

Isn't it possible to install the Server kernel with Apt?

---

### Post by Bachstelze on 2010-08-07
> **asai said:**
> 
Isn't it possible to install the Server kernel with Apt?

Yes

```
sudo apt-get install linux-server
```

---

### Post by asai on 2010-08-07
Perfect! Worked like a charm.
To remove the generic kernel:
```
sudo apt-get remove linux-generic
```
??

---

### Post by Bachstelze on 2010-08-07
Depends.  IF you have old kernels around, it will probably not remove them. You can use [font=monospace]dpkg -l | grep generic[/font] to see the packages you have installed.

---

### Post by asai on 2010-08-07
dpkg -l | grep generic gives this list:
```
ii  fontconfig                                 2.5.0-2ubuntu3               generic font configuration library - support
ii  fontconfig-config                          2.5.0-2ubuntu3               generic font configuration library - configu
ii  libcroco3                                  0.6.1-1build2                a generic Cascading Style Sheet (CSS) parsin
ii  libfontconfig1                             2.5.0-2ubuntu3               generic font configuration library - runtime
ii  linux-generic                              2.6.24.28.30                 Complete Generic Linux kernel
ii  linux-image-2.6.24-28-generic              2.6.24-28.73                 Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.28.30                 Generic Linux kernel image
ii  linux-restricted-modules-2.6.24-28-generic 2.6.24.18-28.6               Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-generic           2.6.24.28.30                 Restricted Linux modules for generic kernels
ii  linux-ubuntu-modules-2.6.24-28-generic     2.6.24-28.46                 Ubuntu supplied Linux modules for version 2.

```
Any way to remove any of these?

---

### Post by asai on 2010-08-09
Is there a way to remove Generic kernels?

---

