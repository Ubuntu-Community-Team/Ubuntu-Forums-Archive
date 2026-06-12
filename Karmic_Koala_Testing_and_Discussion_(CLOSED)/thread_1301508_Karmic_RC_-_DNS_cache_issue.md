---
title: "Karmic RC - DNS cache issue?"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nat42 on 2009-10-26
I have installed the latest release candidate of Karmic Koala (fresh install with new HDD from the alternative/text install AMD64 CD) and things seemed to go OK - it did freeze up at the setting up "Groups and Policies" stage (adding my user to the admin group failed as it was already a member apparently) but the install worked when I rebooted.

However, I since then DNS lookup have been flakey, about a 1/4 of the domain lookups resolve and cache the wrong IP. I might attempt a Google search and get a 404 error from Canonical Squid server or I my attempt to go to Gmail and get a strange error from ebay.

I have verified this behaviour affects not just Firefox & another browser (Chrome) but also 'nslookup'. And I have observed it with various DNS servers (which I have varied in turn on the router & on the PC by altering 'resolv.conf').

Does anyone know what part of my Ubuntu distro is responsible for DNS lookups, and how to go about troubleshooting it? (I have found info on Bind9, but it seems to pertain to running ones own DNS server... a different problem altogether I think)

---

### Post by nat42 on 2009-10-26
](*,) Hmm, as much as I want to get to the bottom of this, I want to get rid of it more... Am re-downloading another RC image and will trying installing over the top of this install (with fingers crossed)

---

### Post by leftcase on 2009-10-26
Could it be this?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757)

---

