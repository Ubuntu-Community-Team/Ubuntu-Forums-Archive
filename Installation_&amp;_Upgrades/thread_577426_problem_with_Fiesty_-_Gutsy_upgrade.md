---
title: "problem with Fiesty - Gutsy upgrade"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by thinksojoe on 2007-10-16
My attempts to upgrade to Gutsy from Feisty have been futile.  I get this error

"failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)"

Any idea how to fix it?

I can't upgrade via CD because of some kind of freak technical issue with the CD drive on my laptop, so essentially the only ways I can do it are via apt or a USB drive

**SOLVED**

after further research, I found that I should have just changed from http to ftp in my sources.list file.

---

### Post by adonikam on 2007-10-19
how do you do this? whenever i try to update sources, i get the same error that i get when i try to update!
Sub-process gzip returned an error code

---

