---
title: "Ubuntu base update fail: error processing archive linux-image-4.4.0-36-generic..."
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by nullsteph on 2016-08-30
Just did a clean install of 16.4, and noticed the updates are failing.  

**sudo apt-get install -f**
```

dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-36-generic_4.4.0-36.55_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-36-generic' to '/boot/vmlinuz-4.4.0-36-generic.dpkg-new': unexpected end of file or stream
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-36-generic_4.4.0-36.55_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**sudo dpkg --configure -a**
```

dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-36-generic:
 linux-image-extra-4.4.0-36-generic depends on linux-image-4.4.0-36-generic; however:
  Package linux-image-4.4.0-36-generic is not installed.

dpkg: error processing package linux-image-extra-4.4.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-36-generic; however:
  Package linux-image-4.4.0-36-generic is not installed.
 linux-image-generic depends on linux-image-extra-4.4.0-36-generic; however:
  Package linux-image-extra-4.4.0-36-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-4.4.0-36-generic:
 linux-signed-image-4.4.0-36-generic depends on linux-image-4.4.0-36-generic (= 4.4.0-36.55); however:
  Package linux-image-4.4.0-36-generic is not installed.

dpkg: error processing package linux-signed-image-4.4.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic:
 linux-signed-image-generic depends on linux-signed-image-4.4.0-36-generic; however:
  Package linux-signed-image-4.4.0-36-generic is not configured yet.
 linux-signed-image-generic depends on linux-image-extra-4.4.0-36-generic; however:
  Package linux-image-extra-4.4.0-36-generic is not configured yet.

dpkg: error processing package linux-signed-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.36.38); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-signed-image-generic (= 4.4.0.36.38); however:
  Package linux-signed-image-generic is not configured yet.

dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-extra-4.4.0-36-generic
 linux-image-generic
 linux-signed-image-4.4.0-36-generic
 linux-signed-image-generic
 linux-generic
 linux-signed-generic
```

---

### Post by ian-weisser on 2016-08-30
> **nullsteph said:**
> [COLOR=#000000]*dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-36-generic_4.4.0-36.55_amd64.deb (--unpack):*[/COLOR]
[COLOR=#000000]*cannot copy extracted data for './boot/vmlinuz-4.4.0-36-generic' to '/boot/vmlinuz-4.4.0-36-generic.dpkg-new': unexpected end of file or stream*[/COLOR]

Please show us the complete output of the following command:
```
df
```

---

