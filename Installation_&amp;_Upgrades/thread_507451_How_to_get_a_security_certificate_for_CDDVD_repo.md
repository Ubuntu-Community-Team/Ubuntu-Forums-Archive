---
title: "How to get a security certificate for CD/DVD repo?"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2007-07-23
Hello there!
My problem is rather common but I couldn't find any solution here, so I post my question. I want to make a local CD repository that I plan to use for postinstall purposes. I copied packages in a single folder, say 'repo', then executed the following command to build the Packages.gz file:```
dpkg-scanpackages repo /dev/null | gzip -9c > repo/Packages.gz
```I burnt it on a CD after that, and it works fine on a machine that I used to create the CD, but aptitude gives me a warning if I try to install it somewhere else:> WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.
What do I do? Thank you in advance! ;)

---

### Post by gwoodard on 2007-07-25
It may be that some programs you could have installed after the fact could be erased (firmware, multiverse which are not free) and it is warning you that if installed on other computers that you could be doing in the copyright files to the programs that may have been installed

Or maybe something is messed up and is warning you not to use it, I don't know, it is your call

---

### Post by az on 2007-07-25
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

See the part about including a gpg key on the cd and then you will need to add the key to apt.

---

