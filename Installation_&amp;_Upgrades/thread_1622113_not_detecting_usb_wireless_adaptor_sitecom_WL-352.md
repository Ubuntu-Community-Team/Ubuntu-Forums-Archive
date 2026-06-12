---
title: "not detecting usb wireless adaptor sitecom WL-352"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by agrlux on 2010-11-15
The only connection to internet I have is via usb adaptor sitecom WL-352, under windows XP. Now I installed Ubuntu 10.10, and I cannot connect to internet via wireless. How can I do to use this adaptor?

---

### Post by cybergnome on 2010-11-15
You can try using ndiswrapper with the Windows driver, if you can't find a linux driver for the chipset included in your USB device.  Generally, development for USB wireless devices is behind that of PCI and cardbus.

---

### Post by agrlux on 2010-11-16
I am starting to use Ubuntu, how will I proceed with the ndiswrapper? Thank you

---

### Post by cybergnome on 2010-11-16
See the link: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Sitecom_WL-352](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Sitecom_WL-352).  You will probably have to be walked through this.

---

### Post by agrlux on 2010-11-18
Can I have Step-to-step of what to do? I downloaded the files but then I don't know what to do

---

