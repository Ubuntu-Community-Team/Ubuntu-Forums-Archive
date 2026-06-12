---
title: "/usr/bin/dpkg returned an error code (1) kernel"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2010-12-01
```
Unpacking replacement linux-image-2.6.35-23-generic ...
dpkg-deb (subprocess): data: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.35-23-generic_2.6.35-23.41_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./boot/vmlinuz-2.6.35-23-generic'
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.35-23-generic_2.6.35-23.41_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/ramaswamy# 
```

both update software and synaptic gave the same error?
how do i install this package?

---

### Post by zvacet on 2010-12-03
```
sudo dpkg --configure -a
```

---

