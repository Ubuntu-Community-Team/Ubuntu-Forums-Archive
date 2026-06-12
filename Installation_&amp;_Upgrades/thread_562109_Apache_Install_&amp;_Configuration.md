---
title: "Apache Install &amp; Configuration"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by jar349 on 2007-09-28
I have some experience with Apache on both Windows and Linux, but have never used Ubuntu before.

I have an Apache server installed on my Ubuntu server and I can view the site from any computer on my network, but I cannot view it from anywhere external to my router.

I have double-checked the router to ensure that port 80 requests get forwarded to my Ubuntu server.  I have looked through the Apache configuration and have found nothing out of the ordinary (it's listening for all incoming requests on 0.0.0.0).

I can therefore only believe that it is ubuntu's software firewall that is allowing intranet requests, but not internet requests.  How can I check to see if this is (or is not) the case?

Thanks!
John

---

### Post by Pumalite on 2007-09-28
Disable firewall.

---

