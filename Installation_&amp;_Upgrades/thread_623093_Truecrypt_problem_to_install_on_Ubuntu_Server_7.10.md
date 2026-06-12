---
title: "Truecrypt problem to install on Ubuntu Server 7.10"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Gladk on 2007-11-25
I have succesfully installed truecrypt on Kubuntu 7.10 and it WORKS!

But  when I installed it on Ubuntu Server 7.10 i have got a problem. It writes:
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.22.ko': -1 Invalid module format
FATAL:module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module 

Can anybody help me with it? 

Thank you.

---

### Post by StevenHarper on 2007-11-25
I presume you used the DEB off TrueCrypts site?

I can tell you that the deb there works fine on Ubuntu 7.10 32bit Desktop, so the problem is likely to be bacause of a difference between Server and Desktop editions.

---

### Post by Gladk on 2007-11-27
Solved, I installed it from source, although it took pretty much time.

---

### Post by trmentry on 2007-12-01
I have 64bit Ubuntu Desktop installed and just installed the deb for Truecrypt, but I can't get it working.

I'm assuming I have to insert the module before modprobe it.  But I get this error.

/usr/share/truecrypt/kernel# insmod truecrypt-2.6.22.ko
insmod: error inserting 'truecrypt-2.6.22.ko': -1 Unknown symbol in module


I'm not exactly sure how to proceed at this point.   I see there is a tcrypt module but it won't load.

# modprobe tcrypt
FATAL: Error inserting tcrypt (/lib/modules/2.6.22-14-generic/kernel/crypto/tcrypt.ko): Resource temporarily unavailable


This is pretty much a new install of Ubuntu 64bit 7.10.

Thanks

---

