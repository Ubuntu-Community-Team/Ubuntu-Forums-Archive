---
title: "Can't upgrade anymore"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by theswortz on 2006-08-24
Every time I try to get the latest updates, whether it be through apt-get or synaptic, the updates fail. The packages are downloaded but they don't get installed. This is what happens when I run sudo apt-get upgrade:
```

Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  ktorrent libtheora0 xserver-xorg-core
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5326kB of archives.
After unpacking 3817kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing /var/cache/apt/archives/ktorrent_2.0.1-0ubuntu1~dapper1_i386.deb (--unpack):
 files list file for package `liblua50' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/ktorrent_2.0.1-0ubuntu1~dapper1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by vanamar on 2006-08-24
I am receiving this message as well.

---

### Post by az on 2006-08-24
The "files list file for package `liblua50' is missing final newline" is a clue that your package database is borked.  I dunno how it happens, but it does, from time to time.  Maybe an interrupted install or something?


sudo dpkg --clear-avail

should fix it.


Then, update and try again to install

---

### Post by vanamar on 2006-08-24
Did that, no help. =(  This is a fresh install of Dapper 6.06.1 that completed without incident.

---

### Post by vanamar on 2006-08-24
Solution!

# sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_move
# sudo mkdir /var/lib/dpkg/info
# sudo apt-get update

Then try installing packages.:grin:

---

### Post by theswortz on 2006-08-25
I tried azz's solution first and that didn't work. But then I tried vanamar's solution and it did work after that. The only thing is that a bunch of warnings popped up when I did the upgrade. No errors, just warnings. What exactly does that info folder contain?

---

