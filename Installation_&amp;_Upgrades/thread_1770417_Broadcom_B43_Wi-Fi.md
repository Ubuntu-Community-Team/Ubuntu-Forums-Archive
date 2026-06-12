---
title: "Broadcom B43 Wi-Fi"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by Nolind on 2011-05-29
I've just upgraded to Natty but during the installation the wi-fi card has failed to install properly. It worked ok with the Meerkat , Lynx and Koala.  

Under additional drivers the STA broadcom driver is installed and activated but the wi-fi light on my laptop. ( HP Pavillion dv6000) stays red (it should turn blue). There are no wireless networks detected. I tried removing and reinstalling the driver in Aditional drivers and restarted but no joy. Help please.


Thanks


Colin

---

### Post by mörgæs on 2011-05-29
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by Nolind on 2011-05-29
Thanks I sorted the problem by using the package manager to reinstall the bcmwl package (solution 2 in the link) and removing the STA driver in additional drivers. Natty doesn't seem to want the STA driver.


Thanks.

---

