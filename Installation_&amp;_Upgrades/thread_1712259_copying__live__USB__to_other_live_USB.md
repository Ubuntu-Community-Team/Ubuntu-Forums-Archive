---
title: "copying  live  USB  to other live USB"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by arkangel on 2011-03-22
Hi 

I have a live USB  and I can boot from it.  I installed some stuff on it and I would like to make copies that are able to boot as well 

I use dd this way 

```

% dd if=/dev/sdd1 of=usb.iso  

```
to have a copy  on my HD 

```

% dd if=usb.iso of=/dev/sdd2  

```
/dev/sdd2  is the other usb 

Any help would be appreciated

---

