---
title: "OEM install questions..."
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by pangalactic on 2007-10-20
I am trying to set up an oem install. I get the gist of how it works, but what I'm wanting to do is get the  oem user account to copy settings to the newly created user. I want the menus and default apps to copy to the newly created use. Is there an easy way to do this, or do I need to invent this wheel?

Thanks in advance

---

### Post by afoglia on 2007-10-21
Coincidentally I was trying to figure this out myself this weekend.  You'll want to copy any changed configuration files to the /etc/skel directory.  Those files are the skeleton of the home directories of any new accounts, and copied to the new homes.  For Ubuntu, the most important files are in the .gconf, .gconf2, .gnome, .gnome2, and .nautilus directories.

I got that from an [Ubuntu mailing list post]("https://lists.ubuntu.com/archives/ubuntu-users/2006-April/073867.html").  Another response suggested a more complicated (but better if it works) way by pointing to the [Gnome System Adminstrator's Guide]("http://www.gnome.org/learn/admin-guide/latest/").

The final user hasn't set up the computer yet, so I don't personally know yet if it'll work.

---

