---
title: "Upgrade OO 3.1 to LO 3.3"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2011-02-02
Hi,

Using Karmic, want to "upgrade" OpenOffice 3.1 to LibreOffice 3.3.

Should I uninstall OO 3.1 and install LO 3.3, or should I try to install over-top of existing OO 3.1?

Thanks,
CH

---

### Post by ajgreeny on 2011-02-02
I think you can run them side by side, according to something I read a month or two ago, but don't take that as gospel truth as I could be remembering wrongly.

How do you intend to install?  If you download the suite from [http://www.libreoffice.org/download/](http://www.libreoffice.org/download/) and unpack all the debs from the tarball into a new folder in your home, you can install with ```
sudo dpkg -i *.deb
``` run from that folder, and I think the suite is then installed into /opt, totally separate from Open Office.

However I have just seen there is at last a final release of 3.3 which is available from a ppa _[https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=](https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=)_ for lucid and maverick, but I've no idea about karmic

---

### Post by jonbonjovi on 2011-02-02
It you add the ppa of Libo and try to install it from there, Synaptic will force you to uninstall OOo. Which is what I did.

---

### Post by frogotronic on 2011-02-02
> **jonbonjovi said:**
> It you add the ppa of Libo and try to install it from there, Synaptic will force you to uninstall OOo. Which is what I did.

What's the PPA for Karmic?

- CH

---

### Post by jonbonjovi on 2011-02-02
Try this:
sudo add-apt-repository ppa:libreoffice/ppa

---

### Post by frogotronic on 2011-02-02
> **jonbonjovi said:**
> Try this:
sudo add-apt-repository ppa:libreoffice/ppa

nope, empty for LO

---

