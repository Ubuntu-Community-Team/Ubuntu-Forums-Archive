---
title: "linux/config.h: No such file or directory"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by tak1150 on 2007-04-21
After I upgraded to Feisty (did a clean install), I couldn't install my VPN software (from Cisco) for work because the install script which compiles the program stops immediately w/ this output;

/```
home/tak/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
```

So I looked in /usr/src/linux-headers-2.6.20-15-generic/include/linux, there is no "config.h"
But there is a "conf.h" and a "configfs.h". Should I make a symlink with one of these?

Actually the install script says it'll use the kernel source from /lib/modules/2.6.20-15-generic/build but the same situation there (ie no conf.h, because these folders are symlinked).

I'm sure that this is not a specific problem to installing this particular software because "config.h" sounds very generic. Please help! Thanks :)

---

### Post by fmerenda on 2007-04-23
> **tak1150 said:**
> After I upgraded to Feisty (did a clean install), I couldn't install my VPN software (from Cisco) for work because the install script which compiles the program stops immediately w/ this output;

/```
home/tak/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
```

So I looked in /usr/src/linux-headers-2.6.20-15-generic/include/linux, there is no "config.h"
But there is a "conf.h" and a "configfs.h". Should I make a symlink with one of these?

Actually the install script says it'll use the kernel source from /lib/modules/2.6.20-15-generic/build but the same situation there (ie no conf.h, because these folders are symlinked).

I'm sure that this is not a specific problem to installing this particular software because "config.h" sounds very generic. Please help! Thanks :)

Hi there,

I just got this working properly. I followed the instructions from here:

[http://www.archlinux.org/pipermail/arch/2006-December/012957.html](http://www.archlinux.org/pipermail/arch/2006-December/012957.html)

and now I can connect again.

Take care,
-Frank

---

### Post by tak1150 on 2007-04-23
Thanks. I got it working too.:)

---

### Post by ragingpenguin on 2007-04-24
There is a much easier to understand link here:

[http://tuxx-home.at/archives/2007/04/10/T15_55_43/]("http://tuxx-home.at/archives/2007/04/10/T15_55_43/")

Basically the issue is that the vpnclient is looking for some files in a location that is obsolete in the newer kernel. Therefore, the link provides a patch for the vpnclient and updates with the new location.

---

### Post by PCFascist on 2007-06-27
thanks ragingpenguin, that is a script I can use!

---

### Post by mojorising on 2007-10-03
Thanks! I had to use the updated script he links to on the bottom of the page since I am running Gutsy on my work PC and it worked great. 


Mike

---

### Post by aneeshk on 2008-05-26
I faced the same problem on 8.04.  You need a patch for kernel 2.6.24.

Instructions here: 
[http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/](http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/)

---

