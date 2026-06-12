---
title: "corrupted apt/dpkg"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by worldDownInFire on 2006-07-15
I just started setting up Dapper after running Breezy for a few months on another system.  During some of my installs (via the command line apt) my computer froze (for reasons unrelated to this) and as a result, my /var/lib/dpkg/available is now corrupt...

[FONT="Courier New"]dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `' must be followed by colon[/FONT]


googling came up with a forum post recommending using a backup (/var/lib/dpkg/available-old) which I did.  I don't get the error about the "available" file now but instead get the following when trying to apt-get install gkrellm

[FONT="Courier New"]Setting up gkrellm-common (2.2.7-5ubuntu1) ...
Setting up gkrellm (2.2.7-5ubuntu1) ...

Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]


googling has failed to yield anything I could make sense of.  Any help would be greatly appreciated.

---

