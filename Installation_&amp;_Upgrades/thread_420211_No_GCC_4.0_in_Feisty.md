---
title: "No GCC 4.0 in Feisty?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by minneyar on 2007-04-23
I just upgraded from Edgy to Feisty, and everything went fine, except for the fact that there doesn't appear to be a gcc-4.0 package in the official repositories.  I recall that Edgy had 3.3, 3.4, 4.0, and 4.1; I need 4.0 for a particular third-party library I'm using (no, I don't have a choice), but I only see 3.3, 3.4, and 4.1 in Feisty's repositories.

There's a gcc-4.0-base package, but it doesn't seem to install much of anything, and there's also a gcc-4.0-locales package, but it depends on cpp-4.0, which doesn't exist.  Does anybody have a clue what's going on here?

---

### Post by zvacet on 2007-04-23
** cpp-4.0** is Edgy package.You can find it here

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=cpp-4.0&searchon=names&subword=1&version=edgy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=cpp-4.0&searchon=names&subword=1&version=edgy&release=all")

---

### Post by minneyar on 2007-04-24
Thanks.  Further investigation reveals that for some reason, GCC 4.0 was removed from Feisty, although I don't know why.  I managed to get the latest source package from Edgy and build and install it without too much trouble.

---

