---
title: "Help: Installing 537EP Drivers"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by the_pc_dude on 2005-06-24
Can Someone help I having some Problems Give Details On How to Install no how-to's

---

### Post by the_pc_dude on 2005-06-25
what does this mean /home/sean/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:454: warning: initialization from incompatible pointer type
  LD [M]  /home/sean/intel-537EP_secure-2.60.80.1/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/sean/intel-537EP_secure-2.60.80.1/coredrv/.537core.lib.cmd for /home/sean/intel-537EP_secure-2.60.80.1/coredrv/537core.lib
  CC      /home/sean/intel-537EP_secure-2.60.80.1/coredrv/Intel537.mod.o
  LD [M]  /home/sean/intel-537EP_secure-2.60.80.1/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/sean/intel-537EP_secure-2.60.80.1/coredrv'
root@ubuntu:/home/sean/intel-537EP_secure-2.60.80.1 #

---

### Post by the_pc_dude on 2005-06-25
this was the attempt before this one LD [M]  /lost+found/intel-537EP_secure-2.60.80.1/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lost+found/intel-537EP_secure-2.60.80.1/coredrv/.537core.lib.cmd for /lost+found/intel-537EP_secure-2.60.80.1/coredrv/537core.lib  CC      /lost+found/intel-537EP_secure-2.60.80.1/coredrv/Intel537.mod.o
  LD [M]  /lost+found/intel-537EP_secure-2.60.80.1/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/lost+found/intel-537EP_secure-2.60.80.1/coredrv'root@ubuntu:/lost+found/intel-537EP_secure-2.60.80.1 # make install
rm -f /etc/hamregistry.bin
bash 537_inst

---

