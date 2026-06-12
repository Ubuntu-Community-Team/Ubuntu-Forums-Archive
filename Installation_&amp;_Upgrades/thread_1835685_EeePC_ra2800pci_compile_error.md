---
title: "EeePC ra2800pci compile error"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-08-29
I got an error while compiling the ra2800 driver for my EeePC:

> root@nb:~/ralink/RT2860# make
make -C tools
make[1]: Entering directory `/root/ralink/RT2860/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/ralink/RT2860/tools'
/root/ralink/RT2860/tools/bin2h
cp -f os/linux/Makefile.6 /root/ralink/RT2860/os/linux/Makefile
make  -C  /lib/modules/2.6.38-11-generic/build SUBDIRS=/root/ralink/RT2860/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /root/ralink/RT2860/os/linux/../../os/linux/rt_linux.o
/root/ralink/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/root/ralink/RT2860/os/linux/../../os/linux/rt_linux.c:1689:10: error: ‘struct net_device’ has no member named ‘open’
/root/ralink/RT2860/os/linux/../../os/linux/rt_linux.c:1690:10: error: ‘struct net_device’ has no member named ‘stop’
/root/ralink/RT2860/os/linux/../../os/linux/rt_linux.c:1691:10: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/root/ralink/RT2860/os/linux/../../os/linux/rt_linux.c:1692:10: error: ‘struct net_device’ has no member named ‘do_ioctl’
/root/ralink/RT2860/os/linux/../../os/linux/rt_linux.c:1702:11: error: ‘struct net_device’ has no member named ‘get_stats’
/root/ralink/RT2860/os/linux/../../os/linux/rt_linux.c:1736:9: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/root/ralink/RT2860/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/root/ralink/RT2860/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [LINUX] Error 2
root@nb:~/ralink/RT2860# 


What do I need to do to get it compiled?

bye

Ronald

---

### Post by gordintoronto on 2011-08-29
Did you install build-essential?

---

### Post by ELMIT on 2011-08-30
Yes, I have installed build-essential

---

