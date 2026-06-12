---
title: "Upgrade to Feisty blocked by '404 Not Found [IP: 82.211.81.138 80]'"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by matjaz_pirnovar on 2007-05-27
Hi,

I'm getting this error when apt-get update. It's preventing me to upgrade to Feisty.

As I know this IP is located in UK and I am in UK as well.


Failed to fetch [http://security.ubuntu.com/ubuntu/ed...ty/Packages.gz](http://security.ubuntu.com/ubuntu/ed...ty/Packages.gz) 404 Not Found [IP: 82.211.81.138 80]


What do I need to do to make it work? Is it temporarily or something in my system?

Thanks, Matjaz

---

### Post by matjaz_pirnovar on 2007-05-27
What does it mean?

Google doesn't throw out anything useful, neither this forum search.  Why am I getting an IP error?

I modified my sources.list with no success.  Security repositories are independent of the mirrors right?

Is it my internet connection?


Thanks for any clues.

Matjaz

---

### Post by D@niel on 2007-05-27
Try this one:
[http://security.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)

(copy the whole link, that is also shown in the status bar)

---

### Post by matjaz_pirnovar on 2007-05-27
> **D@niel said:**
> Try this one:
[http://security.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)

(copy the whole link, that is also shown in the status bar)

Thanks.

Just ...where exactly I need to paste it?


In my sources list..mm, doesn't feel right.

Sorry...am not the best with this. Thanks

---

