---
title: "cant install anything"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by michaelgg13 on 2008-04-17
This is what i have..i keep getting this configure: error: C compiler cannot create executables? please help me.

michael@michael-desktop:~$ cd '/home/michael/Desktop/gtk+-2.12.9' 
michael@michael-desktop:~/Desktop/gtk+-2.12.9$ apt-get ./configure
E: Invalid operation ./configure
michael@michael-desktop:~/Desktop/gtk+-2.12.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for native Win32... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables<<<<<<<<<< help me here?
See `config.log' for more details.
michael@michael-desktop:~/Desktop/gtk+-2.12.9$

---

### Post by tamoneya on 2008-04-17
```
sudo ./configure
```

---

### Post by warp99 on 2008-04-17
What are you trying to compile that is not available in the repositories and what version of Ubuntu are you running? 6.06? 7.10? 8.04b?

---

### Post by michaelgg13 on 2008-04-17
7.10 and i just installed linux so i dont know much all the apps will not install cuased from the same error such as psptoolchain the gtk and synaptic

---

### Post by warp99 on 2008-04-17
If your setting up PSPtoolchain there are supporting packages that need to be installed before compiling. Here is a guide that talks about setting up PSPtoolchain on Ubuntu:

[http://www.guztech.nl/tutorials/38-psp/49-setting-up-the-psptoolchain](http://www.guztech.nl/tutorials/38-psp/49-setting-up-the-psptoolchain)

---

### Post by michaelgg13 on 2008-04-18
ok i found synaptic package installer on adimin panel thingy but i downloaded a couple programs and libraries how do i install those?

---

### Post by warp99 on 2008-04-18
> **michaelgg13 said:**
> ok i found synaptic package installer on adimin panel thingy but i downloaded a couple programs and libraries how do i install those?

[https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

Please see my signature for more helpful tips.

---

### Post by michaelgg13 on 2008-04-18
ok thanks that is pretty much all i need.

---

