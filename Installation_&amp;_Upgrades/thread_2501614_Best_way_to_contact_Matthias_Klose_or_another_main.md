---
title: "Best way to contact Matthias Klose or another maintainer regarding courier-imap?"
date: 2024-10-15
forum: Installation &amp; Upgrades
---

### Post by aathan on 2024-10-15
I've been in touch with the maintainer of the courier mail system, and it HAS been ported to libpcre2. However, based on what I see here: [https://launchpad.net/ubuntu/noble/amd64/courier-imap](https://launchpad.net/ubuntu/noble/amd64/courier-imap)

Matthias Klose removed courier-imap and courier-webadmin from Ubuntu 24.04 because he believes it depends on PCRE3

I did not get a response to my email to him, so I'm thinking mail filters are getting in the way.

---

### Post by ian-weisser on 2024-10-15
The package, according to the link you provided, was removed due to multiple problems detailed at the Debian tracker: [https://tracker.debian.org/pkg/courier](https://tracker.debian.org/pkg/courier)
Security issues, transitions unfinished, dependency problems, no new upload in a very long time, etc.

 It's great to read that the dependency problems may have been fixed, but the other blocking problems remain.

Ubuntu gets most deb packages from Debian. So the best way to get the package back into Ubuntu is for a volunteer to start fixing those problems in Debian. When restored in Debian, it will flow automatically back into Ubuntu. Anyone interested can start at [https://mentors.debian.net](https://mentors.debian.net)

Alternately, a volunteer could create (and commit to maintain) a Snap package. That's the usual way to bypass Debian.

---

