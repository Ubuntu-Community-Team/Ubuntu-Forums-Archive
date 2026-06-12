---
title: "dpkg error"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by khalid.chaudhry on 2011-11-25
Hi All,

I have installed ubuntu 11.04 on my external hard disk(500gb).Afterwards i installed Xen on it.When command( make  && make modules_install && make install)finishes execution it gives me the following display

Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
**dpkg: error: version 'syms-4.1.1' has bad syntax: version number does not start with digit**
**dpkg: error: version '/boot/xen.gz' has bad syntax: version number does not start with digit**
Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
**dpkg: error: version 'syms-4.1.1' has bad syntax: version number does not start with digit**
**dpkg: error: version '/boot/xen.gz' has bad syntax: version number does not start with digit**
Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
**dpkg: error: version '/boot/xen.gz' has bad syntax: version number does not start with digit**
Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
Found linux image: /boot/vmlinuz-3.0.4
Found initrd image: /boot/initrd.img-3.0.4
Found memtest86+ image: /memtest86+.bin
done
root@khalid-Inspiron-1525:/usr/src/linux-source-3.0.0#

I don't know from where these(dpkg) errors are coming from and how to fix it.I am beginner in Ubuntu and Xen so  sorry if its too basic.

Regards,
Khalid

---

### Post by dino99 on 2011-11-26
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by khalid.chaudhry on 2011-11-26
Hi ,
I follow the same guide .I don't why i am receiving dpkg error .Any help would be highly appreciated

Regards,
Khalid

---

