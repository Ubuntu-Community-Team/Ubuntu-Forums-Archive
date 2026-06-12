---
title: "Linking against older versions of glibc"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by daborg on 2007-01-17
Hi,

I need to link a C program against an older version of glibc than 2.4. Unfortunately I can only find packages for glibc 2.4 in the repositories. How would I go about linking a program against older glibc versions on Ubuntu?

---

### Post by po0f on 2007-01-18
daborg,

Linking against an older version of glibc would require you building/installing that version.  It'd probably be more headache than it's worth trying to do this, you really don't want to break glibc.  ;)

The easiest way would be to install a Dapper chroot (I'm assuming you need glibc 2.3.X?) and compiling your program from there.  There are a couple of HOWTOs floating around the forum about using a chroot, just find one and adapt it to your needs.

If you need help, post back.

---

### Post by daborg on 2007-01-19
Worked like a charm, thanks a bunch for the suggestion!

---

