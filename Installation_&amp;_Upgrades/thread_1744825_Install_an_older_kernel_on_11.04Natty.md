---
title: "Install an older kernel on 11.04/Natty"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by radioheads on 2011-04-30
Hi everyone!

Is there any legal way to install an older version of linux-kernel (say 2.6.35) on 11.04? By legal I mean - no source-compiling and third-party repo adding.

Would be very grateful with any help :)

---

### Post by Joe of loath on 2011-04-30
I don't think there is.

Besides, what's illegal about building from source or adding a ppa? ;)

---

### Post by radioheads on 2011-04-30
ough, just didn't want to mess with source-building =)
and what about 2.6.39? is there any backport for it?

---

### Post by taygan on 2011-05-01
You can still download older (and newer) kernels.  Whether they work with the rest of your system, dunno.

Look here:
[http://www.khattam.info/howto-install-linux-kernel-2-6-36-or-2-6-37-in-debian-squeeze-testing-or-ubuntu-or-any-debian-based-distribution-without-compiling-2010-11-13.html]("http://www.khattam.info/howto-install-linux-kernel-2-6-36-or-2-6-37-in-debian-squeeze-testing-or-ubuntu-or-any-debian-based-distribution-without-compiling-2010-11-13.html")

---

### Post by jacksaff on 2011-05-01
If you have upgraded you should still have the old kernel, just select it from the grub menu when you boot. 
If you have a fresh install, change the distribution name in synaptic>settings>repositories for the 'natty main' repo from natty to maverick. Reload, select the kernel you want and install it, and then change the name back and reload again. You should then be able to select the older kernel in grub when you reboot.

---

### Post by VinDSL on 2011-05-01
> **radioheads said:**
> Hi everyone!

Is there any legal way to install an older version of linux-kernel (say 2.6.35) on 11.04? By legal I mean - no source-compiling and third-party repo adding.

Would be very grateful with any help :)
The oldest kernel that I'm aware of is 2.6.36.1-natty

[INDENT]Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.1-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.1-natty/)[/INDENT]


Currently, I have two kernels installed on this machine:

2.6.37.6-natty

[INDENT]Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/)[/INDENT]

2.6.39-rc4-natty

[INDENT]Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/)[/INDENT]


They both work fine!

Installing them is easy.  All I do is:

[LIST]
[*]Download the proper files for my architecture. In my case, the 2 i386.deb files & the all.deb file (3 files total).

[*]I place them in ~/home/vindsl/Downloads/Kernel (but you can put them anywhere).

[*]Open a terminal and navigate to the folder that contains the debs.

[*]Run sudo dpkg -i *.deb

[*]If everything builds correctly, I reboot.
[/LIST]

That's about all there is to it.

Oh, and, don't delete your old kernel, until you've thoroughly tested the new one...  ;)

---

### Post by VinDSL on 2011-05-01
> **radioheads said:**
> [...] and what about 2.6.39?
Heh!

```

vindsl@Zuul:~$ sudo cat /proc/driver/nvidia/version
[sudo] password for vindsl: 
NVRM version: **[COLOR="Red"]NVIDIA UNIX x86 Kernel Module  270.41.06[/COLOR]**  Mon Apr 18 14:54:25 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
vindsl@Zuul:~$ uname -a
Linux Zuul **[COLOR="red"]2.6.39-020639rc4-generic[/COLOR]** #201104191410 SMP Tue Apr 19 15:45:56 UTC 2011 i686 i686 i386 GNU/Linux
vindsl@Zuul:~$ unity --version
**[COLOR="red"]unity 3.8.12[/COLOR]**
vindsl@Zuul:~$ 

```

No problem!  :)

---

### Post by xgt001 on 2011-06-14
hey folks!!! i installed an older stable kernel 2.6.37 after doing a fresh install of 11.04... i basically have an ati card... but i dint install fglrx driver yet...so after installing the older kernel 
[ i installed by above said method.. that is downloading the deb files from the kernel.ubuntu.com ] installation gets done but when i select the older kernel from the grub ... it just fails to boot... but it boots fine in the default natty kernel.. could any body help me to get the older kernel kicking into action :p

---

### Post by cipherboy_loc on 2011-06-14
xgt001, you should probably post in a new thread, but:

1) When you say you haven't installed the fglrx driver yet, did you have it before you installed the older kernel?
2) What are the error messages when booting the older kernel?

---

