---
title: "Can't upgrade, please help"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by Kyle12349 on 2008-08-19
I've noticed that I can upgrade to Ubuntu 7.10 in the Update manager but every time I try to upgrade I keep getting an error. I need an answer to two questions, will my hard drive get wiped if I upgrade and why do I keep getting the "network error?"

Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.compiz.net/dists/edgy/main-edgy/binary-i386/Packages.gz](http://ubuntu.compiz.net/dists/edgy/main-edgy/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://apt.emesene.org/./Sources.gz](http://apt.emesene.org/./Sources.gz) 404 Not Found

---

### Post by bitninja on 2008-08-20
Well just looking here:

[http://gb.archive.ubuntu.com/ubuntu/dists/](http://gb.archive.ubuntu.com/ubuntu/dists/)

It seems that the edgy directory doesn't even exist...which is odd but I'm not quite sure how to fix that one. In response to your other question, no if you upgrade your hard drive should NOT be wiped, it should just upgrade all necessary files and work around your documents, programs and such.

---

### Post by kspncr on 2008-08-20
> **bitninja said:**
> It seems that the edgy directory doesn't even exist.

Well, edgy is no longer supported by Canonical...It's support ended on 4/25/08.

---

### Post by bitninja on 2008-08-20
Oh yeah I forgot about that. Nice catch.

---

### Post by Kyle12349 on 2008-08-20
Thank you for the reply. So there's nothing I can do about upgrading through Update Manager?

---

### Post by bitninja on 2008-08-20
Nope, but I think maybe you can do an upgrade from a CD? I'm not quite sure. You should do some googling to see if you can upgrade from the CD of the version you want.

---

### Post by Kyle12349 on 2008-08-20
Well I'm under 7.04 now and the Manager is showing an upgrade for 7.10 even though there is a 8.04.1? I would upgrade from disc but my computer refuses to burn for some reason. I've tried on google, I've downloaded the iso but I don't know where to go from there. If I upgrade from disc, would it wipe the hard drive that way? Or would it be exactly the same as updating with the Update Manager?

---

### Post by bitninja on 2008-08-20
Copied verbatim from [http://www.ubuntu.com/getubuntu/upgrading:](http://www.ubuntu.com/getubuntu/upgrading:)

> Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download and burn the alternate installation CD.
   2.

      Insert it into your CD-ROM drive.
   3.

      A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4.

      Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesu "sh /cdrom/cdromupgrade"


---

