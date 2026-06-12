---
title: "PXE boot setup *without* NFS"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Digimer on 2010-06-29
Hi all,

  I'm trying to sort out the magical incantation to get Ubuntu 10.04 to boot from a PXE server. Ideally, this would boot in a similar manner as had I booted off the live CD. Is this possible?

  I don't want to use NFS, but I do have all the ISO files available via an http server. I'm doing this to match the existing Fedora/CentOS/RHEL images already hosted on the PXE server.

  If anyone can provide a pointer, I'd be much appreciated!

Digimer

---

### Post by ppatrick on 2013-02-23
You can do that with Serva,
It installs all the big distros with CIFS (MS Share) or HTTP

Including the live versions of Ubuntu LTS 12.04, Ubuntu 12.10 etc.

See here
[http://vercot.com/~serva/an/NonWindowsPXE3.html](http://vercot.com/~serva/an/NonWindowsPXE3.html)

---

