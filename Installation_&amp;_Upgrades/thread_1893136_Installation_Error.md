---
title: "Installation Error"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2011-12-09
I have been getting the same error when I download a package (as a DEB file) and then try and install it. It has happened on Picasa, Google earth and now Skype - can anyone tell me what the error means and what I can do to resolve it?

```
(Reading database ... 183328 files and directories currently installed.)
Unpacking skype (from .../skype-ubuntu_2.2.0.35-1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /tmp/skype-ubuntu_2.2.0.35-1_i386.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 /tmp/skype-ubuntu_2.2.0.35-1_i386.deb

```



Thanks...!

---

### Post by dabl on 2011-12-09
> **bigtel said:**
> 

[CODE]
.
.
.
internal gzip read error: '<fd:0>: data error'
.
[/CODE



Is there a floppy diskette involved in this process?

---

### Post by bigtel on 2011-12-10
There is a floppy drive on the PC but, no, I am not using it for any installations. I am downloading the deb files to the hard drive and then trying to install from there.

---

### Post by dabl on 2011-12-10
As best I can learn from google, that error is the result of an incomplete or corrupted download.  If the skype package source offers an md5sum, then check that against the downloaded package -- probably it won't match.

As an alternative to "click via browser", you might want to give wget a try, via terminal command line.  For example, the skype 32-bit Ubuntu package would be 

```
wget http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/downloading.ubuntu32
```

---

