---
title: "Installing a tar.gz program"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by w9fcc on 2010-02-03
I'm trying to install a VPN client from my employer and having trouble.
I tried to do this:

tar -xvzf vpnclient-linux.tar.gz
cd vpnclient
./configure
make
sudo make install

-----------------

I have build-essential installed.
When I enter the ./configure command, I get this:

bash: ./configure: No such file or directory
dan@dan-desktop:~/Desktop/VPN/vpnclient$ 


If I list the files in this directory (ls) I get:

dan@dan-desktop:~/Desktop/VPN/vpnclient$ ls
cisco_cert_mgr   interceptor.c          license.txt    vpnapi.h
Cniapi.h         IPSecDrvOSFunctions.h  linuxcniapi.c  vpnclient
config.h         IPSecDrvOS_linux.c     linuxcniapi.h  vpnclient.ini
cvpnd            IPSecDrvOS_linux.h     linux_os.h     vpnclient_init
driver_build.sh  ipseclog               Makefile       vpn_install
frag.c           libdriver.so           mtu.h          vpn_ioctl_linux.h
frag.h           libvpnapi.so           sample.pcf     vpn_uninstall
GenDefs.h        license.rtf            unixcniapi.h
dan@dan-desktop:~/Desktop/VPN/vpnclient$ 

I've never tried this before. Can anyone lead this old
noobie down the right path?

I'm running Ubuntu 9.10 by the way.

Thanks.

Dan in Minnesota

---

### Post by amauk on 2010-02-03
looks like there's no configure script
but there is a Makefile already

(so, just do make & sudo make install without the configure)

---

### Post by w9fcc on 2010-02-03
Thanks.

Tried that and got:

dan@dan-desktop:~/Desktop/VPN/vpnclient$ make
make -C /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/dan/Desktop/VPN/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/dan/Desktop/VPN/vpnclient/linuxcniapi.o
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /home/dan/Desktop/VPN/vpnclient/Cniapi.h:15,
                 from /home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:34:
/home/dan/Desktop/VPN/vpnclient/GenDefs.h:114: error: conflicting types for ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’
/home/dan/Desktop/VPN/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/dan/Desktop/VPN/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/dan/Desktop/VPN/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [default] Error 2
dan@dan-desktop:~/Desktop/VPN/vpnclient$ 

-------------------------

Maybe I'd just better forget it until I've done
a lot more studying. Or maybe this program just
won't work on Ubuntu. Can't find anyone at work
who knows who made this tar file.

Thanks anyway.

---

### Post by amauk on 2010-02-03
Unless there's something unique about this VPN client (unlikely), just ask for the login details and use the VPN client from the ubuntu repositories

---

