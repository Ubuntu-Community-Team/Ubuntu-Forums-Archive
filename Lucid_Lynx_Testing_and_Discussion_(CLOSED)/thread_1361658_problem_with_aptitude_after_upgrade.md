---
title: "problem with aptitude after upgrade"
date: 2009-12-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-12-22
I just did an upgrade, apt-utils ... and now I get:```
~$ sudo aptitude safe-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages have been kept back:
  empathy evolution evolution-common evolution-indicator evolution-plugins 
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
*** stack smashing detected ***: aptitude terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7fb7e7bd4e67]
/lib/libc.so.6(__fortify_fail+0x0)[0x7fb7e7bd4e30]
aptitude[0x4e858a]
aptitude[0x4e8df0]
aptitude[0x5019fe]
aptitude[0x41b1f6]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7fb7e7afbadd]
aptitude[0x4195e9]
======= Memory map: ========
00400000-00625000 r-xp 00000000 08:02 1473                               /usr/bin/aptitude
00824000-00825000 r--p 00224000 08:02 1473                               /usr/bin/aptitude
00825000-00827000 rw-p 00225000 08:02 1473                               /usr/bin/aptitude
00827000-0082b000 rw-p 00000000 00:00 0 
00ec1000-015e1000 rw-p 00000000 00:00 0                                  [heap]
7fb7e4c01000-7fb7e4c02000 ---p 00000000 00:00 0 
7fb7e4c02000-7fb7e5402000 rw-p 00000000 00:00 0 
7fb7e5402000-7fb7e540e000 r-xp 00000000 08:02 3798                       /lib/libnss_files-2.10.2.so
7fb7e540e000-7fb7e560d000 ---p 0000c000 08:02 3798                       /lib/libnss_files-2.10.2.so
7fb7e560d000-7fb7e560e000 r--p 0000b000 08:02 3798                       /lib/libnss_files-2.10.2.so
7fb7e560e000-7fb7e560f000 rw-p 0000c000 08:02 3798                       /lib/libnss_files-2.10.2.so
7fb7e560f000-7fb7e5619000 r-xp 00000000 08:02 4960                       /lib/libnss_nis-2.10.2.so
7fb7e5619000-7fb7e5818000 ---p 0000a000 08:02 4960                       /lib/libnss_nis-2.10.2.so
7fb7e5818000-7fb7e5819000 r--p 00009000 08:02 4960                       /lib/libnss_nis-2.10.2.so
7fb7e5819000-7fb7e581a000 rw-p 0000a000 08:02 4960                       /lib/libnss_nis-2.10.2.so
7fb7e581a000-7fb7e5830000 r-xp 00000000 08:02 3794                       /lib/libnsl-2.10.2.so
7fb7e5830000-7fb7e5a30000 ---p 00016000 08:02 3794                       /lib/libnsl-2.10.2.so
7fb7e5a30000-7fb7e5a31000 r--p 00016000 08:02 3794                       /lib/libnsl-2.10.2.so
7fb7e5a31000-7fb7e5a32000 rw-p 00017000 08:02 3794                       /lib/libnsl-2.10.2.so
7fb7e5a32000-7fb7e5a34000 rw-p 00000000 00:00 0 
7fb7e5a34000-7fb7e5a3b000 r-xp 00000000 08:02 3795                       /lib/libnss_compat-2.10.2.so
7fb7e5a3b000-7fb7e5c3b000 ---p 00007000 08:02 3795                       /lib/libnss_compat-2.10.2.so
7fb7e5c3b000-7fb7e5c3c000 r--p 00007000 08:02 3795                       /lib/libnss_compat-2.10.2.so
7fb7e5c3c000-7fb7e5c3d000 rw-p 00008000 08:02 3795                       /lib/libnss_compat-2.10.2.so
7fb7e5c3d000-7fb7e5e01000 rw-p 00000000 00:00 0 
7fb7e5e10000-7fb7e69d1000 rw-p 00000000 00:00 0 
7fb7e69d1000-7fb7e76d6000 rw-p 00000000 08:02 131122                     /var/cache/apt/pkgcache.bin
7fb7e76d6000-7fb7e76d8000 r-xp 00000000 08:02 3785                       /lib/libdl-2.10.2.so
7fb7e76d8000-7fb7e78d8000 ---p 00002000 08:02 3785                       /lib/libdl-2.10.2.so
7fb7e78d8000-7fb7e78d9000 r--p 00002000 08:02 3785                       /lib/libdl-2.10.2.so
7fb7e78d9000-7fb7e78da000 rw-p 00003000 08:02 3785                       /lib/libdl-2.10.2.so
7fb7e78da000-7fb7e78dc000 r-xp 00000000 08:02 4979                       /lib/libutil-2.10.2.so
7fb7e78dc000-7fb7e7adb000 ---p 00002000 08:02 4979                       /lib/libutil-2.10.2.so
7fb7e7adb000-7fb7e7adc000 r--p 00001000 08:02 4979                       /lib/libutil-2.10.2.so
7fb7e7adc000-7fb7e7add000 rw-p 00002000 08:02 4979                       /lib/libutil-2.10.2.so
7fb7e7add000-7fb7e7c43000 r-xp 00000000 08:02 3397                       /lib/libc-2.10.2.so
7fb7e7c43000-7fb7e7e43000 ---p 00166000 08:02 3397                       /lib/libc-2.10.2.so
7fb7e7e43000-7fb7e7e47000 r--p 00166000 08:02 3397                       /lib/libc-2.10.2.so
7fb7e7e47000-7fb7e7e48000 rw-p 0016a000 08:02 3397                       /lib/libc-2.10.2.so
7fb7e7e48000-7fb7e7e4d000 rw-p 00000000 00:00 0 
7fb7e7e4d000-7fb7e7e63000 r-xp 00000000 08:02 1129                       /lib/libgcc_s.so.1
7fb7e7e63000-7fb7e8062000 ---p 00016000 08:02 1129                       /lib/libgcc_s.so.1
7fb7e8062000-7fb7e8063000 r--p 00015000 08:02 1129                       /lib/libgcc_s.so.1
7fb7e8063000-7fb7e8064000 rw-p 00016000 08:02 1129                       /lib/libgcc_s.so.1
7fb7e8064000-7fb7e80e6000 r-xp 00000000 08:02 3791                       /lib/libm-2.10.2.so
7fb7e80e6000-7fb7e82e6000 ---p 00082000 08:02 3791                       /lib/libm-2.10.2.so
7fb7e82e6000-7fb7e82e7000 r--p 00082000 08:02 3791                       /lib/libm-2.10.2.so
7fb7e82e7000-7fb7e82e8000 rw-p 00083000 08:02 3791                       /lib/libm-2.10.2.so
7fb7e82e8000-7fb7e83da000 r-xp 00000000 08:02 1125                       /usr/lib/libstdc++.so.6.0.13
7fb7e83da000-7fb7e85da000 ---p 000f2000 08:02 1125                       /usr/lib/libstdc++.so.6.0.13
7fb7e85da000-7fb7e85e1000 r--p 000f2000 08:02 1125                       /usr/lib/libstdc++.so.6.0.13
7fb7e85e1000-7fb7e85e3000 rw-p 000f9000 08:02 1125                       /usr/lib/libstdc++.so.6.0.13
7fb7e85e3000-7fb7e85f8000 rw-p 00000000 00:00 0 
7fb7e85f8000-7fb7e860f000 r-xp 00000000 08:02 4973                       /lib/libpthread-2.10.2.so
7fb7e860f000-7fb7e880e000 ---p 00017000 08:02 4973                       /lib/libpthread-2.10.2.so
7fb7e880e000-7fb7e880f000 r--p 00016000 08:02 4973                       /lib/libpthread-2.10.2.so
7fb7e880f000-7fb7e8810000 rw-p 00017000 08:02 4973                       /lib/libpthread-2.10.2.so
7fb7e8810000-7fb7e8814000 rw-p 00000000 00:00 0 
7fb7e8814000-7fb7e882a000 r-xp 00000000 08:02 803                        /lib/libz.so.1.2.3.3
7fb7e882a000-7fb7e8a29000 ---p 00016000 08:02 803                        /lib/libz.so.1.2.3.3
7fb7e8a29000-7fb7e8a2a000 r--p 00015000 08:02 803                        /lib/libz.so.1.2.3.3
7fb7e8a2a000-7fb7e8a2b000 rw-p 00016000 08:02 803                        /lib/libz.so.1.2.3.3
7fb7e8a2b000-7fb7e8b6e000 r-xp 00000000 08:02 78                         /usr/lib/libxapian.so.15.6.8
7fb7e8b6e000-7fb7e8d6d000 ---p 00143000 08:02 78                         /usr/lib/libxapian.so.15.6.8Aborted
:~$ 
```Apt-get doesn't produce any error.

