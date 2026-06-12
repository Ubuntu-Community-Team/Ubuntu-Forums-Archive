---
title: "[SOLVED] Ubuntu server md5 mismatchs...sort of"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by plr4ever on 2008-11-23
I just downloaded an ISO of the ubuntu server 8.10 i386 cd, and the md5's matched. I then burned it to a cd, and popped it into the server, and ran a cd check. However, i get an md5 mismatch on

 "./pool/main/libn/libnet-ip-perl/libnet-ip-perl_1.25-2_all.deb"

So i popped the cd back into my desktop, and ran 
```
md5sum -c md5sum.txt 
```
from the root cd directory. I found the check for the libnet-ip-perl_1.25-2_all.deb package, and it said "OK." 

I'm running memtest now, but other than the memory, what can cause a mismatch on one computer, but the other one checks out? The disc is a dvd-rw, but that shouldnt affect it, as i also tried this out on a cd-rw.

EDIT: The memtest finished and there were no errors.

---

### Post by Rucas on 2008-11-23
I have posted a similar thread to yours.
And i also suspect or for better way of saying, that the ISO file for the 32 bit version is indeed damaged or a 64bit by error. My machine went really crazy when trying to install Ubuntu 8.10 version. I burnt and downloaded quite a few times the iso file, coz i thought also that the CD could have burnt wrong/etc...
Nothing like that at all.

---

### Post by plr4ever on 2008-11-23
> **Rucas said:**
> I have posted a similar thread to yours.
And i also suspect or for better way of saying, that the ISO file for the 32 bit version is indeed damaged or a 64bit by error. My machine went really crazy when trying to install Ubuntu 8.10 version. I burnt and downloaded quite a few times the iso file, coz i thought also that the CD could have burnt wrong/etc...
Nothing like that at all.

I didnt download the wrong ISO, as the md5sum on my desktop and on the server checked out.

---

### Post by plr4ever on 2008-11-24
Well never mind, i just went off of the base install and got ubuntu-desktop installed, and i am going from there.

---

