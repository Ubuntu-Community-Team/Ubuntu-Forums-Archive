---
title: "Running Windows 7 natively on Ubuntu through Wine."
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by Dangerzone812 on 2010-12-01
Hey everyone,

I've been thinking recently about switching to Ubuntu as my full time OS, BUT I still like aspects of windows, and want to use some of its features.

My question is this to you:

Is there any way (and if so, how?) for me to run Windows 7 natively on Ubuntu as well as seamlessly using wine? 

Thanks in advance,

Danger.

---

### Post by sikander3786 on 2010-12-01
Wine is a compatibility layer that allow running some Windows programs, not the whole OS.

However you can run Windows 7 in a virtual machine inside Ubuntu ;-)

I would advise Virtualbox from Software Center.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

[https://wiki.ubuntu.com/VirtualBox](https://wiki.ubuntu.com/VirtualBox)

There are many others like VMWare, Qemu etc etc but what I found to be the easiest and the best is Virtualbox.

---

### Post by pacoware on 2012-09-22
Hey their, 

I have found this distro called Zorin OS it's based on Ubuntu maybe you should give it a try.

[www.zorin-os.com/free.html]("http://www.zorin-os.com/free.html")

Good Luck,
Paco Ware

---

### Post by Mark Phelps on 2012-09-23
> **Dangerzone812 said:**
> ... 
Is there any way (and if so, how?) for me to run Windows 7 natively on Ubuntu 

NO -- there is no way to run one OS "natively" inside another OS.

> as well as seamlessly using wine? 
Again, NO.  Wine is not a Windows Emulator; instead, it is a set of DLLs that have been modified to make Linux system calls instead of Windows system calls -- which allow SOME Windows apps to run in Linux.

Of course, there is Virtualbox -- but that would NOT run Win7 natively and would require complete installation of Win7 to use it.

---