---

### Post by philinux on 2009-12-22
Confirmed.

I dont use aptitude and like you say apt-get is not affected.

---

### Post by zika on 2009-12-22
> **philinux said:**
> Confirmed.

I dont use aptitude and like you say apt-get is not affected.Now that starts to pose a problem. In Update manager and Synaptic I can not upgrade because they want to remove some package (documentation) from evolution, aptitude is broken, only apt-get is left. It is a difficult task to recover when upgrade is, let's say, troublesome ...
BTW should I let evolution-documentation-en be removed ...? That would free Synaptic ...

---

### Post by philinux on 2009-12-22
> **zika said:**
> Now that starts to pose a problem. In Update manager and Synaptic I can not upgrade because they want to remove some package (documentation) from evolution, aptitude is broken, only apt-get is left. It is a difficult task to recover when upgrade is, let's say, troublesome ...
BTW should I let evolution-documentation-en be removed ...? That would free Synaptic ...

Yes that package is deprecated I think

---

### Post by jppr on 2009-12-22
i have updated system both synaptic and update-manager, it remove evolution but you can install it back, i do it that way. :)

---

### Post by Kevbert on 2009-12-22
Thanks for that. So do mean that
```
sudo aptitude safe-upgrade
```
isn't that safe ? I'll have to start using apt-get again.

