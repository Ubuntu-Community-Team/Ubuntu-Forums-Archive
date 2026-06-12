---
title: "install one package unstable"
date: 2017-09-20
forum: Installation &amp; Upgrades
---

### Post by landjalan on 2017-09-20
hi there,

i just took over an old linuxserver with 14.04 trusty running.

i am having difficulties installing firebird2.5-superclassic.

in ubuntu repositories firebird2.5.2 is the current version. the software(magellan) using firebird from now on wants 2.5.5 as firebird version.

how do i install 2.5.5 ? in gentoo it is enough to put firebird2.5-superclassic in /etc/portage/package.keywords.

what do i have to do to install firebird2.5-superclassic(2.5.5) in ubuntu ?

thanks a lot!!

---

### Post by Perfect Storm on 2017-09-20
If you don't mind getting 3.02 version there's is a PPA for it: [https://launchpad.net/~mapopa/+archive/ubuntu/firebird3.0?field.series_filter=trusty](https://launchpad.net/~mapopa/+archive/ubuntu/firebird3.0?field.series_filter=trusty)
Or does it have to be version 2.5.5?

EDIT: 2.5.6 can be found here: [https://launchpad.net/~mapopa/+archive/ubuntu/ppa](https://launchpad.net/~mapopa/+archive/ubuntu/ppa)

---

### Post by kc1di on 2017-09-20
> **landjalan said:**
> hi there,

i just took over an old linuxserver with 14.04 trusty running.

i am having difficulties installing firebird2.5-superclassic.

in ubuntu repositories firebird2.5.2 is the current version. the software(magellan) using firebird from now on wants 2.5.5 as firebird version.

**how do i install 2.5.5 ? in gentoo **it is enough to put firebird2.5-superclassic in /etc/portage/package.keywords.

what do i have to do to install firebird2.5-superclassic(2.5.5) in ubuntu ?

thanks a lot!!

If your using gentoo then you'd be better off asking in the gentoo forums found[ here: ]("https://forums.gentoo.org")

other than that you can download and build firebird 2.5.5 from [here.]("https://firebirdsql.org/en/firebird-2-5-5/#Linux_AMD64")

---

