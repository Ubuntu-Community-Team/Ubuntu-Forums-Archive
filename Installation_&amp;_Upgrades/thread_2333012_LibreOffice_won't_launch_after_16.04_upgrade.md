---
title: "LibreOffice won't launch after 16.04 upgrade"
date: 2016-08-06
forum: Installation &amp; Upgrades
---

### Post by Bill_McConnell on 2016-08-06
I upgraded my System76 laptop to Ubuntu 16.04, and following the upgrade, LibreOffice will not launch.  This affects each of the sub-programs (calc, writer, impress), and all modes of launching (from menu bar, double clicking a LibreOffice file).

I have tried uninstall and reinstall both from the applications icon and from ap-get without success.

The symptom is that I get a centered banner forLibreOffice5.  This is stationary for a moderate tme (many seconds, but less than a minute) and then begins flashing.  There is a text within the banner while flashing that says "resynchronizing ..."

I would welcome any suggestions

Bill McConnell

---

### Post by howefield on 2016-08-06
Try renaming the folder in ~/.config/libreoffice

Then try starting libreoffice, if all is well you can delete the renamed folder if no longer required.

---

### Post by Bill_McConnell on 2016-08-06
Thank you for the quick response.  That did the trick

---

### Post by howefield on 2016-08-07
Great, glad to hear it. Thanks for marking the thread solved.

---

