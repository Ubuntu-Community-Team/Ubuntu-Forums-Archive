---
title: "HELP apt-get and update manager not working"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by mic159 on 2007-12-23
everytime i try to install updates or new programs via apt-get or the update manager i get this error:
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/binfmt-support_1.2.10_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `libgnome-keyring0': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/binfmt-support_1.2.10_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

why is this happeneing?

is there a solution?

what broke? :S

---

### Post by Edfrommars on 2007-12-23
I'm not sure if it'll help but try doing a

```
sudo apt-get clean
```

Restart your computer and try to update again.

---

### Post by mic159 on 2007-12-23
nope, still not working.

---

### Post by mic159 on 2007-12-30
Bump, still not working...

---

### Post by mic159 on 2007-12-31
well i managed to fix it and here is how i did it:
somehow, the libgnome-keyring0.list file in dpkg got corrupted and turned into a folder.
So all i had to do was delete that folder from /var/lib/dpkg/info

[This]("http://ubuntuforums.org/showthread.php?t=24236") thread got me the answer i was looking for

---

