---
title: "Dovecot over top of unused Postfix?"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by aplonis on 2009-12-31
I am wanting to set up full mail service 
on my brand new Karmic Koala just recently
installed on a box that had used to run
NetBSD 2.0.2.

I want to send and receive mail from the
local net of 192.168.0.0/24 where Ubuntu
runs and also one static IP from a Netgear
router on SDSL 65 miles away.

I had gotten started with this how-to...

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

...and it went as described. 

Bu now, with no mail clients having yet 
to employ Postfix, I am having second 
thoughts, thinking I might better have 
gone with this one...

[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

...because it is fully supported by Ubuntu.

The latter mentions choosing mbox instead
of maildir if I had already installed the
Postfix from the prior how-to.

This seems to indicate it is okay to install
Dovecot over the top of Postfix. But I'm a
little timid to just go ahead do that...put
in Dovecot leaving Postfix in place. Is that
really okay, or not?

---

