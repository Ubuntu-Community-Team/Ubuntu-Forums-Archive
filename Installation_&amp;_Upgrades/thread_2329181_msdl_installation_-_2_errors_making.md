---
title: "msdl installation - 2 errors making"
date: 2016-06-28
forum: Installation &amp; Upgrades
---

### Post by gadol89 on 2016-06-28
Hello,

I'm trying to install msdl (streaming download), if you know better alternative fell free to let me know.

after doing ./configure, I'm getting 2 errors by trying to do make command, which preventing me to make install.

my system:
> 
yosi@yosi-VirtualBox:~$ ls /usr/bin/gcc*
/usr/bin/gcc     /usr/bin/gcc-ar-5  /usr/bin/gcc-ranlib
/usr/bin/gcc-5   /usr/bin/gcc-nm    /usr/bin/gcc-ranlib-5
/usr/bin/gcc-ar  /usr/bin/gcc-nm-5
yosi@yosi-VirtualBox:~$ sudo mount -t vboxsf  d_drive /home/yosi/share
[sudo] password for yosi: 
yosi@yosi-VirtualBox:~$ lsusb && lsb_release -a && uname -r
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
4.4.0-21-generic
yosi@yosi-VirtualBox:~$ gcc -dumpversion
5.3.1




the errors:

> 
yosi@yosi-VirtualBox:~/Downloads/msdl-1.2.7-r2$ make
make  all-recursive
make[1]: Entering directory '/home/yosi/Downloads/msdl-1.2.7-r2'
Making all in src
make[2]: Entering directory '/home/yosi/Downloads/msdl-1.2.7-r2/src'
gcc  -g -O2   -o msdl asf.o asmrule.o display.o ftp.o http.o main.o mmsh.o mmst.o msdl.o msdllib.o network.o progress.o real.o realchallenge.o rmff.o rtsp.o sdpcommon.o sdpreal.o sdpwms.o wmserver.o url.o  
http.o: In function `http_encode_uri':
/home/yosi/Downloads/msdl-1.2.7-r2/src/http.c:456: undefined reference to `is_url_valid_char'
/home/yosi/Downloads/msdl-1.2.7-r2/src/http.c:467: undefined reference to `is_url_valid_char'
msdl.o: In function `get_url_list_from_file':
/home/yosi/Downloads/msdl-1.2.7-r2/src/msdl.c:361: undefined reference to `is_url_valid_char'
collect2: error: ld returned 1 exit status
Makefile:218: recipe for target 'msdl' failed
make[2]: *** [msdl] Error 1
make[2]: Leaving directory '/home/yosi/Downloads/msdl-1.2.7-r2/src'
Makefile:223: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/yosi/Downloads/msdl-1.2.7-r2'
Makefile:162: recipe for target 'all' failed
make: *** [all] Error 2





thanks.

---

### Post by steeldriver on 2016-06-28
Are you using gcc-5? if so, there have been some changes to the default handling of inline functions: see [Porting to GCC 5]("https://gcc.gnu.org/gcc-5/porting_to.html")

Try setting the C standard back to gnu89 as suggested in the linked page, e.g.

```

./configure "CFLAGS=-std=gnu89 -g -O2"

make clean

make

```

---

