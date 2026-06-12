---
title: "no kernel upgrades on 14.04 LTS"
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by sulla on 2016-01-31
Dear all!

my productive machine is a several-time upgraded ubuntu server, not on 14.04 LTS.
It currently runs kernel
```
$ uname -a
Linux freedom 3.13.0-76-generic #120-Ubuntu SMP Mon Jan 18 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

but every
```
$ sudo apt-get dist-upgrade
sulla@freedom:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```
tells me there is nothing to do.

I just set up a test system with a freshly installed 14.04.3 LTS, and this runs kernel
```
$ uname -a
Linux freeplay 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

I noticed that the /etc/apt/sources.list is different.
The production server has
```
deb http://at.archive.ubuntu.com/ubuntu/ trusty main
```
while the test system has
```
deb http://at.archive.ubuntu.com/ubuntu/ trusty main **restricted**
```
is this the reason?

Can anyone clarify to me what is wrong with my productive system, why is it not getting upgrades?
Problem is that I own a piece of hardware that is not recognized on the production system but is up and running on the test system and I suspect it is the old kernel that is preventig it from working.

---

### Post by sulla on 2016-01-31
ok, I added the restricted component, no difference.
I even copied the sources.list file from the test system to the productive system, no difference.

---

### Post by ajgreeny on 2016-01-31
This is all related to the hardware-enablement stack [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) which is not really necessary for a server with no GUI, unless you specifically need some of the extra kernel drivers, though you still will not need any of the graphic software enhancement packages.

You can add the higher series of the kernel alone by installing the **linux-generic-lts-vivid** package which will bring in all the 3.19.0-47 packages of that series and ensure they are continuously updated from that point as new versions arrive in the repos.  You can also move to the wily series 4.2.0-25 if you want to try it.

However, if the 3.13.0- series is doing all that you need, it is probably less trouble to keep that as it will continue to be supported until the end of trusty's support period; if you change to the vivd or wily series they will all have only 9 months of support in total, so vivid is nearly finished already and wily has only 6 months left.  When xenial (16.04) appears in April there may well be a chance to use the kernel series from that but it is certainly not available at the moment in the normal repos.

---

### Post by sulla on 2016-01-31
OK, thank you!
As this is a production server (indeed without GUI) I stick to LTS (just to avoid upgrading too often), but I do usually upgrade from LTS to LTS, so the next do-release-upgrade will not be far away.
For the moment I'll continue the tests with the new hardware on the test-system with it's 3.19 kernel that knows this hardware, and when I'll move the hardware over to the production system I'll give the linux-generic-lts-vivid a try.

---

