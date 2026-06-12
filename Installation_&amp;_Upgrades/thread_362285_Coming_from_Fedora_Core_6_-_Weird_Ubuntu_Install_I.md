---
title: "Coming from Fedora Core 6 - Weird Ubuntu Install Issue"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by broy on 2007-02-15
I have had this wierd problem with FC5 and 6 when installing Ubuntu. It's almost like Fedora puts root-only permissions on your filesystem, so when you try to install windowsxp or ubuntu or basically anything else it will fail (or in the case of windowsxp not do anything). So what I've had to do is boot into Fedora and do this:

chmod -R 777 /

which is completely stupid but it works. idk.

---

### Post by meng on 2007-02-15
That 'fix' sounds like a great way to screw up your Fedora install actually. How exactly did you try to install the other OSes? What changes did you make to the partition table?

---

