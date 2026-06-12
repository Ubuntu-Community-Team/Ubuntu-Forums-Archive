---
title: "mdadm errors with 11.10"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by ClangerMan on 2011-12-09
I've been using Symbolik's process ([http://symbolik.wordpress.com/2009/05/01/howto-kubuntu-904-raid-10-lvm2-and-xfs/](http://symbolik.wordpress.com/2009/05/01/howto-kubuntu-904-raid-10-lvm2-and-xfs/)) to build a raid 10 array with 10.04.1 LTS: it works perfectly, and the scripts to automate it (avoiding finger trouble) run very reliably and quickly.

When I run the same scripts on the same hardware under 11.10, mdadm mis-operates as follows:
1) it refuses the chunk size I give it, and substitutes its default of 64 k (not a problem, but not encouraging either) message: "chunk size ignored for this level"
2) it ignores the value (4) I give for --raid-devices (abbreviated to -n) and substitutes the value 2, and goes on to create duplicate arrays md126 & md127 in addition to the arrays md1 and md2. (md0, the raid-1 boot array, is created correctly). message: "layout defaults to n2"

Whilst I have my reservations about the GUI on the new Ubuntues, I don't want to have to live with an (eventually) unsupported version. Can anyone offer a clue as to what might be going wrong, and how I may correct it?

If further diagnostic information is needed, please don't hesitate to indicate what will be needed.

Thank you all           :confused:

Solution: this version of mdadm (3.1.4) recognises the "--raid-devices=" parameter, but not the abbreviated "-n" form. Similarly the use of "--chunk=" instead of "-c" has resolved that problem.

---

