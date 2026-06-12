---
title: "OLSR and Ubuntu Breezy Badger"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by rosho on 2005-10-21
Sorry for posting again here, but I think that I posted it before in the wrong section.

Could it be a problem if I put in the sources.list the repositories for the OLSR ([www.olsr.org](www.olsr.org)) binaries meant for Debian Sid?
In Hoary I had these repositories from [www.olsr.org:](www.olsr.org:)

deb [http://www.skyhub.de/debian/](http://www.skyhub.de/debian/) unstable main
deb-src [http://www.skyhub.de/debian/](http://www.skyhub.de/debian/) unstable main

Now I don't know if everything will be OK.
Thank you for the answer.

---

### Post by Kyral on 2005-10-21
Stuff built for Sid is kinda sketchy in Ubuntu. In THEORY it should work, but if it breaks (or breaks your system) we can't help you

---

### Post by cven on 2006-05-02
[QUOTE=rosho]Sorry for posting again here, but I think that I posted it before in the wrong section.

Could it be a problem if I put in the sources.list the repositories for the OLSR ([www.olsr.org](www.olsr.org)) binaries meant for Debian Sid?
In Hoary I had these repositories from [www.olsr.org:](www.olsr.org:)

deb [http://www.skyhub.de/debian/](http://www.skyhub.de/debian/) unstable main
deb-src [http://www.skyhub.de/debian/](http://www.skyhub.de/debian/) unstable main

Now I don't know if everything will be OK.
Thank you for the answer.[/QUOTE]

hi
If you want deal with olsr, then please use the olsrd-0.4.10.tar.bz2 from olsr.org and use the README/INSTALL
for compiling, you need also flex and bison.
I did it, that way and it works very fine with dapper and the ipw3945 in ad-hoc mode


for more info about olsr, join the olsr-users mailing list
[email]olsr-users@olsr.org[/email]
[https://www.olsr.org/mailman/listinfo/olsr-users](https://www.olsr.org/mailman/listinfo/olsr-users)

or have a look at [http://www.olsrexperiment.de](http://www.olsrexperiment.de) (mostly in german)

---

