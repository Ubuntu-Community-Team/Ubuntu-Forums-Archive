---
title: "Firefox 10 error Ubuntu 11.10"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by kimbledesign on 2012-03-10
After a fresh install of Ubuntu 11.10 I get the following error when I try to open Firefox:

could not initialize the application's security component.  The most likely cause is problems with files in your application's profile directory.  Please check that this directory has no read/write restrictions and your hard drive is not full or close to full.  It is recommended that you exit the application and fix the problem.  If you continue to use this session, you might see incorrect application behavior when accessing security features.

I looked at the permissions of /usr/var/firefox-10.0.2 and /usr/var/firefox addons and they were both set as  root:root so I changed the owner to my login name and made sure they both had read/write permissions but I still get the same error when opening firefox.  I have plenty of hard drive space so I am not sure what the problem is.

Anyone have any ideas?

---

### Post by larry_the_canary on 2012-03-16
I am getting this same problem after applying recent updates. 

Cisco Anyconnect VPN which relies on Firefox for certificate storage has also stopped working.

---

### Post by larry_the_canary on 2012-03-16
I managed to fix the error by deleting the file ~/.mozilla/firefox/<random-string>.default/cert8.db

I guess it somehow became corrupted.

---

### Post by kimbledesign on 2012-03-20
I found another post in this forum that has a command line fix that involves running a firefox profile manager.  I will try and find this again and post it

---

