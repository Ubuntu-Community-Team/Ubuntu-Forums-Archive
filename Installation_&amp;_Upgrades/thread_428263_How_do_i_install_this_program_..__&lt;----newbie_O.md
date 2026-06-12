---
title: "How do i install this program .. ? &lt;----newbie :O"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by exidez on 2007-04-30
i am completely new to linux so i dont really understand why we use commands like make and make install etc...
anyway, i am trying to install this program from work that enables me to connect to their network....
if i had windows it would be easy but i have strait linux now.. no dual boot

i used the make command and this is what i get
exidez@UNKNOWN:~/vpnclient$ make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/exidez/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/exidez/vpnclient/linuxcniapi.o
/home/exidez/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/exidez/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/exidez/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

these are all the files in the directory:
.                interceptor.c          linuxcniapi.c     unixkernelapi.h
..               IPSecDrvOSFunctions.h  linuxcniapi.h     vpnapi.h
cisco_cert_mgr   IPSecDrvOS_linux.c     .linuxcniapi.o.d  vpnclient
Cniapi.h         IPSecDrvOS_linux.h     linuxkernelapi.c  vpnclient.ini
config.h         ipseclog               linux_os.h        vpnclient_init
cvpnd            libdriver64.so         Makefile          vpn_install
driver_build.sh  libdriver.so           mtu.h             vpn_install~
frag.c           libvpnapi.so           sample.pcf        vpn_ioctl_linux.h
frag.h           license.rtf            .tmp_versions     vpn_uninstall
GenDefs.h        license.txt            unixcniapi.h


I tries to run the script vpn_install using the command sh vpn_install but i get this error
vpn_install: 47: Syntax error: "(" unexpected

Line 47 states:
function getvalue() {
    ans='!'
    local rp=$1
    local dflt=$2
   
    printf "\n%s [%s]" "$rp" "$dflt"


etc.... etc...
What is wrong? why cant i install it?

---

### Post by public_void on 2007-04-30
From looking at the output, I'm guessing your trying to install vpnclient. This [guide]("http://popey.com/node/62") for Ubuntu 6.06 should help. It seems your missing the kernel headers, to get them do
```
sudo apt-get install linux-headers-`uname -r`
```Note the character before uname is a `, not a ', a quick shortcut is to copy (Ctrl+C) and paste into the terminal (Ctrl+Shift+V).

---

### Post by exidez on 2007-04-30
that is correct i am installing that
the above command didnt work though, looks like i allready have the latest

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-15-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

as for the guide i followed it and this is what happended....
$ patch -p0 < vpnclient-linux-4.7.patch.txt
patching file linuxcniapi.c
Hunk #2 FAILED at 291.
Hunk #3 succeeded at 403 (offset 9 lines).
Hunk #4 FAILED at 445.
2 out of 4 hunks FAILED -- saving rejects to file linuxcniapi.c.rej
exidez@UNKNOWN:~/vpnclient$ make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/exidez/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/exidez/vpnclient/linuxcniapi.o
/home/exidez/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/exidez/vpnclient/linuxcniapi.c: In function &#8216;CniInjectReceive&#8217;:
/home/exidez/vpnclient/linuxcniapi.c:279: warning: unused variable &#8216;timecount&#8217;
/home/exidez/vpnclient/linuxcniapi.c: In function &#8216;CniInjectSend&#8217;:
/home/exidez/vpnclient/linuxcniapi.c:403: warning: unused variable &#8216;timecount&#8217;
make[2]: *** [/home/exidez/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/exidez/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

---

### Post by exidez on 2007-04-30
ok i followed the guide on [http://doc.gwos.org/index.php/Cisco_VPN_Client](http://doc.gwos.org/index.php/Cisco_VPN_Client)



now i get this error:
Making module
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/exidez/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/exidez/vpnclient/linuxcniapi.o
/home/exidez/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/exidez/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/exidez/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

now what... ?:confused:

---

### Post by exidez on 2007-04-30
i just found this thread: [http://ubuntuforums.org/showthread.php?p=2564752#post2564752](http://ubuntuforums.org/showthread.php?p=2564752#post2564752)

but as you can see i cant use the patch... :confused: 
it hangs on me

edit////////////

Ok i fixed the problem
it looks like to apply the patch i need to type
patch -i <the file name>

i didint have -i before

it has installed great now

---

