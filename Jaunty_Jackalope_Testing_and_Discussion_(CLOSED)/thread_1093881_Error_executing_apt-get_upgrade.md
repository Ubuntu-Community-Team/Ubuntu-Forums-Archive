---
title: "Error executing apt-get upgrade"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eprenen on 2009-03-12
I'm unable to execute 'sudo apt-get upgrade' in Jaunty.

Error message:

dpkg: parse error, in file `/var/lib/dpkg/available' near line 12724 package `libpango1.0-common':
 EOF during value of field `Suggests' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)

The file /var/lib/dpkg/available seems to be incomplete.

Ideas how to repair?

Thanks,

Eric

---

### Post by mcla0203 on 2009-03-12
Hi, so I see this in my /var/lib/dpkg/available file.  My upgrade functionality seems to work fine.  Take a look at the line with "Suggests:" after the "Package: libpango1.0-common" line.  Make sure there is a new line after all of the "Suggests:" i.e., before "Conflicts:" starts, there should be a new line for "Conflicts:".


```
14513 Package: libpango1.0-common
...
...
...
14524 Suggests: ttf-kochi-gothic, ttf-kochi-mincho, ttf-thryomanes, ttf-baekmuk, ttf-arp      hic-gbsn00lp, ttf-arphic-bsmi00lp, ttf-arphic-gkai00mp, ttf-arphic-bkai00mp
14525 Conflicts: pango-libthai (<< 0.1.6-2)
```

If thats way off you may have to show your /var/lib/dpkg/available file.

---

### Post by eprenen on 2009-03-12
Solved it. This is the way to do it, as the /var/lib/dpkg/available file was corrupt.

> sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.oldBusted
> sudo touch /var/lib/dpkg/available
> sudo apt-get update
> sudo apt-get upgrade

Thanks all.

Eric

---

