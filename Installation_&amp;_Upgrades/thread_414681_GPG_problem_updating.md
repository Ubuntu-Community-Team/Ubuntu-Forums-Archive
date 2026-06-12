---
title: "GPG problem updating"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Pom_ on 2007-04-20
Hi,

I try to upgrade from edgy to feisty (like a lot of people here ...) using the official command :
gksu "update-manager -c"

But no upgrade button appears (I have done this many times before for other upgrades ...), logically, because when I do an apt-get update, the following error appears :
```
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

I had also tried with ch.archive (same gpg key errors), also tried to download another gpg key from a gpg server (same result) and also tried to download the key from the server (Release.pgp, but "gpg: no valid OpenPGP data found." error).

What could/should I do ? 
Is there a server GPG key corruption or missfunction ?

Thanks for your answers.

Pom

---

