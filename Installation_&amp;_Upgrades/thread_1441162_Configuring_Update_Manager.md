---
title: "Configuring Update Manager"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by George Heine on 2010-03-28
Working with Ubuntu 9.04.  
Today the Update Manager window shows that there are updates available for the
following, all involving Samba:

libsmbclient
libwbclient
samba-common
smbclient

I don't use Samba and don't ever plan to.  How do I configure Update Manager so that it doesn't  send me unnecessary updates?

---

### Post by MichaelSammels on 2010-03-28
I believe that the samba-common come with all Ubuntu installs, but you could try opening Synaptic Package Manager (System -> Administration), search for and remove all Samba related packages.

---

### Post by Enigmapond on 2010-03-28
Right or..

```
sudo apt-get purge libsmbclient libwbclient samba-common smbclient
```

---

