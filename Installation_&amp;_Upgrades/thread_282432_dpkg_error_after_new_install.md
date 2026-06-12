---
title: "dpkg error after new install"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by degsy on 2006-10-22
Can anyone help me please. Having just installed Ubuntu 6.06 lts on my old Toshiba Sat Pro 4200 I was excited to get it going and on the web only to be disappointed when I had an error carrying out updates via internet.

The problems start after clicking on the update icon when I get the Software updates windows start quickly followed by a message window stating "Only one software management tool is allowed to run at a time" etc. etc.

When I go to System-Synaptic Package Manager I get an error window stating "E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

Can anyone help???

---

### Post by meng on 2006-10-22
Try dropping to the command line and running:
sudo dpkg --configure -a

(you'll be asked for your user password)
One wonders if some installation/upgrade operation was interrupted previously, and consequently the lock wasn't removed.

---

### Post by meng on 2006-10-22
Evidently not the patient type.

---

