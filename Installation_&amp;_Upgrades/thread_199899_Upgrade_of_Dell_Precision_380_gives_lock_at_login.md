---
title: "Upgrade of Dell Precision 380 gives lock at login"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by The Mad Scientist on 2006-06-19
I just did an upgrade of my Dell Precision 380 workstation from 5.10 to 6.06.  This resulted in loss of mouse and keyboard at the boot screen, so I can't log in.    All I can do is cycle power.  The upgrade seemed to go OK.

When I installed 5.10, I had a similar problem (the keyboard went away during the installation, resulting in a lock), but I cannot remember how to solve it or find the web site I originally did.  The actual problem has something to do with the USB keyboard (which I am not using, since my KVM switch does not support it) and some sort of BIOS problem due to DELL.  I seem to remember the fix coming from an IBM website.

Anyone have any ideas?

---

### Post by cacharreo on 2006-06-19
Try to reconfigure the xserver selecting the mouse and keyboard propperly:
Start in terminal mode and run:
***sudo dpkg-reconfigure xserver-xorg***

---

### Post by The Mad Scientist on 2006-06-20
It was a BIOS issue.  I upgraded the BIOS from A02 to A07 and it solved the problem.

---

### Post by joesapo on 2007-05-21
> **The Mad Scientist said:**
> It was a BIOS issue.  I upgraded the BIOS from A02 to A07 and it solved the problem.

FYI:  Upgrading the BIOS on my P380 as stated fixed this issue, as well as the KVM problems I was having with the system.

---

