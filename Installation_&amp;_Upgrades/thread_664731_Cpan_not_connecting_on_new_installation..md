---
title: "Cpan not connecting on new installation."
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by jimford on 2008-01-11
I posted this in the programming forum, but have received no answers. As this problem has occurred 'out of the box' - on a fresh installation, I thought I'd mention it here. 

I've been using a Kubuntu 'Breezy Badger' set-up for some time with no problems - but thought it was time to update by installing a later distro on another box.

I've installed Ubuntu 7.10, but when I tried running cpan to install the modules I use on the other box, I get connection problems with timeouts by failing to connect to [ftp://ftp.perl.org](ftp://ftp.perl.org). Cpan doesn't appear to be down as I can connect on the old box.

There's no difference if I run 'sudo cpan'.

Ideas, anyone please?

Jim Ford
_____

---

### Post by reckless2k2 on 2008-01-11
you just need to go into the config file and config a new mirror. i heard this was happening over at zimbra with same issues.

---

### Post by jimford on 2008-01-14
> **reckless2k2 said:**
> you just need to go into the config file and config a new mirror. i heard this was happening over at zimbra with same issues.

Thanks, but running 'o conf init' doesn't invite me to input a mirror, just proxies. When I run (say)
'i /cpan/',  cpan just assumes 'ftp://ftp.perl.org/pub/CPAN/'. With the 'old' box on the same network I didn't need to configure any mirrors, cpan just found them.

JIm

---

