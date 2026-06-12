---
title: "ERROR when I compile&amp;install linux kernel 2.6.27.1 &amp; linux kernel 2.6.27-7.12(ubuntu)"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by myheimu on 2008-10-20
I'm a new Ubuntu user in China, and my computer has intel E8400 CPU & Nvidia 9600GT.
I use Ubuntu 8.10 beta, and nvidia 177.80 driver(install by apt-get itself).
 I try to compile&install linux kernel 2.6.27.1, and also try ubuntu's linux-source 2.6.27-7.12. Both of them have this problem.

When I install the kernel...Well, I can use the kernel with GPU working well now.

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/liv/dpkg/info/linux-image-2.6.27-1020-hm.postinst line 1181
dpkg: linux-image-2.6.27-1020-hm(--configure) error:
subprocess post-installation script returned error exit status 2

---

### Post by plun on 2008-10-20
Hello and welcome  :)

No need to compile a kernel, Ubuntu uses packages.

Please choose a chinese server which is updated today, cn99 and lupaworld seeems to be 2 days left-behind 

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Meny System > Administration >Software Sources

then please start the terminal
```

sudo apt-get update

sudo apt-get upgrade
```

Below will check for latest kernel for your flavour

```
sudo apt-get install linux
```


Good Luck !

---

### Post by myheimu on 2008-10-20
Thanks for your reply, but I'm sorry to say that I HAD update my kernel from the servers.....

I want to compile my own kernel because I have 4G memory & I want a optimized system.

What's a pity that normal ubuntu kernel does's support 4G memory completly...

---

### Post by Slug71 on 2008-10-20
Use Ubuntu 64bit.

---

### Post by syko21 on 2008-10-20
Doesn't the server kernel use PAE for 4GB support on 32 bit?

---

### Post by myheimu on 2008-10-20
> **syko21 said:**
> Doesn't the server kernel use PAE for 4GB support on 32 bit?
Is there something called "the server kernel"? I'm not sure. Maybe there's only ubuntu server but not linux server kernel.

AND I don't want to use ubuntu 64bit because software support and something else...

That's no person kown about Compiling kernel here???

---

### Post by syko21 on 2008-10-20
> **myheimu said:**
> Is there something called "the server kernel"? I'm not sure. Maybe there's only ubuntu server but not linux server kernel.

AND I don't want to use ubuntu 64bit because software support and something else...

That's no person kown about Compiling kernel here???

I meant the ubuntu kernel server package. If you install this package 
**[B]linux-image-2.6.27-7-server**[/B]

and choose it when you start up your computer then it should see all 4Gb of your RAM.

---

### Post by cariboo on 2008-10-20
There is an Ubuntu server kernel, just open Synaptic and search for linux-image-2.6.27-7-server. Or as another poster said you could run the 64bit version.

Jim

Beat me to it :)

---

### Post by Slug71 on 2008-10-21
> **myheimu said:**
> Is there something called "the server kernel"? I'm not sure. Maybe there's only ubuntu server but not linux server kernel.

AND I don't want to use ubuntu 64bit because software support and something else...

That's no person kown about Compiling kernel here???

64bit has very good support. Has all the 32bit libs so 32bit apps are still supported. I have Google Earth and Limewire 32bit installed and works perfect.:guitar:

---

### Post by antiram on 2008-10-21
remove package nvidia-common completly with --purge

---

### Post by MighMoS on 2008-10-28
So does anyone know what the actual solution is rather than working around the problem?

Some of us for various reasons would prefer to run a custom kernel and it would be nice if system utilities didn't crash and burn when we tried to do so.

---

