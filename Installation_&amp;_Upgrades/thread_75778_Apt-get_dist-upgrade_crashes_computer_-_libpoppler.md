---
title: "Apt-get dist-upgrade crashes computer - libpoppler0c2"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by localzuk on 2005-10-14
Hi,

I am trying to apt-get dist-upgrade from the RC Breezy to Final Breezy and it is causing my laptop to freeze.

It gets as far as 'Setting up libpoppler0c2-glib...' and then I get constant hard disk activity and my computer stops responding. I can't switch to another virtual terminal.

I have to cold-reset the laptop.

When I'm back in and running, it asks me to run 'dpkg --configure -a' due to the apt-get dist-upgrade being interrupted - but it just does the same thing again.

Any help would be great.

Cheers
Tony

---

### Post by localzuk on 2005-10-14
It seems to have sorted itself on the 5th run of dpkg --configure -a? Very odd

---

