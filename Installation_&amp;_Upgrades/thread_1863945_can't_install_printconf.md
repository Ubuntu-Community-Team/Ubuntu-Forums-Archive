---
title: "can't install printconf"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by rtalcott on 2011-10-18
When I try to install **printconf** using synaptic I get the following:

**Depends on foomatic-db-gutenprint but it is not going to be installed**

Anyone have any ideas on how to get around this....printconf has installed on all previous versions.

rt

---

### Post by crazy bird on 2011-10-18
> **rtalcott said:**
> When I try to install **printconf** using synaptic I get the following:
 
**Depends on foomatic-db-gutenprint but it is not going to be installed**
 
Anyone have any ideas on how to get around this....printconf has installed on all previous versions.
 
rt
 
Try installing that package first: [http://packages.ubuntu.com/search?keywords=foomatic-db-gutenprint](http://packages.ubuntu.com/search?keywords=foomatic-db-gutenprint). That migth solve your problem.

---

### Post by rtalcott on 2011-10-18
no cigar....the error now is:

[B]foomatic-db-gutenprint
Depends:foomatic-db (>=20000101)[/B]

What I am actually trying to do is configure a usb printer...more exactly I have a usb-parallel port cable connected to an HP 6L...and this has worked fine till now but I always installed printconf and CUPS then found it and all was happy...those daze are gone...however I did notice an open bug for configuration of usb printers in 11.04 so maybe it's all related.
rt

---

### Post by rtalcott on 2011-10-18
Brute force almost always works...I installed foomatic-db...of course that removed a few things BUT that did allow me to install printconf and now with a bit of luck I can print...will mark this solved if that is the case.

**printconf installs so this thread is solved BUT I still cannot get the printer recognized.**
rt

---

