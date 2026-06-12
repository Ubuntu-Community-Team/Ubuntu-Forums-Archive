---
title: "dpkg error----Ubuntu installed on external Hard disk"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by khalid.chaudhry on 2011-11-27
Hi All,

I have installed ubuntu 11.04 on my external hard disk(500gb).Afterwards i installed Xen on it.When command( make && make modules_install && make install)finishes execution it gives me the following display

Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
dpkg: error: version 'syms-4.1.1' has bad syntax: version number does not start with digit
dpkg: error: version '/boot/xen.gz' has bad syntax: version number does not start with digit
Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
dpkg: error: version 'syms-4.1.1' has bad syntax: version number does not start with digit
dpkg: error: version '/boot/xen.gz' has bad syntax: version number does not start with digit
Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
dpkg: error: version '/boot/xen.gz' has bad syntax: version number does not start with digit
Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
Found memtest86+ image: /memtest86+.bin
done
root@khalid-Inspiron-1525:/usr/src/linux-source-3.0.0#

I don't know from where these(dpkg) errors are coming from and how to fix it......:confused:

Regards,
Khalid

---

