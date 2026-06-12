---
title: "System Package Manager Error"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by Enigmacat on 2008-10-20
I recently added the medibuntu repository and I get this error message:

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


What on earth does this mean? I am a noob, though an advanced noob, so if you can keep it simple for me I'd appreciate that.

---

### Post by meho_r on 2008-10-20
That means that Medibuntu's public key isn't available so packages can't be verified (but can be installed). Just a warning, not a big deal at all. To add/install it just run this command in terminal:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Refer to Medibuntu page for infos (section: "Adding the Repositories", at the end of it): [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Enigmacat on 2008-10-20
Gee, thanks. ):P  That did it! No more error messages. Cool! :lolflag:

---

### Post by 22flames on 2008-10-20
Please mark this thread solved it will clean up people looking to help :)

22FLAMES

---

