---
title: "Linux-Headers are not the same on two computers"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2013-06-06
I have a laptop that has Linux-headers 3.2.0.37 and the update manager says system is up to date.  My desktop has Linux-Headers 3.2.0.45. Both are 64-bit, laptop is Intel CPU, and the desktop is AMD CPU.

The question is why are they not the same version of Linux-headers?

---

### Post by matt_symes on 2013-06-06
Hi

On both machines, can you post the output of

```
uname -r && dpkg -l | grep linux-headers
```

Kind regards

---

### Post by jlh68 on 2013-06-07
```
john@Eagle:~$ uname -r && dpkg -l | grep linux-headers 
3.2.0-45-generic 
ii  linux-headers-3.2.0-33                 3.2.0-33.52         Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-33-generic    3.2.0-33.52         Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-36                 3.2.0-36.57         Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-36-generic    3.2.0-36.57         Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-37                 3.2.0-37.58         Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-37-generic     3.2.0-37.58        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-38                 3.2.0-38.61         Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-38-generic     3.2.0-38.61        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-39                 3.2.0-39.62         Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-39-generic    3.2.0-39.62         Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-40                 3.2.0-40.64         Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-40-generic    3.2.0-40.64         Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-41                 3.2.0-41.66         Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-41-generic    3.2.0-41.66         Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-43                 3.2.0-43.68         Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-43-generic    3.2.0-43.68          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-44                 3.2.0-44.69          Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-44-generic    3.2.0-44.69          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-3.2.0-45                 3.2.0-45.70          Header files related to Linux kernel version 3.2.0 
ii  linux-headers-3.2.0-45-generic    3.2.0-45.70          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP 
ii  linux-headers-generic                  3.2.0.45.54           Generic Linux kernel headers 
john@Eagle:~$ 
```

```

john@Nighthawk:~$ uname -r && dpkg -l | grep linux-headers
3.2.0-37-generic
ii  linux-headers-3.2.0-36                 3.2.0-36.57          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic    3.2.0-36.57          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic    3.2.0-37.58          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.37.44           Generic Linux kernel headers
john@Nighthawk:~$
```

---

### Post by matt_symes on 2013-06-07
Hi

You are running two different kernel releases between your desktop and laptop. 

That, as i am sure you know, is why the headers are out.

The question is why :)

Have you pinned any packages ?

Please post the output of (on the laptop)

```
apt-mark showhold
```

On the desktop and the latop can you please post the output of

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

On the desktop and laptop, can you also post the output of

```
apt-cache show linux-image | grep -i filename
```

Kind regards

---

