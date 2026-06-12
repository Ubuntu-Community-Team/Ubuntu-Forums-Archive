---
title: "Upgrde to breezy, problem with GDM."
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by chajuram on 2005-10-15
Hi,

I upgraded to breezy using apt-get dist-upgraded. When I rebooted the computer and GDM started I got the error message 
"The configuration file contains an invalid command line for the dialog. So running the default. Please fix your configuration."
And a default looking theme comes up. 

1. I tried doing dpkg-reconfigure kdm, just to see if it works and get the error
"Reloading K Display Manager configuration...kdm not running."

2. I tried changing themes but the changes do not take effect.

I hope someone can help.

Thanks,

Ritwik.

---

### Post by f-bomb on 2005-10-15
i had the same problem.  Seems like I told apt to keep my old config file rather than use the new one.  I copied /etc/gdm/gdm.conf.dpkg-dist to gdm.conf, restarted, and it works fine.

---

### Post by chajuram on 2005-10-15
Thanks a million. 

I realized I had to replace the gdm.conf, but did not know where to get it from, little did I know that it was right next to it all the time. :( 

Thanks.
Ritwik.

---

