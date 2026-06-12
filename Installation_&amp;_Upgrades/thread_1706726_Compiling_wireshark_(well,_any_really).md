---
title: "Compiling wireshark (well, any really)"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by Xeneth on 2011-03-14
I am compiling wireshark, and when I do ./configure, there's no errors, but it can build, but it's still missing header files which will affect capabilities.  

Second question is that while I was able to get it working with the last version I had, I cannot make the interfaces show up unless I run as root.  The normal tricks are not working.  I even went as far as to make my user the owner, but still no, so I do not believe it's with the permission with dumpcap, yet I get a permission error when I call it directly too.

Granted, I have not been able to test it after downloading a bunch of packages to get some of the header files, but I'm looking for a way to find the correct packages without Google and guessing.

Any help would be most Appreciated.  

PS. I do get warnings when running wireshark, though those seem mostly about defaults and preferences.

---

