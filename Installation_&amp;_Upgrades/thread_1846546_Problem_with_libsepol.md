---
title: "Problem with libsepol"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by Legendante on 2011-09-19
Hi there,

I'm in the process of upgrading my server from Hardy. I managed to get all the way to Karmic when I ran into the following issue. Anything I try with apt-get, aptitude or dpkg gives me the following error

```
dpkg: error processing libsepol1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libsepol1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I've tried to re-install libsepol but it fails for the same reason.

Anybody able to give me a direction to go in? This is a production server though so I don't have physical access to it and would really not have to do a clean install

---

