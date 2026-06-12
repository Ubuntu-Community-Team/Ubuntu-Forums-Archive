---
title: "trying to generate a windows executable for wireshark using mingw"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by anoopchalil on 2011-06-29
Hi,

I am pretty new in working with cross compilers. I want to create a windows executable for wireshark from ubuntu. With some online research I figured out that it can be done using mingw but I am unable to do so.

I first installed mingw from the synaptic package manager and then went to the wireshark source directory and tried running the below command:

./configure --prefix=/usr/i586-mingw32 --host=i586-mingw32msvc --build=x86_64-linux

This gives me two different errors:
1) configure: error: funtion socket not found
2) configure: error: Header file pcap.h not found; if you installed libpcap
from source, did you also do "make install-incl", and if you installed a
binary package of libpcap, is there also a developer's package of libpcap,
and did you also install that package?

Any inputs to resolve this would be appreciated.

Thanks
Anoop

---

