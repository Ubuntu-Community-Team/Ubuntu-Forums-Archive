---
title: "[SOLVED] NEED HELP - Installation of Canon PIXMA iP 2200 - Ubuntu 8.10"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by user-max on 2008-11-05
Hello all, I never posted before, since I always got answers via different sources, but seeing how most of the answers come from this nice forum, I will give it a try. Thank you for taking the time to help me out.

New distro of Ubuntu 8.10
HP dv2000 (dv2500) laptop
Canon PIXMA iP 2200

I downloaded a tar.gz drivers from Canon website that are cnijfilter-ip2200-lprng_2.60-1_i386.deb, cnijfilter-common_2.60-1_i386.deb, cnijfilter-ip2200_2.60-1_i386.deb. Originally they were RPM, but I converted with Alien.

First 2 installed fine, without any errors in terminal. But the last one (cnijfilter-ip2200_2.60-1_i386.deb) gives this output:

max@armageddon:~/Desktop$ sudo dpkg -i cnijfilter-ip2200_2.60-1_i386.deb 
(Reading database ... 119762 files and directories currently installed.)
Unpacking cnijfilter-ip2200 (from cnijfilter-ip2200_2.60-1_i386.deb) ...
dpkg: error processing cnijfilter-ip2200_2.60-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libcnbpess256.so.2.2.2', which is also in package libcnbj-2.6
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-ip2200_2.60-1_i386.deb


No idea as to what to do in this case. Help is greatly appreciated.

---

### Post by user-max on 2008-11-06
bump == >>  Anybody ?:)

---

### Post by user-max on 2008-11-11
Bump:)

---

### Post by user-max on 2008-11-12
Bump: there has to be someone who had this problem

---

### Post by Liviu-Theodor on 2008-11-12
At [http://openprinting.org/]("http://openprinting.org/") somebody said this printer is not in their database (yet), but reccomends using instead one of the drivers for bjc8200, bj800 or bj7000. Just give them a try.

---

### Post by user-max on 2008-11-12
> **Liviu-Theodor said:**
> At [http://openprinting.org/]("http://openprinting.org/") somebody said this printer is not in their database (yet), but reccomends using instead one of the drivers for bjc8200, bj800 or bj7000. Just give them a try.

Great! Thank you for reply, I will give those a try!

---

