---
title: "Trouble with Installing VPN Client"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by dagarshali on 2008-04-19
Hi,
I am very very new to linux world. I installed ubuntu 7.10-gutsy version. I order to access some of the softwares from off campus, we need to install the vpn client provided by our school. The link of the website is [http://www.it.iastate.edu/pub/lng335/lng_335.html](http://www.it.iastate.edu/pub/lng335/lng_335.html)

It says to type in terminal
rpm -q kernel-source, and when i do that...I get 

> root@dagarshali-desktop:/usr/src# rpm -q kernel-source
package kernel-source is not installed
root@dagarshali-desktop:/usr/src# 

the document then asks to install the kernel-source. I also did > uname -r at the terminal and got 2.6.22.14-generic as output

When I go to the folder

/usr/src/ I find folders name linux-headers-2.6.22.14, linux-headers-2.6.22.14-generic and another folder called rpm.

when installing the vpn client it asks for the path for the kernel source. when i give /usr/src/linux-headers-2.6.22.14-generic, it gives

> Making module
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/dagarshali/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/dagarshali/Desktop/vpnclient/linuxcniapi.o
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/dagarshali/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/dagarshali/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Please help

Regards,
vishwa

---

