---
title: "Unable to install linux-image-2.6.17-10-386"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by jecspasc on 2006-12-19
I have had an update for several days that I haven't been able to
install. The update is "linux-image-2.6.17-10-386". When I try to
install this update, I get a pop-up window that says "An Error Occurred"
followed by the following:

E: /var/cache/apt/archives/linux-
image-2.6.17-10-386_2.6.17.1-10.34_i386.deb: subprocess new pre-
removal script returned error exit status 2

For a while this was only a minor annoyance, but now I can't install
other packages because this package runs first and errors out.

Any help will be appreciated.

Jim

---

### Post by jecspasc on 2006-12-21
Google was my friend.  I found that I had installed a version of perl that was the root of my problem.  By using Synaptic to reinstall perl-base and perl-modules, my problem went away.

Merry Christmas and a most Happy New Year to all.

Jim

---

