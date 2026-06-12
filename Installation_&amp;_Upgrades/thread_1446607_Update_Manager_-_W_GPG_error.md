---
title: "Update Manager - W: GPG error"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by mmosier1 on 2010-04-04
I'm running Ubuntu 9.10 and getting the following error when I try to run Update Manager...

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

Any ideas on how to fix this?

Thanks

mm

---

### Post by byStanderone on 2010-04-04
...here's a thread that runs parallel to your problem, taking a look at it, seems to show that the medibuntu site is active on the software sources list, the reason why the gpg pubkey is being required. take a look also at your sources list, you might want to uncheck medibuntu should it be in use, that is if you don't need it...but if you are using it, follow the thread's suggestions: [http://ubuntuforums.org/showthread.php?t=318519](http://ubuntuforums.org/showthread.php?t=318519)

---

### Post by mmosier1 on 2010-04-04
> **byStanderone said:**
> ...here's a thread that runs parallel to your problem, taking a look at it, seems to show that the medibuntu site is active on the software sources list, the reason why the gpg pubkey is being required. take a look also at your sources list, you might want to uncheck medibuntu should it be in use, that is if you don't need it...but if you are using it, follow the thread's suggestions: [http://ubuntuforums.org/showthread.php?t=318519](http://ubuntuforums.org/showthread.php?t=318519)

Thanks!

mm

---

