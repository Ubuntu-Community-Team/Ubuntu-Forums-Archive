---
title: "FQDN / hostname problems"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by tenjin on 2005-09-20
Hi,

When I set up my Ubuntu server I seem to have messed up the hostname / FQDN of the machine.

Here's what I have:

My machine is called "king". I have a domain called "tenjin.co.uk". I entered "king.tenjin.co.uk" during the Ubuntu installation.

However, when I ran "vino" and "mutt" I get a hostname of king.tenjin.co.uk.tenjin.co.uk

The contents of /etc/hostname are:

king.tenjin.co.uk

hostname gives:

king.tenjin.co.uk

Any ideas how I can clean my system so that everything stores the domain name as "king.tenjin.co.uk"?

I've entered the FQDN in the Ubuntu control panel for networking (I entered "king.tenjin.co.uk" in the "hostname" field. Is this right, or should I have put "king" in the hostname field, and "tenjin.co.uk" in the domain field?)

Cheers

D.

---

### Post by KingBahamut on 2005-09-20
What does your /etc/hosts file have in it?

---

### Post by tenjin on 2005-09-20
Hi,

Thanks for the tip.

I've sorted it now.

Cheers

D.

---

### Post by mmoo9154 on 2008-05-29
Wow Tenjin, I know you wrote this a long time ago, but it's pretty lame to not explain what you did to solve your problem.

I've got the same problem with Ubintu 8.04 (Hardy).  I'll post if/when I get it resolved.

---

### Post by tenjin on 2008-05-29
Hi,

You're right, my bad.

IIRC I think putting the FQDN in the Ubuntu networking dialog created a bad /etc/hosts file.

I think all I did was manually edit the hosts file to remove the duplication, then restart the machine.

If that doesn't work post another message and I have a think. BTW, my Ubuntu server is out of action at the moment so I don't have a machine to test things on.

Cheers

D.

---

