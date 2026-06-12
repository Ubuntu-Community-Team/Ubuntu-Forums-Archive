---
title: "[SOLVED] ltsp-build-client fails after 8.10 upgrade"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by lipinski on 2008-11-20
I performed an Upgrade from 8.04 to 8.10.

I am trying to rebuild my LTSP image via ltsp-build-client, however, it fails with the following:

dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ltsp-client:
 ltsp-client depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing ltsp-client (--configure):
 dependency problems - leaving unconfigured


The other errors I see during ltsp-build-client are:
debconf: unable to initialize frontend: Passthrough
debconf: (Failed to open fd 3: Bad file descriptor at (eval 22) line 3)
debconf: falling back to frontend: Noninteractive


Now I no longer have a working LTSP environment.  Please help.

---

### Post by lipinski on 2008-12-22
> **lipinski said:**
> I performed an Upgrade from 8.04 to 8.10.

I am trying to rebuild my LTSP image via ltsp-build-client, however, it fails with the following:

dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ltsp-client:
 ltsp-client depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing ltsp-client (--configure):
 dependency problems - leaving unconfigured


The other errors I see during ltsp-build-client are:
debconf: unable to initialize frontend: Passthrough
debconf: (Failed to open fd 3: Bad file descriptor at (eval 22) line 3)
debconf: falling back to frontend: Noninteractive


Now I no longer have a working LTSP environment.  Please help.

Figured out the problem.  Well, how to get around it anyways.

This problem was specific to my configuration because I configure /opt to be a symlink to /usr/local/opt.  Once I replaced the /opt symlink with an actual directory /opt, ltsp-build-client was successful.

(Afterwards, I moved the contents of /opt to /usr/local/opt, and recreated the /opt -> /usr/local/opt symlink)

Hopefully this will still get fixed in ltsp.

---

