---
title: "Can I copy 9.10 upgrade files from one PC to another?"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by urepedese on 2010-02-19
I now have two apparently successful installs with unbuntu:) It will be an adventure this week learning how to drive it all.:D

I have updated one to 9.10 from 9.04 and I am just wondering if I can copy the upgrade files to a USB stick and transfer them across. It will save me about 45 mins and significant Mb if I can do this.

---

### Post by solar george on 2010-02-20
try copying the contents of
/var/cache/apt/archives
from the 9.10 machine onto the 9.04.

In future try downloading a CD for the new version and updating from that.

---

### Post by urepedese on 2010-02-20
Hey thanks for that.

I wasn't sure how to go about pasting the files in as I am brand new to ubuntu, but I found this guide that helped.

[http://ubuntuforums.org/showthread.php?t=1335365&highlight=install+updates](http://ubuntuforums.org/showthread.php?t=1335365&highlight=install+updates) 

Only thing is I got this message at the end.
Errors were encountered while processing:
 libc6-i686_2.9-4ubuntu6.1_i386.deb
 libdns45_1%3a9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
 openoffice.org-core_1%3a3.0.1-9ubuntu3.1_i386.deb
 openoffice.org-base-core
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-gnome
 openoffice.org-gtk
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-writer
 python-uno
 openoffice.org-emailmerge

But it does look like the update manager is going to take care of it.

---

