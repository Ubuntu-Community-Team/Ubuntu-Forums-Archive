---
title: "samba error &quot;couldn't display all the contents of &lt;foo&gt;&quot;"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by asarwate on 2005-06-07
So I'm trying to access the file servers on a windows network, and Ubuntu sees the network just fine but when I go to browse the list of servers I get:

    Sorry, couldn't display all the contents of "Windows Network: czr".

where czr is the name of the network -- the resulting window has no machines listed.  Thsi happened under the current Warty version of samba and also with the slightly newer backports version, so I suspect it might be a problem with a lower-level package which was somehow corrupted during the install process.

Anyone know what this error means?

---

