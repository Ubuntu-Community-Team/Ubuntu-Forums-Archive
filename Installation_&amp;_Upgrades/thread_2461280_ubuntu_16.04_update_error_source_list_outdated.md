---
title: "ubuntu 16.04 update error: source list outdated"
date: 2021-04-27
forum: Installation &amp; Upgrades
---

### Post by dadata on 2021-04-27
Hello all,
Greetings.
I have not managed to update internet for sometimes.

```

Step 1: sudo apt-get update. below is part of output.

W: Failed to fetch https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu/dists/xenial/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F01618A51312F3F
W: Failed to fetch http://ppa.launchpad.net/octave/stable/ubuntu/dists/xenial/InRelease  Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
W: Failed to fetch http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/xenial/InRelease  Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
W: Failed to fetch https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04/Release.gpg  The following signatures were invalid: KEYEXPIRED 1535386001
W: Failed to fetch http://debian.neo4j.org/repo/stable/Release.gpg  The following signatures were invalid: KEYEXPIRED 1572135620
E: Failed to fetch http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu/dists/xenial/main/dep11/icons-64x64.tar  404  Not Found [IP: 91.189.95.85 80]
E: Failed to fetch http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu/dists/xenial/main/binary-amd64/Packages  403  Forbidden [IP: 91.189.95.85 80]
E: Failed to fetch http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu/dists/xenial/main/binary-amd64/Packages  403  Forbidden [IP: 91.189.95.85 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
E: The package lists or status file could not be parsed or opened.
```

Can I delete the source files and create a new one? any help much appreciated?
In /etc/apt/sources.list, there are two files:
1. source.list
2. source.list.d
which one to work on?

---

### Post by Xian on 2021-04-27
If you want to hand-edit your distro-specific repo source list the correct file is /etc/apt/sources.list

The sources.list.d folder should contain individual user-added repos that may also need to be updated.

---

### Post by Impavidus on 2021-04-28
source.list is a file with standard software sources. source.list.d is a directory with additional source lists.

Ubuntu 16.04 reaches end of life this week. Your software sources will no longer work (some PPAs have already stopped working). I suggest you plan an upgrade. A fresh install of 20.04 may be cleanest.

---

