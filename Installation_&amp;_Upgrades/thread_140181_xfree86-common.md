---
title: "xfree86-common"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by infinitee on 2006-03-05
Hi,
One of my apt-get update got me into this error. I googled and checked forums (here and also Debian) but could not get a fix. Could someone please help?

```

Setting up xfree86-common (6.8.2-10.1) ...
update-rc.d: /etc/init.d/xfree86-common exists during rc.d purge (use -f to force)
dpkg: error processing xfree86-common (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 xfree86-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

regards,
Pavan

---

### Post by christhemonkey on 2006-03-05
I think this is just saying that there is already a script in /etc/init.d/
that refers to xfree86, try manually removing it mayhaps?
or better idea just renaming it to somwething like xfree86-common.old

---

### Post by knalle on 2006-03-05
[QUOTE=infinitee]

```

update-rc.d: /etc/init.d/xfree86-common exists during rc.d purge (use -f to force)

```

regards,
Pavan[/QUOTE]

try to -f to force it, looks like you got a dirty package that has been removed but not purged

---

### Post by infinitee on 2006-03-06
thanks, but -f option didnt work, but I just removed and installed it again, and updating/upgrading doesnt produce those error messages again.

thanks,
Pavan

---

