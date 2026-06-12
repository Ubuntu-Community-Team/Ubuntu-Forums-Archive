---
title: "tzdata not happy"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by homegrown on 2007-03-17
I've been having trouble with the tzdata package -- The problem has existed for a couple of weeks, but now I really want to get this sorted.

Please see what happens when I try & upgrade below:

The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 188 not upgraded.
1 not fully installed or removed.
Need to get 0B/315kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 275898 files and directories currently installed.)
Preparing to replace tzdata 2007a-3ubuntu1 (using .../tzdata_2007b-0ubuntu1_all.deb) ...
Unpacking replacement tzdata ...
dpkg: error processing /var/cache/apt/archives/tzdata_2007b-0ubuntu1_all.deb (--unpack):
 **unable to make backup link of `./usr/share/zoneinfo/Antarctica/Casey' before installing new version: Operation not permitted**
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2007b-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm in London, not Antarctica! 

Any tips would be appreciated.

---

### Post by davebgimp on 2008-02-25
I'm having this same problem with another package. Did you ever resolve this?

---

