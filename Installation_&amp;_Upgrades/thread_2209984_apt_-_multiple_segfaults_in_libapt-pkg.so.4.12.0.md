---
title: "apt - multiple segfaults in libapt-pkg.so.4.12.0"
date: 2014-03-08
forum: Installation &amp; Upgrades
---

### Post by mkuenemann on 2014-03-08
Hello,
I recently got a problem with apt-get after the last apt-get upgrade. I find following lines in dmesg:
********************
[   37.979438] apt-get[2818]: segfault at b6ece244 ip b76fde5f sp bfc5cee0 error 6 in libapt-pkg.so.4.12.0[b7630000+11d000]
[   75.169801] apt-check[3004]: segfault at b6a7c244 ip b7044e5f sp bfb71220 error 6 in libapt-pkg.so.4.12.0[b6f77000+11d000]
[  235.126074] apt-cache[3138]: segfault at b6e52244 ip b7681e3f sp bfb0c8a0 error 6 in libapt-pkg.so.4.12.0[b75b4000+11d000]
********************

I tried:
apt-get clean
rm -f /var/cache/apt/*.bin
apt-get -f install apt (does not work at all as apt breaks)

When I try to run apt-get upgrade, the system starts to read information an breaks without message.

I have no idea, how to fix this problem without building the whole system from scratch. Has anyone an idea?

Thanks!!!

Regards,
max

---

### Post by raja.genupula on 2014-03-08
Just give us the output of > apt-get update and > apt-cache policy libapt-pkg

---

### Post by mkuenemann on 2014-03-08
Hi Raja!
Thanks for the quick response!

I just found a possible solution by myself. I found in this blog:
[http://aziest.wordpress.com/2011/01/24/how-to-increase-your-apt-cache-limit/](http://aziest.wordpress.com/2011/01/24/how-to-increase-your-apt-cache-limit/)
a hint that it might be a memory problem. So I tried that, but it 
fixed the problems not completely. I instead added the following line in 
/etc/apt/apt.conf.d/70debconf
at the end: APT::Cache-Start "100000000";
That worked for now....

To answer your question:
apt-get updated crashed half the way and did not complete. And 
apt-cache policy libapt-pkg:
N: Paket libapt-pkg kann nicht gefunden werden

Thanks again!
Regards,
Max

---

