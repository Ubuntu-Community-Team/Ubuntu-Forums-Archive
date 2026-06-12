---
title: "Compile problems with mPlayerplug-in plugin"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2007-01-05
I'm trying to follow the instructions for creating the mPlayer plug-in for Opera in the HOWTO section, but I'm having some trouble.  I try to run the ./configure script for mplayerplug-in (Emperor, page 2) it checks for utilities it needs and finds gpp, then gives this output:

```
root@Lithium:/home/downloads/mplayerplug-in# ./configure --enable-x --with-gecko-sdk=/home/downloads/gecko-sdk
checking for g++... no
checking for c++... no
checking for gpp... gpp
checking for C++ compiler default output file name... b.out
checking whether the C++ compiler works... configure: error: cannot run C++ compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
root@Lithium:/home/downloads/mplayerplug-in#
```

EDIT: Apparently I *didn't* have a compiler.  I had G++ 4.0 package but not G++.  After installing this with synaptic it got past that point with no errors.  The next step is to run "make".  I did this and got about 10,000 errors.  I can post that output if anyone needs it.  The instructions I am using are [Here](http://www.ubuntuforums.org/showpost.php?p=4098&postcount=12)

*Because that post is pretty old, I got the newest packages instead of following those links.

---

