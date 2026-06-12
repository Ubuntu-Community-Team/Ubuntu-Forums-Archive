---
title: "Can't upgrade from Gutsy to Hardy"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by dualscreenman on 2008-01-31
I'm on Kubuntu 7.10. When I run update-manager -d everything chugs along nicely until a popup with this error appears.


Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release](http://archive.canonical.com/ubuntu/dists/hardy/Release) Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file (malformed Release file?)

It then restores itself to pre-update conditions.

Something like this had happened to me with Gutsy, but I had installed Gutsy from Tribe 3 or something and the updates got me almost to a final release. And the Tribe 5 -> final upgrade did finally work.

So I'd like to update to the latest Kubuntu alpha, any help appreciated.

---

### Post by taurus on 2008-01-31
Why don't you edit /etc/apt/sources.list and comment out that repo, canonical, for now.  Maybe they have not activated a repo for Hardy, yet.

---

### Post by dualscreenman on 2008-01-31
I was able to upgrade by replacing all instances of gutsy with hardy in my sources.list file, and commenting out the commercial repos. Then, I manually upgraded with apt-get dist-upgrade

---

