---
title: "error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by ahso4271 on 2012-06-16
error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

So still is still broken on 12.04 64bit....sigh....no wonder nobody supports Linux...broken for 2 months or what?

---

### Post by ahso4271 on 2012-06-16
Or, instead of editing the file ld.so.conf directly, create a file  called local.conf in the subdirectory /etc/ld.so.conf.d containing just  the line /usr/local/lib.  That is,

Contents of  /etc/ld.so.conf.d/local.conf:

/usr/lib32

Then run the ldconfig command.  (This assumes that the file  /etc/ld.so.conf contains the line include /etc/ld.so.conf.d/*.conf.   This is not the case in Dapper, but appears to be true in later versions  of Ubuntu.)

You only have to do this once.

That worked but hey what year is it? 1991?

---

### Post by osirisx11 on 2013-06-10
Thank you so so much for this! It worked. It actually worked. Spent many many hours googling and trying things and bugging #ubuntu. It all started after I borked my install of nvidia binary. Skype would refuse to start. All solved now! Thanks so much.

---

