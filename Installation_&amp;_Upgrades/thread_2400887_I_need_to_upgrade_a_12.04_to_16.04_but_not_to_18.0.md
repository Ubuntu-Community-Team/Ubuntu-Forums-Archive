---
title: "I need to upgrade a 12.04 to 16.04 but not to 18.04"
date: 2018-09-11
forum: Installation &amp; Upgrades
---

### Post by janosaudron on 2018-09-11
Can this be done? I need to upgrade a particular software in it but requires ubuntu 16.04, but 18.04 is not supported. How should I go about it?

Thanks to anyone in advance.

---

### Post by LHammonds on 2018-09-11
Can you backup your server, wipe it, install 16.04.5 LTS fresh, install the particular software and configure it to work on the new OS and then restore your data?

If you are not confident in the process, you could install 16.04.5 LTS inside a virtual machine and test/document how you would configure it, the software and what to restore so you can be confident in the wipe/install/restore process.

**EDIT:** This is how I "upgrade" all my servers even when it is supported to do in-place upgrades for the OS.  There are usually too many quirks in updated config files, library dependencies, deprecated functions, etc. to keep it from going 100% smooth.  It is easy for me though since everything runs in virtual machines on massive servers so spinning up additional servers is not an issue and I can just swap the server IP when the new server is ready to become the new production server.

LHammonds

---

### Post by janosaudron on 2018-09-11
Yes, I guess I can, I was trying to avoid doing that, I hoped maybe there was a cleaner way to upgrade to 16.04.

---

### Post by Autodave on 2018-09-11
In theory, you could upgrade to 16.04. In actuality (at least in my experiences) it rarely goes well or doesn't go at all. A new install is always the best and usually the quickest way.

---

