---
title: "/usr/local/lib/xen/bin/qemu-system-i386: error while loading shared libraries: libnet"
date: 2020-10-24
forum: Installation &amp; Upgrades
---

### Post by marietto2008 on 2020-10-24
Hello to everyone.

I've upgraded ubuntu 20.04 to 20.10. Unfortunately when I try to start xen with these commands :

sudo /etc/init.d/xencommons start
sudo /etc/init.d/xendomains start
sudo /etc/init.d/xen-watchdog start
sudo /etc/init.d/xendriverdomain start

I get this error :

Starting /usr/local/sbin/oxenstored...Setting domain 0 name, domid and JSON config...
Done setting up Dom0
Starting xenconsoled...
Starting QEMU as disk backend for dom0
/usr/local/lib/xen/bin/qemu-system-i386: error while loading shared libraries: libnettle.so.7: cannot open shared object file: No such file or directory
 *   [done]
Starting xen-watchdog (via systemctl): xen-watchdog.service.

It didn't happen with ubuntu 20.04,so 20.10 removed some "obsolete" package. I tried to reinstall some packages related to nettle component,but the error didn't go away. Somone wants to help me ? thanks.

---

### Post by TheFu on 2020-10-24
I don't know your situation, but VM servers shouldn't be running non-LTS releases.

Thanks for being a tester.

---

### Post by marietto2008 on 2020-10-25
I have installed this package : libnettle7_3.5.1+really3.5.1-2_amd64 ; it didn't give any error. But ubuntu 20.10 comes with the libnettle8 package already installed. So now what ? I have the libnettle 7 and the 8 installed simultaneously ? anyway it seems that it works.

---

