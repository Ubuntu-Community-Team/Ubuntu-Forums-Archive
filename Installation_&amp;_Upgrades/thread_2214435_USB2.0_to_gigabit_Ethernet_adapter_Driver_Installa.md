---
title: "USB2.0 to gigabit Ethernet adapter Driver Installation using Ubuntu 11.10"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by Tabsy on 2014-04-01
Hi,

I am having issues installing the driver for USB21000S2 USB2.0 to gigabyte Ethernet adapter Driver Installation.

root@wmmps:~/Desktop/drivers-usb2eth/Linux/smsc7500# make
make -C /lib/modules/3.0.0-32-generic-pae/build SUBDIRS=/root/Desktop/drivers-usb2eth/Linux/smsc7500 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-32-generic-pae'
  CC [M]  /root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.o
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c: In function ‘smsc7500_rx_setmulticastlist’:
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c:1286:19: error: ‘struct net_device’ has no member named ‘mc_count’
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c:1288:39: error: ‘struct net_device’ has no member named ‘mc_list’
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c:1295:15: error: dereferencing pointer to incomplete type
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c:1296:35: error: dereferencing pointer to incomplete type
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c:1301:19: error: dereferencing pointer to incomplete type
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c:1303:32: error: ‘struct net_device’ has no member named ‘mc_count’
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c: In function ‘smsc7500_bind’:
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c:3195:5: error: implicit declaration of function ‘init_MUTEX’ [-Werror=implicit-function-declaration]
/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.c:3265:15: error: ‘struct usb_device’ has no member named ‘autosuspend_disabled’
cc1: some warnings being treated as errors

make[2]: *** [/root/Desktop/drivers-usb2eth/Linux/smsc7500/smsclan7500.o] Error 1
make[1]: *** [_module_/root/Desktop/drivers-usb2eth/Linux/smsc7500] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-32-generic-pae'
make: *** [modules] Error 2
root@wmmps:~/Desktop/drivers-usb2eth/Linux/smsc7500# 


Kernel version -
root@wmmps:~# uname -r
3.0.0-32-generic-pae

I tried with sudo apt-get update 
sudo apt-get install source
sudo apt-get linux-headers-3.0.0-32-generic-pae

But could not resolve the issue.




Kindly help.

Thanks,
Aamina

---

