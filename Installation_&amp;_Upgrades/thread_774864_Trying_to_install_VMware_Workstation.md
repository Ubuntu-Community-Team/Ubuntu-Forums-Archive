---
title: "Trying to install VMware Workstation"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by ChromeKaldra on 2008-04-29
I'm kinda new to linux so through what i've learned so far, i ran this code to install my Vmware.

```
cd Desktop/~/vmware-distrib
sudo perl vmware-install.pl

```

It asks me a lot of questions, i press enter to confirm the location it wants to store stuff, then near the end i get the error that it can't build a module.

```
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

```

So i follow the links and that reminded me that i need the any-anyupdate. So i run that in the same manner as i ran the above and i get:

```
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

```

Weird, same error. Is this a good way of installing things? Why can't it be a debian package...:(

I'm stranded w/o my VM, so this is vitally important to me. I have a lot of work i need to get done, including pieces for my art portfolio for admission requirements for college.

---

### Post by skunkTrader on 2008-04-29
apt-get install g++-4.2-multilib

---

### Post by ChromeKaldra on 2008-04-29
^ didn't work. Sorry. :(

---

### Post by raidensix on 2008-04-29
Did u try the vmware-any-any-update116?

---

### Post by markbl on 2008-04-29
> **raidensix said:**
> Did u try the vmware-any-any-update116?

That's the one that fixed it for me yesterday. My older copy of update115a did not work. Also had to do a "aptitude install build-essential" as well of course.

---

### Post by ChromeKaldra on 2008-04-30
> **markbl said:**
> Also had to do a "aptitude install build-essential" as well of course.

That's what did it for me. Now it's working. Thanks guys! :D

---