---

### Post by philinux on 2009-12-22
> **Kevbert said:**
> Thanks for that. So do mean that
```
sudo aptitude safe-upgrade
```
isn't that safe ? I'll have to start using apt-get again.

No just aptitude is broken for now.

---

### Post by VMC on 2009-12-22
Its not broken for me. In fact I've been doing both just to see if any difference. There's none.

"sudo aptitude update && sudo aptitude safe-upgrade",
 then I say 'N' and do 
"sudo apt-get update && sudo apt-get upgrade",
 to see any differences.

I just did this 5 minutes ago?! Strange that it doesn't effect me.

---

### Post by gnomeuser on 2009-12-22
> **philinux said:**
> Confirmed.

I dont use aptitude and like you say apt-get is not affected.

sadly though tools such as ppa-purge use aptitude internally so those board the fail boat as well.

---

### Post by zika on 2009-12-22
From latest description of aptitude:
aptitude is also Y2K-compliant, non-fattening, naturally cleansing,
and house**broken**.
Sadly enough, from changelog, as far as I can see, the latest version is from Sep. 25th. (Karmic).

---

### Post by VMC on 2009-12-22
Ok, now mine broke too. Will report it if someone doesn't beat me to it.

---

### Post by zika on 2009-12-22
> **VMC said:**
> Ok, now mine broke too. Will report it if someone doesn't beat me to it.That is because aptitude itself is not broken. It is broken because it depends on something that changed in the meantime. It's, simply kind-of old ...

---

### Post by Kevbert on 2009-12-22
[[COLOR="Red"]Here's the bug report...[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/499543")

---

### Post by zika on 2009-12-22
> **Kevbert said:**
> [[COLOR="Red"]Here's the bug report...[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/499543")Thank You, I've signed it.

---

### Post by VMC on 2009-12-22
> **Kevbert said:**
> [[COLOR="Red"]Here's the bug report...[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/499543")

Thanks Kevbert. "Affects me also"...Signed sealed and delivered.

---

### Post by slakkie on 2009-12-22
Same bug here. Like Lucid doesn't like me. Haven't been able to do anything on that install for over a month now.

Fixed it. Downgrade apt to karmic's version and you can use aptitude again.

---

### Post by zika on 2009-12-23
New aptitude arrived and everything is OK. It was fast. I'll mark it.

---

### Post by VMC on 2009-12-23
> **zika said:**
> New aptitude arrived and everything is OK. It was fast. I'll mark it.

Your right. I don't know how I missed it. I was reading(at least I thought I was) all the updates, and I didn't see anything.

I wonder now, if after using apt-get will my aptitude database be messed up. I was told not to intermingle the two. 

```
vmc@vmc-desktop:~$ aptitude --version
aptitude 0.4.11.11 compiled at Dec 23 2009 07:55:36

```

---

