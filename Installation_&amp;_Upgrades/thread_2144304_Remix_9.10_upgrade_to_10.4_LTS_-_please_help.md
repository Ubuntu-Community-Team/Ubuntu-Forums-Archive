---
title: "Remix 9.10 upgrade to 10.4 LTS - please help"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by distortedecho on 2013-05-11
Hi all.

Was wondering if you could please advise what is going wrong with my Ubuntu 9.10 re-install?

After a failed upgrade from 10.4 to latest, I decided to re-install.
I only have the 9.10 disk working, 10.4 wouldn't boot.

I thought, "no bother, I'll install 9.10 and upgrade" - but it's just not possible. :(

I can't install anything from Software Centre. And all the servers I choose, fail to update/upgrade.
This is what I get:

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.156 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

Can anybody please advise how I can either stay on 9.10 and install software, or upgrade to 10.4 LTS?

Many thanks.

---

### Post by ibjsb4 on 2013-05-11
Like 9.10, 10.04 has also reached end of life and no longer supported through normal channels.  I think you would be better off with a fresh install of 12.04, its LTS and supported till 2017.

Or maybe Xubuntu if your running an older box.

---

### Post by distortedecho on 2013-05-13
OK, will do that then, Thanks.

Shame it can't be done from within 9.10 easily: [http://askubuntu.com/questions/144673/how-can-i-upgrade-to-ubuntu-12-04-from-clean-install-of-9-10](http://askubuntu.com/questions/144673/how-can-i-upgrade-to-ubuntu-12-04-from-clean-install-of-9-10)

Burning .iso now.

---

### Post by papibe on 2013-05-13
Hi distortedecho.

[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to mark a thread as solved.

Regards.

---

### Post by ibjsb4 on 2013-05-13
Papibe, you got the right thread this time ? :p

---

