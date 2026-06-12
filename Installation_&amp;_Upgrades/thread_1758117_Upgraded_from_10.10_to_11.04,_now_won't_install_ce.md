---
title: "Upgraded from 10.10 to 11.04, now won't install certain updates"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by Luthiensdad on 2011-05-14
This is my first time posting, just upgraded from 10.10 to 11.04 (downloaded, not installed from disc) and it seemed to go okay, but now whenever I try to check for updates I get the following failed/error message:

Failed to Download Repository Information

W:GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I have tried updating from both the US and the Main server. What do I need to do differently? thanks.

---

### Post by zvacet on 2011-05-15
PPA for xbmc doesn´t have Natty packages,so you can try to find new one,so you can remove this PPA from your source list.For medibuntu run in terminal

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

