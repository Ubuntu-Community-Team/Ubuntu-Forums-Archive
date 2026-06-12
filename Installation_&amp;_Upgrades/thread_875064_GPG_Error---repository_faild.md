---
title: "GPG Error---repository faild"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by shamshir48 on 2008-07-30
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

This error pops up when i try to update my system


anyone to help!

---

### Post by zvacet on 2008-07-30
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Pumalite on 2008-07-30
Double post:
[http://ubuntuforums.org/showthread.php?t=874675](http://ubuntuforums.org/showthread.php?t=874675)

---

