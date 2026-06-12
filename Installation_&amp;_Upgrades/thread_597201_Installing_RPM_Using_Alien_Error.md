---
title: "Installing RPM Using Alien Error"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-10-30
I downloaded a Red Hat rpm file as a portion of an installation routine.  I converted the rpm file to a deb file using alien.  I then issued the dpkg command and recieved the following error message.

```

~/communication/download/epson/Scanners/epson_imagescan$ [COLOR=DarkGreen]**sudo dpkg -i iscan_2.8.0-2_i386.deb**[/COLOR]


(Reading database ... 162785 files and directories currently installed.)
Unpacking iscan (from iscan_2.8.0-2_i386.deb) ...
dpkg: error processing iscan_2.8.0-2_i386.deb (--install):
 trying to overwrite `/usr/lib/sane/libsane-epkowa.la', which is also in package libsane-extras
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 iscan_2.8.0-2_i386.deb

```However it appeared a portion of the install did complete since I can execute the software that I was expecting to install.

**[COLOR=Blue]QUESTION[/COLOR]**:

I am not sure that the software was installed properly and I may be missing something.  Does anybody know what this error means and how to fix it?

Thanks in advance.

---

