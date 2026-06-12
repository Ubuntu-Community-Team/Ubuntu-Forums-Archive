---
title: "Videolan servers are down &gt; installing libdvdread4 currently fails"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by bapoumba on 2014-12-21
[https://forum.videolan.org/viewtopic.php?f=13&t=123251](https://forum.videolan.org/viewtopic.php?f=13&t=123251)

---

### Post by monkeybrain20122 on 2014-12-21
It is working here.

---

### Post by bapoumba on 2014-12-21
> **monkeybrain20122 said:**
> It is working here.
Ah, I just tried to run the install script and it fails with a 404 :

```
~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2014-12-21 21:06:14--  http://download.videolan.org/pub/debian/stable//Packages
Resolving download.videolan.org (download.videolan.org)... 195.154.236.203, fe80::be30:5bff:fed0:40f9
Connecting to download.videolan.org (download.videolan.org)|195.154.236.203|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: unspecified
ERROR: Redirection (301) without location.
Dynamic fetch failed; Falling back to static fetch
--2014-12-21 21:06:14--  http://download.videolan.org/pub/debian/stable/libdvdcss2_1.2.13-0_i386.deb
Resolving download.videolan.org (download.videolan.org)... 195.154.236.203, fe80::be30:5bff:fed0:40f9
Connecting to download.videolan.org (download.videolan.org)|195.154.236.203|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2014-12-21 21:06:14 ERROR 404: Not Found.

```
Edit : ran the script once again just now, same error. I can install the other way, but I'm not that on a rush.

---

### Post by bapoumba on 2014-12-23
Working now, they must have fixed their faulty server hard drive :)

---

