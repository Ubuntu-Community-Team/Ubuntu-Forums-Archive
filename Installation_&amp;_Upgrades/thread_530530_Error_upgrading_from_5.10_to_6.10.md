---
title: "Error upgrading from 5.10 to 6.10"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by UnknownPg on 2007-08-20
I found an old Kubuntu CD and decided to install it but found out it was "Breezy" and I wanted to update to edgy and then eventually Fiesty. So I followed these directions [http://ubuntuforums.org/showthread.php?t=285099](http://ubuntuforums.org/showthread.php?t=285099) and I get this error after everything is downloaded 

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 57171 files and directories currently installed.)
Unpacking volumeid (from .../volumeid_093-0ubuntu18.0edgy2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/volumeid_093-0ubuntu18.0edgy2_i386.deb (--unpack):
 trying to overwrite `/sbin/vol_id', which is also in package udev
Errors were encountered while processing:
 /var/cache/apt/archives/volumeid_093-0ubuntu18.0edgy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mocoloco on 2007-08-22
You cannot upgrade from 5.10 (Breezy) to 6.10 (Edgy), you would have to go
5.10 (Breezy) -> 6.06 (Dapper)
6.06 (Dapper) -> 6.10 (Edgy)
6.10 (Edgy) -> 7.04 (Feisty)

Doing so would be a pain and would use a lot of bandwidth and time, so you're better off just downloading and burning a 7.04 disc and doing a fresh install.  Because the world of Linux moves so fast, and Ubuntu in particular, old discs quickly become coasters :).

If you still feel you must upgrade incrementally just use the regular update manager, except that Dapper won't offer to upgrade because of it's long-term support, so on Dapper you would hit Alt-F2 and type
```
update-manager -c
```

---

