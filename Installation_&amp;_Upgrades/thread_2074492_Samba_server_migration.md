---
title: "Samba server migration"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by groupthinker on 2012-10-21
Hello all! I have rebuild a Samba 3.6.3 server running Ubuntu 12.04. Before I do this I need to know how to import/export samba users and passwords. I've searched Google and found a few helpful guides, but nothing I've been able to successfully follow in my sandbox.
[http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/)

from /etc/samba/smb.conf
        security = user
        map to guest = bad user
        dns proxy = no
        username map = /etc/samba/smbusers

I think maybe I don't fundamentally understand how authentication is working on this server. Does Samba have its own set of authentication or is it using Ubuntu's authentication?
I'm starting to think I should setup and openLDAP database and authenticate against that? This is only for 10 people on Windows machines.
Thank you all for your time.

---

