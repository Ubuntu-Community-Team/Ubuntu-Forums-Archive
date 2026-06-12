---
title: "Error in Synaptic Package Manager -- Adobe"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by kklingerman on 2007-08-19
HI,

  I recently installed Adboe Reader and it semeed to install successfully.  It runs OK.  However, now everytime when I run Synaptic Package Manger or Update Manager, I receive the attached error message (subprocess post-installation script returned error exit status 1).  Is there any way to get rid of this error?  Thanks.

Kevin

---

### Post by taurus on 2007-08-19
Open a terminal and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kklingerman on 2007-08-19
> **taurus said:**
> Open a terminal and run

```
sudo apt-get update
sudo apt-get upgrade
```

Still didn't finish fully.  Here are the results:

Setting up adobereader-enu (7.0.9-2) ...
ln: creating symbolic link `/Reader/intellinux/lib/libldap.so' to `/usr/lib/libldap.so.2': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/liblber.so' to `/usr/lib/liblber.so.2': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libORBit-2.so' to `/usr/lib/libORBit-2.so.0': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libbonobo-2.so' to `/usr/lib/libbonobo-2.so.0': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libbonobo-activation.so' to `/usr/lib/libbonobo-activation.so.4': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libgnomespeech.so' to `/usr/lib/libgnomespeech.so.7': No such file or directory
dpkg: error processing adobereader-enu (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 adobereader-enu
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

