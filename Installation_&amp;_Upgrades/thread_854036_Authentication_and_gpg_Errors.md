---
title: "Authentication and gpg Errors"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by reZo on 2008-07-09
I have two problems, the first with update-manager. When I go to upgrade, it says:

```

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2: Hash Sum mismatch

```

How can I resolve this issue?

The second (CLI, apt-get update):

```

Fetched 58.7kB in 11s (5217B/s)                                                                                                                               
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2  Hash Sum mismatch
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

As you can see, I'm using Gusty.

I haven't used this box in about 6 months, and have recently upgraded it so it's operational again.

Thanks,

---

### Post by zvacet on 2008-07-09
This should fix it 

```
sudo apt-get update && sudo apt-get upgrade
```

---

