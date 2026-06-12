---
title: "How to install an older version of g++"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by matrix72 on 2010-02-03
Hi all.

I have problem installing a program (GTNets) since it requires an older version of g++ (3.3), while the current version of g++ is 4.4 in my ubuntu installation (vers 9.10). Can anyone give me recommendations on how to solve this?

I guess that there should be able to install an older version of g++ in addition to the current g++. Furthermore, the current should be the default, while the older is an optional version.

Please help.

Thx

---

### Post by gmargo on 2010-02-04
_GTNets_ does not require version 3.3 of the compiler (but that's probably how it was originally tested.)

What OS version are you using?  

Under 8.04 Hardy with gcc-4.2.4, it compiles and runs without changes.

Under 9.10 Karmic with gcc-4.4.1, I did have to make a few minor patches.  All the changes were adding "#include <cstring>" lines.  With these patches, GTNets compiles and runs.

See attachment for compressed patch file for Karmic.

Mind you, since I don't really know how to run GTNets, I'm not sure it's working as it should.  But at least it runs :-).

---

