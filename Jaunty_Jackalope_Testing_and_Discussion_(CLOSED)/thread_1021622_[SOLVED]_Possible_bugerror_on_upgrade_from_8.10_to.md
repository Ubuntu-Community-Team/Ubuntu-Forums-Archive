---
title: "[SOLVED] Possible bug/error on upgrade from 8.10 to 9.04"
date: 2008-12-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by acebrain01 on 2008-12-25
W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  Unable to find expected entry  partner/binary-amd64/Packages in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  Unable to find expected entry  partner/binary-amd64/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
:confused::confused:

---

### Post by mejy on 2008-12-25
> **acebrain01 said:**
> W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  Unable to find expected entry  partner/binary-amd64/Packages in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  Unable to find expected entry  partner/binary-amd64/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
:confused::confused:

This isn't really a bug - these lines correspond to post-release updates, which are obviously not applicable to Jaunty since it has not yet been released.  If you disable security and updates in Administration -> Software Sources these errors should go away.

---

### Post by acebrain01 on 2008-12-25
Working now and thanks. this is my first upgrade, so i didn't know.

---

