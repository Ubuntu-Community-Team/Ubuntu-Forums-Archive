---
title: "make localmodconfig doesn't work"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by graysky on 2010-08-23
The announcement of several new make scripts in the [2.6.32 release notes](http://kernelnewbies.org/Linux_2_6_32#head-11f54cdac41ad6150ef817fd68597554d9d05a5f) is very exciting.

> 1.8. Easy local kernel configuration

Most people uses the kernel shipped by distros - and that's good. But some people like to compile their own kernels from kernel.org, or maybe they like following the Linux development and want to try it. Configuring your own kernel, however, has become a very difficult and tedious task - there're too many options, and some times userspace software will stop working if you don't enable some key option. You can use a standard distro .config file, but it takes too many time to compile all the options it enables.

To make easier the process of configuration, a new build target has been added: make localmodconfig. It runs "lsmod" to find all the modules loaded on the current running system. It will read all the Makefiles to map which CONFIG enables a module. It will read the Kconfig files to find the dependencies and selects that may be needed to support a CONFIG. Finally, it reads the .config file and removes any module "=m" that is not needed to enable the currently loaded modules. With this tool, you can strip a distro .config of all the unuseful drivers that are not needed in our machine, and it will take much less time to build the kernel. There's an additional "make localyesconfig" target, in case you don't want to use modules and/or initrds.

localmodconfig  - Update current config disabling modules not loaded
localyesconfig  - Update current config converting local mods to core

So if I run them in that order, first the 'make localmodconfig' should only enable modules that I have currently loaded then the 'make localyesconfig' should switch them from modules to compiled into the kernel when I build it -- this is isn't the case for me.  

```
$ extract linux-2.6.35.tar.bz2 && cd linux-2.6.35
$ make mrproper
$ zcat /proc/config.gz > .config
$ make localmodconfig
$ make menuconfig
```

After running the the "make localmodconfig" script, have TONS of options that don't apply to my system flagged as modules when I inspect it via a "make menuconfig."  For example:

```
Device Drivers>Graphics support>Direct Rendering Manager
<M> ATI Radeon
[*] Enable modesetting on radeon by default
<M> Intel 830M, 845G, 852M, 855GM, 865G
<M> i915 driver
```

My system does not have ATI anything on board, nor does it have that those Intel chips.  

Here is another representation that there are many extra module options:

My distro's kernel config I'm using as a starting point:
```
$ cat .config | grep =m | wc -l
2434
```


The kernel config after I run the make localmodconfig:
```
cat .config-make | grep =m | wc -l
341
```

According to /proc/modules I only have 76 modules currently loaded:
```
$ cat /proc/modules | wc -l
76
```

What am I doing wrong?

---

### Post by graysky on 2010-09-19
Solved.  Tomk in [this thread](https://bbs.archlinux.org/viewtopic.php?id=103406) reported that for some reason, calling the streamline_config.pl script from the Makefile fails to give the advertised behavior.  Running it yourself however, does!

```
# chmod +x ./scripts/kconfig/streamline_config.pl && ./scripts/kconfig/streamline_config.pl > config_strip
# mv config_strip .config
# make oldconfig
```

---

