---
title: "Is hardware drivers installation required on ubuntu"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by durga11 on 2009-12-26
Hi,I had installed ubuntu 9.10 on my new lenovo laptop which has a intel 245 chipset in it.I had a problem running few of games .I had no idea if we need to install any hardware drivers.Till now i havent installed any hardware drivers. My question is if I had to install any drivers explicitly as it is a new installation.

With the forms help i had chked few things related to this. pls use it for ur reference
**->**
durga@durga-laptop:~$ sudo lshw -C video
[sudo] password for durga: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:f4000000-f43fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f4400000-f44fffff
**->**
system-adminsitration->hardware drivers  is showing the o/p as [B]No proprietory drivers are in use on this system .

->
[/B]durga@durga-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)Thanks in advance

---

### Post by byStanderone on 2009-12-26
...being a noob by myself, i look at drivers as language interpreters between the existing hardware and programs that exist in a computer system. drivers are the go between the two, for proper execution of programs...hence drivers are prime necessities in every system.

---

### Post by durga11 on 2009-12-27
Thanks for the reply, Can you tell me what are all the drivers that are needed to be required on my system.

---

### Post by cascade9 on 2009-12-27
Nope, that doesnt need any proprietary drivers. 

> In general, Intel graphics driver is well integrated in Linux        distributions so users won't worry about the driver setup.

[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

All the Intel graphics drivers (and chipset drivers) are kernel or free software based as far as I know.

---

### Post by noway2 on 2009-12-27
A partial answer to your question: at every startup, the system hardware is scanned and the appropriate drivers are chosen and loaded.  This allows you to do things (very unlike Windows) such as placing the HDD into an entirely different machine and it will run correctly.

You may also want to look at the log files, such as udev.log and kernel.log.  The log files, though difficult for a newbie to interpret, will contain this information.

---

