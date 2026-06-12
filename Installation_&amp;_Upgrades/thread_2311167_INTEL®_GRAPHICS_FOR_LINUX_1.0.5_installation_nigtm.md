---
title: "INTEL® GRAPHICS FOR LINUX 1.0.5 installation nigtmare"
date: 2016-01-25
forum: Installation &amp; Upgrades
---

### Post by Qbi_Wan on 2016-01-25
I'm trying as titled, but i met SOME problems:
1. Do i need to use Intel_3100_gold_rhel30u6 or Intel_3100_gold_rhel40 folder or both, installed in the right order?
2. Release states that I need "Red Hat Enterprise Linux AS (or WS) Version 3, Update 6 "; what actually is that? I need 2 Linux releases to install it on Ubuntu 14.04? Synaptic packages manager have plenty of different similar described packages, which one to choose?
3. Release also states need of "Linux Kernel Source Code (AS Version 2.4.21-37.El, WS Version 2.4.21-4.EL)" I installed something named "linux-source-3.13.0" (I couldn't find 2.4.21-4.EL and 2.4.21-37.EL.); is that ok?
4. "GNU C Compiler Version 3.2.3'; once again no such version, I got "gcc-4.8"; is that ok?

 Other questions depends on four mentioned. Can somebody help?

---

### Post by siepo on 2016-01-25
Why do you want to install such a thing at all? Usually, Intel graphics just works in Linux.

---

### Post by Nuno_Abreu on 2016-01-25
Intel graphics usually work out of the box - probably your problem is related to hybrid graphics, am I correct? If not, what is the issue you're facing?

---

### Post by Bucky Ball on 2016-01-25
> **siepo said:**
> Why do you want to install such a thing at all? Usually, Intel graphics just works in Linux.

> **Nuno_Abreu said:**
> Intel graphics usually work out of the box - probably your problem is related to hybrid graphics, am I correct? If not, what is the issue you're facing?

Both of the above. You don't need to install anything unless you are having a problem. You might be suffering from a spot of 'Win-think'. You don't need to install a driver for every piece of hardware in Ubuntu (and if you're lucky, none). Lots of drivers are already contained in the kernel. Only bother with what isn't, evidenced by something not working or misbehaving.

If you are having a specific issue and therefore have a reason to be hunting for a solution, please spell it out for us. Otherwise, mark thread as solved and forget about installing drivers for Intel graphics. You don't need to if all is working.

To confirm you do have the correct driver already installed, open a terminal and paste in this command, enter your password (it will be invisible) then press enter:

```
sudo lshw -C video
```

Post the output back here between code tags (see the link in my signature for how to do that).

---

### Post by grahammechanical on 2016-01-25
> Release states that I need "Red Hat Enterprise Linux AS (or WS) Version 3, Update 6 "; what actually is that?

Red Hat is a commercial organisation and Red Hat Enterpirse Linux (RHEL) is a paid for version of the Red Hat Linux distribution. Red Hat and Its free to download companion Fedora use the Red Hat Package Management system (rpm).

Ubuntu is based on Debian and uses the Debian packaging system (deb).

So, you are trying to install the wrong driver package on Ubuntu.

Regards.

---

### Post by Nuno_Abreu on 2016-01-25
> **Bucky Ball said:**
> Both of the above. You don't need to install anything unless you are having a problem. You might be suffering from a spot of 'Win-think'. You don't need to install a driver for every piece of hardware in Ubuntu (and if you're lucky, none). Lots of drivers are already contained in the kernel. Only bother with what isn't, evidenced by something not working or misbehaving.

If you are having a specific issue and therefore have a reason to be hunting for a solution, please spell it out for us.

I'm not facing this problem myself - I have an old Pentium IV machine and it worked out of the box the first time I installed Linux on. I'm writing this from an AMD machine (my laptop) which before 14.04 was a pain due to lack of open-source driver support - now the drivers are a lot better than the proprietary ones.

Now, hybird graphics can be a pain because if you want to use both graphics cards/chips, Linux couldn't do it not a long time ago - and usually it is a combination of Intel's chip and NVIDIA's. I just wanted to know if he did have that problem.

I started to use Linux 3 or 4 years ago, do not remember - now I'm just facing a hard time figuring out how to solve a problem on Windows... So, pretty much not "Win-Thinking"...

---

### Post by Bucky Ball on 2016-01-25
> **grahammechanical said:**
> 

Ubuntu is based on Debian and uses the Debian packaging system (deb).

So, you are trying to install the wrong driver package on Ubuntu.

Regards.

And this. Slipped me by so well caught.

Redhat has nothing to do with Ubuntu apart from the fact they are both Linux distributions. Might pay to have a bit of a read up on Linux and what it's about, how it works. There are literally hundreds of Linux 'distros', some related, some distantly, some not at all. Because Redhat is a Linux distro it does not mean it has anything to do with Ubuntu. It doesn't. ;)

Windows has Windows. Mac has OSx. Linux has many distros and variations catering for general and specific computing purposes. [Look HERE]("http://distrowatch.com/").

---

### Post by Qbi_Wan on 2016-01-28
THX for so many replies ;)
I want to install it because my Game Maker Studio (PlayOnLinux) shows this info on game test:
[IMG]http://s16.postimg.org/6lpxt41bp/D3_D.png[/IMG]
I'm using Samsung N150 Plus netbook. With Windows on the same device it was working all fine. 
I have used all hints from WineHQ, but testing is still impossible. If drivers are not the problem then what?

& here's the output:
```
  *-display:0                    description: VGA compatible controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:f0300000-f037ffff ioport:18d0(size=8) memory:d0000000-dfffffff memory:f0000000-f00fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0380000-f03fffff
```

---

