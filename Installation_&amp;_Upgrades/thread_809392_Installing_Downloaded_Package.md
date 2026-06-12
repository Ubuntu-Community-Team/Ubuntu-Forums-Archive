---
title: "Installing Downloaded Package"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Dan++ on 2008-05-27
I'd like to install a beta version of a package available through synaptic (release is 6.8, beta is 6.10), called testdisk, so I downloaded it, decompressed the tar.gz and here's the structure:

```
.:
AUTHORS    COPYING             ico   linux  README
ChangeLog  documentation.html  INFO  NEWS   THANKS

./ico:
photorec.ico  testdisk.ico

./linux:
l  photorec.1  photorec_static  readme.txt  testdisk.1  testdisk_static

./linux/l:
linux

```

**There's supposed to be a binary I can run**, according to my searches on Google, but **I'm not sure where or how to run it.**

Any ideas? Thanks!:)

---

### Post by hal8000 on 2008-05-27
Here's the install instructions:
[http://www.cgsecurity.org/wiki/TestDisk_Compilation](http://www.cgsecurity.org/wiki/TestDisk_Compilation)

after installing the executable may not be in /usr/sbin so you may have to look for it if its not on the path.

With HH 8.04 testdisk 6.8 installs to /usr/sbin, so after installing you may find that it installs to /usr/local

The changelog between 6.8 and 6.10 offers only some small improvements so its up to you if you decide to test beta software on a stable system.
Hope that helps

---

### Post by Dan++ on 2008-05-28
> **hal8000 said:**
> Here's the install instructions:
[http://www.cgsecurity.org/wiki/TestDisk_Compilation](http://www.cgsecurity.org/wiki/TestDisk_Compilation)

after installing the executable may not be in /usr/sbin so you may have to look for it if its not on the path.

With HH 8.04 testdisk 6.8 installs to /usr/sbin, so after installing you may find that it installs to /usr/local

The changelog between 6.8 and 6.10 offers only some small improvements so its up to you if you decide to test beta software on a stable system.
Hope that helps
Don't those instructions apply only to the source version?

And it's not so much testing beta software as needing the new features :) 6.8 doesn't search for txt files (the files I need most from my broken disk) without causing an error, and apparently 6.10 fixes that.

Thanks :)

---

