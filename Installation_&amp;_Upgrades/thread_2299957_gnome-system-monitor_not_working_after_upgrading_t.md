---
title: "gnome-system-monitor not working after upgrading to 15.10"
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by Teddy_Wang on 2015-10-22
Has anybody come across this yet?

gnome-system-monitor: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1: undefined symbol: _ZN4Glib11VariantTypeD1Ev

Not a huge deal, but I'd like to get the System Monitor working again, so any help would be greatly appreciated.

Thanks

---

### Post by vedavrata on 2015-10-23
$ sudo gparted
[sudo] password: 
[B]/usr/sbin/gpartedbin: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1: undefined symbol: _ZN4Glib11VariantTypeD1Ev
[/B]$ 

What to do?

---

### Post by ducanh-babim on 2015-10-24
all application need 'libglibmm-2.4-1v5' are error .....[B]/libgiomm-2.4.so.1: undefined symbol: _ZN4Glib11VariantTypeD1Ev

[/B]I don't know how to fix. Wait reply

---

### Post by tancerz77 on 2015-10-24
I have the same problem, but with mate-system-monitor. Everything was fine till tonight. 

mate-system-monitor: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1: undefined symbol: _ZN4Glib11VariantTypeD1Ev
Maybe it's nut our fault but apt-get update/upgrade fault? It was clean installation in my case.

---

### Post by Teddy_Wang on 2015-10-27
> **vedavrata said:**
> $ sudo gparted
[sudo] password: 
[B]/usr/sbin/gpartedbin: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1: undefined symbol: _ZN4Glib11VariantTypeD1Ev
[/B]$ 

What to do?

At least for me, it must be something to do with accessing apps that require elevated privs work in 15.10. After I tried gparted (which works fine both from the command line as well as through the UI, which prompts me for authentication), I was able to start gnome-system-monitor with "sudo gnome-system-monitor" from the command line.

---

### Post by jam707 on 2015-10-27
I also get this with System Monitor and mysql workbench.


jr@jr:~$ sudo mysql-workbench
/usr/lib/mysql-workbench/mysql-workbench-bin: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1: undefined symbol: _ZN4Glib11VariantTypeD1Ev
jr@jr:~$ sudo gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1: undefined symbol: _ZN4Glib11VariantTypeD1Ev

---

### Post by gdeabvgmail on 2015-10-28
I have the same problem. In my case,  the reason is vmware libs.  You need to run:
     ldd  /usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1 
In my case  /usr/lib/vmware/lib/libglibmm-2.4.so.1/libglibmm-2.4.so.1 is wrong. If i rename it, all applications will work normally except VMware apps.

---

### Post by pae4646 on 2015-11-07
Use kSysGuard - good alternative
```
sudo apt-get install ksysguard
```

---

### Post by SpUpUz on 2015-11-13
same problem form me, and also gparted not working :/

---

### Post by shai3 on 2016-03-08
I've got this same problem when trying to start mysql-workbench.

---

