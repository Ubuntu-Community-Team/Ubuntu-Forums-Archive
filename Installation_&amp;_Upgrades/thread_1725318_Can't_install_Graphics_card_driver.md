---
title: "Can't install Graphics card driver"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by BigSears on 2011-04-09
I'm trying to install a driver for a Radeon x700. I downloaded the driver from the site and the sh command to install it but this is what I got.

```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-28-generic; make sure that the version is being
correctly set by --iscurrentdistro

```

Any ideas?

---

### Post by MAFoElffen on 2011-04-09
> **BigSears said:**
> I'm trying to install a driver for a Radeon x700. I downloaded the driver from the site and the sh command to install it but this is what I got.

```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-28-generic; make sure that the version is being
correctly set by --iscurrentdistro

```Any ideas?
Please, need more info on what release of Ubuntu you are trying to install on, on what architecture (32bit or 64bit).  Also, which driver downloaded from where- for what type of linux?   And what model of ATI Radeon X700 is it? (many versions of that card).

If you aren't sure which card or chipset it is, please use 
```
sudo hwinfo --framebuffer
```or```
sudo lspci -vvv
``` and copy the results here.

NOTE: If you used the old "  ati-driver-installer-9-3-x86.x86_64.run " file from ATi... It is an old outdated file that ATI dropped support for and has not been supported for years... the opensource driver does support this card/chipset as of Ubuntu 8.10 and newer...  This same shell error came up in this other post last year: > **alket said:**
> I just downloaded ATI Radeon x700 driver from ... but I get this error

---

### Post by BigSears on 2011-04-10
Nevermind, did more research and found out why it isn't working.

---

