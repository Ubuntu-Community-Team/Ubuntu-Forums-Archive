---
title: "Upgrade kernel to get MPPE support???"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by toyitosal on 2007-04-03
Hi there
I have a littel problem configuring pptpd, i have a viretal server at vpsland, my kernel version is 2.6.16.33-vpsX, and i dont have MPPE support.
What i need to get MPPE support, im thinking on a kernel upgrade, is this correct????
How can i do it? maybe apt-get install linux-XXX....if so what version....

Thanks a lot

Hector

---

### Post by qneill on 2007-04-04
According to [http://pptpclient.sourceforge.net/howto-debian-build.phtmll](http://pptpclient.sourceforge.net/howto-debian-build.phtmll), MPPE should be in the kernel starting in 2.6.12 as a patch, and as part of the kernel.

On my Ubuntu 2.6.17-10-generic, looking at the kernel source I get: 
[INDENT][FONT="Courier New"]$ find . -type f -print | xargs grep -H -i MPPE 
./include/config/ppp/mppe/module.h:#define CONFIG_PPP_MPPE_MODULE 1
./include/linux/autoconf.h:#define CONFIG_PPP_MPPE_MODULE 1
./.config:CONFIG_PPP_MPPE=m[/FONT][/INDENT]

You may be able to just load it as a module.  I tried a few things and finally did this:

[INDENT][FONT="Courier New"]$ sudo insmod ppp_mppe[/FONT][/INDENT]

which loaded a module, not sure if that is the one you need or not.
-- 
Quentin

---

### Post by moon2js on 2007-09-10
I was trying to follow this [Debian pptpd HOWTO]("http://poptop.sourceforge.net/dox/debian-howto.phtml"), and it says to make sure my kernel supports MPPE with:

```
# modprobe ppp-compress-18 && echo success
```

...but that fails on my machine.

```
$ sudo insmod ppp_mppe
Password:
insmod: can't read 'ppp_mppe': No such file or directory
james@moonbase:~$ modprobe ppp-compress-18 && echo success
WARNING: Error inserting slhc (/lib/modules/2.6.20-16-generic/kernel/drivers/net/slhc.ko): Operation not permitted
WARNING: Error inserting ppp_generic (/lib/modules/2.6.20-16-generic/kernel/drivers/net/ppp_generic.ko): Operation not permitted
FATAL: Error inserting ppp_mppe (/lib/modules/2.6.20-16-generic/kernel/drivers/net/ppp_mppe.ko): Operation not permitted
```

From what I've read, I should be good...
```
$ uname -r
2.6.20-16-generic
```

Anyone else get this? Ignore, Retry, Abort?

Or is there a more 'buntu howto for poptop?

---

### Post by moon2js on 2007-09-10
> **qneill said:**
> 

You may be able to just load it as a module.  I tried a few things and finally did this:

[INDENT][FONT="Courier New"]$ sudo insmod ppp_mppe[/FONT][/INDENT]

which loaded a module, not sure if that is the one you need or not.
-- 
Quentin
```

$ sudo insmod ppp_mppe
Password:
insmod: can't read 'ppp_mppe': No such file or directory
```

No such luck.

---

### Post by tenwiseman on 2007-09-26
Hi moon2js

try

sudo modprobe ppp-compress-18 && echo success

--
Adrian C

---

### Post by moon2js on 2007-09-26
```
$ sudo modprobe ppp-compress-18 && echo success
Password:
success
```

oops. I guess I forgot the sudo. But I already figured that my kernel (from feisty) had the mppe support and I was just checking.

Thanks!

As I am now, I can log into my ubuntu poptop/pptpd from XP or OSX clients, but I can't do anything once logged in. I'm still trying to find a good howto.

---

