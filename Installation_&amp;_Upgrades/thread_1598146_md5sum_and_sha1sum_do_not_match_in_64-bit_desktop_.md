---
title: "md5sum and sha1sum do not match in 64-bit desktop edition!"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by rquin66 on 2010-10-16
Is it just me, or 64 bit desktop edition checksum do NOT match?

I've tried 32 bit edition and seems to be OK.

---

### Post by CharlesA on 2010-10-16
64-bit desktop edition matched for me.

You probably have a corrupted download.

---

### Post by rquin66 on 2010-10-16
I've tried (from the same PC) in ubuntu, kubuntu, fedora and windows7 and never get the right checksum for the 64-bit edition. It's weird... I'll try with a netbook I have to see waht happens.

---

### Post by CharlesA on 2010-10-16
How are you doing the md5sum or sha1sum?

Here are the ones I get from my ISO:

```
charles@thor:~/.VirtualBox$ md5sum ubuntu-10.10-desktop-amd64.iso
1b9df87e588451d2ca4643a036020410  ubuntu-10.10-desktop-amd64.iso
```

```
charles@thor:~/.VirtualBox$ sha1sum ubuntu-10.10-desktop-amd64.iso
ac7323b1f98d07583b59c2ace45e0e6102541467  ubuntu-10.10-desktop-amd64.iso
```

---

