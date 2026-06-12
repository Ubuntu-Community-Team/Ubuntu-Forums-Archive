---
title: "Cannot adjust monitor resolution"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by grubdude on 2010-01-06
Hi,

Any idea why both ubuntu and centos 5.4 will only give me 800x600 resolution on my monitor when opensolaris immediately gives me 1280x1024?

The first time I tried ubuntu it gave me 1280x1024 and now will only make 800x600...This is a viewsonic VG930M Monitor......

Thanks...

---

### Post by kansasnoob on 2010-01-06
Please post the output from Terminal of:

```
lsb_release -a
```

And:

```
lspci | grep VGA
```

---

### Post by grubdude on 2010-01-06
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic


lspci | grep VGA
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter

Thanks, does that help?

P.S. this occurs whether running in virtual box or a straight install on hard drive or using live cd...The very first time that I installed ubuntu it worked fine....I am also running Windows 7 on this monitor with high resolution too....

---

### Post by grubdude on 2010-01-06
Anyone?

---

### Post by grubdude on 2010-01-06
By the way, ubuntu sees this as an unrecognized monitor....

---

