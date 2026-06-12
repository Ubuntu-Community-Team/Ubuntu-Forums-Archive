---
title: "Firefox 1.0 installation"
date: 2005-01-01
forum: Installation &amp; Upgrades
---

### Post by Humboldt on 2005-01-01
When trying to upgrade to firefox 1.0 I followed the instruction in
<http://www.ubuntulinux.org/wiki/UpgradingToFirefox10/view?searchterm=firefox%201.0>
However, when trying to uninstall the deafult firefox installation - I tried to use synaptic - I got a massage that I also had to uninstall the unbuntu-desktop. That do not sound as a good idea. How can I uninstall the existing default firefox installation?

Thanks for any help

---

### Post by cllow on 2005-01-01
Hi,  to uninstall the current version of firefox, just go to /etc/apt directory. Enter:

sudo apt-get remove mozilla-firefox

<Enter>

---

### Post by Adrenal on 2005-01-02
Hmm, i followed that method, and i now i can't install any extensions. I go to the site, click install now like normal, then nothing happens. Any ideas? Anyone? Please?

---

### Post by wallijonn on 2005-01-02
View -> Hidden files.

navigate to .mozilla -> firefox -> default.xxx -> 

cut the extension folder, go up e levels (back to your home directory), paste. 

Startup Firefox and see if you can now add extensions.

---

### Post by Adrenal on 2005-01-05
[QUOTE=wallijonn]View -> Hidden files.

navigate to .mozilla -> firefox -> default.xxx -> 

cut the extension folder, go up e levels (back to your home directory), paste. 

Startup Firefox and see if you can now add extensions.[/QUOTE]
 Nope, still same problem, but thanks anyway

---

### Post by wallijonn on 2005-01-06
I forgot to tell you that whenever you remove anything from the hidden firefox folder you should logout and log back in otherwise FF doesn't start.

---

