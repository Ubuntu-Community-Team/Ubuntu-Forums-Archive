---
title: "VMware server config files erased after restart"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by gollybegully on 2007-04-06
VMware Server is installed on my system, but every time I reboot my computer it seems to forget and  prompts:

> vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

so I run through this configuration every time I want to use vmware after system reboot.  Here's some steps that I suspect might be crucial in solving this problem:
> 
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes]

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-11-generic/build/include] <--standard option, I just hit enter

Then comes this part:

> Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
**WARNING**: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x86_64.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

I think it's saving this configuration to a temp folder or something so every time I restart it's erased.  HELP!

---

