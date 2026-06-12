---
title: "getlibs not fetching libQtWebKit.so correctly"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by LonelyStar on 2010-10-07
Hi,

I am trying to compile a 32 bit project in an 64 Bit ubuntu envoirement.

I found getlibs, wonderful program, solved most of my linker errors.
Now I did:
getlibs -l libQtWebKit.so

Which work, did not complain about anything.
But I got:

file /usr/lib32/libQtWebKit.so
/usr/lib32/libQtWebKit.so: broken symbolic link to `libQtWebKit.so.4.7.0'

There is also:
file /usr/lib32/libQtWebKit.prl
/usr/lib32/libQtWebKit.prl: ASCII text, with very long lines

No Idea what that does.

And that is all I can found of libQtWebKit files in /usr/lib32.

Any Ideas what I could do?

Thanks!
nathan

---

