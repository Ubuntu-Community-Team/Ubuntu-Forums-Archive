---
title: "Installing LTSP?"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by nic-clark on 2006-07-04
Hi,

We're looking into the idea of LTSP for a small cafe type thing at our school. I have used Ubuntu 5 before so have some limited knowledge, but that's about as far as it goes!

Is there a step by step guide to installing LTSP with the Ubuntu server anywhere that does not assume too much prior knowledge of Linux?

Is it possible to easily(ish) hook up our active directory server to provide the same user and login info to the thin client network also? Is there a guide for this?

Thanks,

Nic Clark

---

### Post by Jagot on 2006-07-04
There's the server starter guide here:

[https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

And another here:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

Don't know if they might be of help to you.

Never done anything with servers myself so can't answer your specific questions.

---

### Post by CyberX on 2006-07-04
Hi
I've been using Ubuntu 6.06 with LTSP in my classroom (I'm a teacher here in Portugal) in the last 2 months (1 year ago I knew nothing about Ubuntu, and  almost nothing about Linux in general).
I started with this document in the LTSP wiki:

[http://wiki.ltsp.org/twiki/pub/Ltsp/Documentation/ltspguide.pdf]("http://wiki.ltsp.org/twiki/pub/Ltsp/Documentation/ltspguide.pdf")

I remember having some problems with tftp, but after 1 night (in google and LTSP site, mostly) I was already using my first thin client.

My setup is a mix of thin-clients and fat-xp-clients (via Cygwin/X). The XP clients authenticate in a AD, but didn't even consider Active Directory integration, although I believe that it is possible, perhaps with Samba.

---

