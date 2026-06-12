---
title: "Problem With Make Oldconfig"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by issamneo on 2008-01-30
HI ALL
i'm using ubuntu 7.04 SERVER (2.6.20-15-server) i want to add vserver support:
i go to:
[http://linux-vserver.org/Welcome_to_Linux-VServer.org](http://linux-vserver.org/Welcome_to_Linux-VServer.org)
and i downlad the kernel 2.6.20.20 AND the patch file for 2.6.20.20

cd /usr/src/ && mkdir kernel && cd kernel
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.20.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.20.tar.bz2)
wget [http://ftp.linux-vserver.org/pub/kernel/vs2.2/patch-2.6.20.20-vs2.2.0.4.diff](http://ftp.linux-vserver.org/pub/kernel/vs2.2/patch-2.6.20.20-vs2.2.0.4.diff)
tar xfjv linux-2.6.20.20.tar.bz2
cd linux-2.6.20.20

THEN
cat ../patch-2.6.20.20-vs2.2.0.4.diff | patch -p1
cp /boot/vmlinuz-2.6.15-26-server .
 
HERE BEGIN THE PROBLEM
IF I DO

>sudo make oldconfig

it gives error
then i copy the /boot/config-2.6.20-15-server like that
> sudo cp /boot/config-2.6.20-15-server .config   ///    i'm in /usr/src/kernel/linux-2.6.20.20
>sudo make oldconfig

it gives always alot of error and warning related to the script : script/basic/filedep.c

any help pls

---

### Post by issamneo on 2008-01-31
can the problem be that i'm using the kernel 2.6.20.15 and i'm downloading the kernel and the patch for 2.6.20.20, coz it seems for me that it's normal i upgrade my system from .15 to .20 and then i patch it to support vserver
any help

---

### Post by issamneo on 2008-01-31
solved:

i have just to install the libc6_dev.

thanks for all.

---

