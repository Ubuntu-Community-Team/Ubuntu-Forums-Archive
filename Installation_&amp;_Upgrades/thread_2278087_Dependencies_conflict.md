---
title: "Dependencies conflict"
date: 2015-05-13
forum: Installation &amp; Upgrades
---

### Post by zhenia on 2015-05-13
After a system update I keep getting message errors like
```
***
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb (--unpack): 
 trying to overwrite '/lib/modules/3.13.0-32-generic/kernel/net/packet/af_packet_diag.ko', which is also in package linux-image-extra-3.13.0-32-generic 3.13.0-32.57 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb 
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-32-generic: 
 linux-image-extra-3.13.0-32-generic depends on linux-image-3.13.0-32-generic; however: 
  Package linux-image-3.13.0-32-generic is not installed. 
dpkg: error processing linux-image-extra-3.13.0-32-generic (--configure): 
 dependency problems - leaving unconfigured
***
```
I have tried to purge the cache and reinstall but the conflict does not let me neither repair nor install anything else.
Thanks for your help!

---

### Post by bcschmerker on 2015-05-13
Looks as though the Extra kernel has to be removed to unstick APT and permit linux-image-generic-lts-trusty and linux-image-3.13.0-32-generic to install.  What luck with sudo apt-get remove --purge linux-image-extra-3.13.0-32-generic?

---

### Post by matt_symes on 2015-05-13
Hi

> linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb

Where is this deb being pulled in from ? It doesn't look right to me.

Can we check you sources please.

Please post the output of

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by zhenia on 2015-05-14
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:4:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:5:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:9:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:10:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:15:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:16:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:17:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:18:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:25:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:26:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:27:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:28:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:35:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:36:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:40:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:41:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:52:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:53:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:54:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:55:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:56:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:57:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list.d/google-chrome.list:3:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:3:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/precise-dell.list:1:deb [http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/) precise-dell public
/etc/apt/sources.list.d/precise-dell.list:2:deb-src [http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/) precise-dell public
/etc/apt/sources.list.d/precise-dell.list.distUpgrade:1:deb [http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/) precise-dell public
/etc/apt/sources.list.d/precise-dell.list.distUpgrade:2:deb-src [http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/) precise-dell public

---

### Post by zhenia on 2015-05-14
thanks this seems to have worked! thanks a million!

---

