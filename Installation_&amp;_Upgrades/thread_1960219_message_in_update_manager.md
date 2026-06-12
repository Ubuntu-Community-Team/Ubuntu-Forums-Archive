---
title: "message in update manager"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by VsetSunder on 2012-04-17
This is the message I get update old by 23 days, please update. When trying through terminal this is the message in terminal, please guide.
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)

---

### Post by darkod on 2012-04-17
It sounds like that extras repository for precise has changed something, maybe the GPG key. It's still in development so maybe they changed something, or it got corrupted.

Try deleting that repository and add it again, or similar. It is only the extras repository, not all of them.

---

### Post by darkod on 2012-04-17
PS. The development version of ubuntu has a separate forum for problems that were discovered during testing the Beta/Alpha.
It's here:
[http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)

---

### Post by Frogs Hair on 2012-04-17
If you are running 12.04 with no updates for 23 days be prepared for hundreds of them. See the link . [http://naveenubuntu.blogspot.com/2011/08/fixing-gpg-keys-in-ubuntu.html](http://naveenubuntu.blogspot.com/2011/08/fixing-gpg-keys-in-ubuntu.html)

---

