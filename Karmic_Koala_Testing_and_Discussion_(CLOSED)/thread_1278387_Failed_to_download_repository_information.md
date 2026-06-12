---
title: "Failed to download repository information?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thegodsquirrel on 2009-09-29
For a while now I have been receiving this error when doing an update whether in the Terminal or using Update Manager. At first I thought I had a bad Third Party Repo that wasnt working, however upon disabling all these repo's still error still remained.  Perhaps someone has some insight to the reason for this error???

Any help would be appreciated


W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1DABDBB4CEC06767, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/Release](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/Release)  Unable to find expected entry  main'/binary-i386/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sooperspook on 2009-10-06
I get something similar.

Failed to download repository information.
Check your internet connection.

Details:
W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

My net connection is fine though.

Any ideas?

---

### Post by drs305 on 2009-10-06
sooperspook,

Try again in a few minutes. Sometimes this happens as the repository files are updated.

I just tried the server you are using and am getting the same message. If you are in a hurry, try a different server. Mine in the US worked fine.

---

