---
title: "File Serve from desktop?"
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by djw53079 on 2013-12-18
Any suggestions or pre-requisites for a secured, encrypted small business file server with managed user access for 5TB of medical-related records that's accessed by 20+ windows users throughout the day, with a desktop that could be managed remotely with incremental backups. Is there anything I need to be prepared for? Anything I should do? Any suggestions? Hardware: ASUS M5A99FX PRO with a FX-8350 Vishera 4.0GHz, 16Gigs and high performance raid array.

---

### Post by ian-weisser on 2013-12-18
Well, if you are supporting Windows clients, then you should look at Samba.
Lots of options for incremental backups. Easy. The default Ubuntu backup application, Deja Dup (duplicity), does incremental backups. 
Remote management via ssh or RDP is also well supported.


What's your experience level?
Have you used Ubuntu before?
Have you done a Samba file server before?
Have you done encrypted files before?
Have you done incremental backups before?
Have you done remote management before?

---

