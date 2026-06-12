---
title: "What to do when Update Manager fails?"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by phflupp on 2008-11-14
Recent updates failed as follows:

E: /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.33_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./lib/firmware/2.6.24-21-generic/ipw2200-ibss.fw')
E: /var/cache/apt/archives/libmysqlclient15off_5.0.51a-3ubuntu5.3_amd64.deb: corrupted filesystem tarfile - corrupted package archive

...if "Check" re-downloads then the file on the server seems corrupt. If "Check" does not re-download, how do I repeat the download in Update Manager?

Thx,
-P.
ps: a little more easy-to-reach documentation on Update Manager would be helpful :-)

---

### Post by inobe on 2008-11-14
open synaptic, click edit > fix broken packages .

---

### Post by phflupp on 2008-11-19
Nope... the following does not show as a broken package and the command appears to have no effect.

I still get the following error:

E: /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.33_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./lib/firmware/2.6.24-21-generic/ipw2200-ibss.fw')

Suggestions?

Thx in advance!
-P.
:(

---

### Post by phflupp on 2008-11-21
Ok... not very user-friendly (unless you're an ex sys admin), but I was able to find the download, open a terminal window to delete it, and then Update Manager downloaded a new copy which worked.

Now, why can't Update Manager delete and re-download on its own when such problems occur? Someone might want to add this to a list of enhancements for Update Manager.

Cheers!
-Phflupp

---

### Post by steveneddy on 2008-11-21
Ok

---

