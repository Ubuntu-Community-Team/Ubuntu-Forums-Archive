---
title: "VLC is broken on Lucid"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by grikdog on 2010-08-18
```
Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

Some index files failed to download, they have been ignored, or old ones used instead.
```

The only fix offered on the Videolan forum is to live "on the bleeding edge" and update to Maverick, where the VLC stuff now resides.  Lucid?  What's a Lucid?

I thought the idea of LTS was an agreement by all parties to provide a stable, supportable base so users know what to expect.  Apparently, it's called Windows 7, not Lucid.

---

### Post by bowens44 on 2010-08-18
> **grikdog said:**
> [CODE]Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found



You're not trying to get it from a standard repository. You're going to a  PPA. This is not a problem with lucid, it's a problem with the PPA. Remove the PPA from your sources list, refresh and install or wait for the PPA to be fixed.....

---

