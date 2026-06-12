---
title: "Upgrade error"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by fabiocunha on 2010-10-11
I'm trying to upgrade and this appears:

: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 2

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release: The following signatures were invalid: NODATA 2
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg)  Error reading from server - read (104: Connection reset by peer) [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release](http://archive.canonical.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


Anyone have any ideas?

---

### Post by mörgæs on 2010-10-11
You could try opening Software Sources and select another server.

---

