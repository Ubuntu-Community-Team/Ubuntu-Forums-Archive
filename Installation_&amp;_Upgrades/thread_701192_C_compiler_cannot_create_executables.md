---
title: "C compiler cannot create executables"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by _linuxnewbie on 2008-02-19
Hey I have another problem, seems like I need to go through a kind of initial setup to get things work on the newly installed ubuntu on my laptop!!

I tried to compile a package called SphinxTrainer using the command:
phanee@phanee:~/tutorial/SphinxTrain$ ./configure

This gave the following error:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I checked config.log file then I checked if gcc, libusb were installed and were indeed. Then I tried installing g++ as follows:
phanee@phanee:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g

The process of installing new softwares doesnt seem to be straight forward. why is it so? Kindly suggest me a solution or an alternate for this.

Thanking in advance,
Phanee S

---

### Post by yabbadabbadont on 2008-02-19
Make sure that the permissions on /tmp are 1777.

```
sudo chmod 1777 /tmp
```

Edit: Also, the package you most likely want to install is build-essential

---

### Post by t1kky on 2008-02-20
Hi, i have much the same problem.
I tried to use the default gcc but it gives "stdio.h : No such file ".On another forum someone tiped me to use crosstool but during the instalation it gives me the same 
problem:

creating cache ./config.cache
checking host system type... i686-host_pc-linux-gnulibc1
checking target system type... i686-unknown-linux-gnu
checking build system type... i686-host_pc-linux-gnulibc1
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

Any ideas?

---

### Post by dstew on 2008-02-20
You need to install the package build-essential as mentioned by yabbadabbadont:```
sudo apt-get install build-essential
```This package has the standard headers in it.

---

### Post by Nameless_one on 2008-02-20
@_linuxnewbie
I suspect that when you tried to install g++, it didn't work because + is handled by bash as an operator, and so bash saw 'sudo apt-get install g++' as 'sudo apt-get install g' with two operators at the end. You could use this:

```
$ sudo apt-get install g\+\+
```

however, to install everything required to compile applications, you should install build-essential as mentioned above.

---

### Post by t1kky on 2008-02-20
thanks a million mate ;)

---

