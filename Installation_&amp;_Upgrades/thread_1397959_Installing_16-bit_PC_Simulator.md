---
title: "Installing 16-bit PC Simulator"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by Xiode on 2010-02-03
I'm currently in a class at Georgia Tech called CS2200 - Systems and Networks that's basically a low-level CS class that starts at the hardware level and abstracts up from there (processor design, multithreading, ISA's, etc..).

Anyway, we use this 16-bit ISA called the "LC2200", which basically simulates a very simple 16-bit computer.  For the first assignment, we were provided an assembly skeleton file and the actual simulator in a tarball.  We had to create a recursive assembly program that computed a power, given a base and a power.

However, I wasn't able to get the simulator to install on my Karmic Koala partition.  In our classes/labs, we use Red Hat 5 Enterprise, so I had to remote desktop into one of the servers in order to do the assignment.  My current setup is a 64-bit install of 9.10 running in VirtualBox on top of Windows 7 Professional.  Part of installing the simulator requires compiling the binaries via "make".  Initially, the problem was that I didn't have GCC installed.  After grabbing the latest version however, it was giving me errors that had to do with incompatible type conversions.  I know that it works, however, because it compiled successfully on the school computers running Red Hat.


I know that's a lot of information to take in, but does anyone have any suggestions on what the problem might be?  I attached a copy of the files we were provided (with the homework instructions) to provide a little more insight into what I'm asking.


Thanks in advance!
-Dan

---

### Post by gmargo on 2010-02-04
Surely a fine young computer science student such as yourself has figured it out by now. But if not, here is the patch I had to apply in order to compile on 9.10 Karmic with gcc-4.4.1 (although I only have 32-bits at my disposal.)

```

diff -urBw simpl-src-gt16.orig/common.h simpl-src-gt16/common.h
--- simpl-src-gt16.orig/common.h        2007-01-13 12:23:39.000000000 -0800
+++ simpl-src-gt16/common.h     2010-02-04 08:58:49.000000000 -0800
@@ -818,11 +818,11 @@

     /* TODO: Evil casting... */
     char* find(char c) const
-     { return strchr(mArray.begin(), c); }
+     { return const_cast<char*>(strchr(mArray.begin(), c)); }
     char* findr(char c) const
-     { return strrchr(mArray.begin(), c); }
+     { return const_cast<char*>(strrchr(mArray.begin(), c)); }
     char* find(const char* s) const
-     { return strstr(mArray.begin(), s); }
+     { return const_cast<char*>(strstr(mArray.begin(), s)); }

     String padLeft(char padChar, size_t len) const;
     String padCenter(char padChar, size_t len) const;


```

---

