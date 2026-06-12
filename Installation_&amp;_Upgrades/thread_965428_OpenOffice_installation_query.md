---
title: "OpenOffice installation query"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by paulb42 on 2008-10-31
Hello

I downloaded and installed OpenOffice.org 3.0 last night, following instructions from the excellent howtoforge.com, and noticed a couple of messages about no valid Java run time being installed. I can go and get JRE and install it but do I need to reinstall OOo 3 again ? 

Also is it safe to deinstall 2.4 so I can install the desktop integration ? I read somewhere thet deinstall removes some other required package but can't remember where I read it now ..

Thanks
Paul
Christchurch UK

---

### Post by Hagar Delest on 2008-10-31
No, you don't need to reinstall OOo after JRE install. Just go to Tools>Options>OOo>Java, wait a while so that OOo scans the system and check the latest version of JRE.

You can keep OOo 2.4 and install the integration package. Files will be associated to 3.0 but you'll keep the 2.4. I run both on my xubuntu box (with both 2.4.1 and 3.0).

---

### Post by markharding557 on 2008-10-31
you can install open office3 from > deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
just put these in your sources list

---

