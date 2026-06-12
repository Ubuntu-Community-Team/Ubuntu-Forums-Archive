---
title: "LTSP client fails to start building"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by extradessert on 2012-06-14
I'm trying to build a LTSP install on my 10.04 computer.

Trying to put it on a separate /opt partition, but it fails with: 

/usr/sbin/debootstrap: 471: cannot create /opt/ltsp/i386/test-dev-null: Permission denied
E: Cannot install into target '/opt/ltsp/i386' mounted with noexec or nodev
error: LTSP client installation ended abnormally

If I don't use the separate partition it works fine.

Wondering if fstab needs special mount options or something.

---

### Post by extradessert on 2012-06-18
bump?

Is there a LTSP specific forum?

---

### Post by gnusci on 2012-06-18
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by extradessert on 2012-06-18
I've checked that wiki over and over again, I haven't seen anything about a separate /opt partition.

---

### Post by gnusci on 2012-06-18
your question has nothing to be with "LTSP client fails to start building"

Make your research first and make the right question.

---

### Post by extradessert on 2012-06-18
I think you misread my question.

I run 'sudo ltsp-build-client --arch i386' and it gives me the message given in OP.

To me that's fails to start building.

---

### Post by extradessert on 2012-06-19
Solved, thanks to help on #ltsp

Had to take out the 'user' part in mount setting in fstab.

---

