---
title: "Error messages while updating my source.list"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by newyilang on 2008-05-06
I typed "[COLOR="Blue"]sudo apt-get update[/COLOR]" to update my source.list. But I always get the following message:

[COLOR="Blue"]W: Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://mirror.rootguide.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://mirror.rootguide.org/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2](http://mirror.rootguide.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/hardy/main/source/Sources.bz2](http://mirror.rootguide.org/ubuntu/dists/hardy/main/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://mirror.rootguide.org/ubuntu/dists/hardy/restricted/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/hardy/universe/source/Sources.bz2](http://mirror.rootguide.org/ubuntu/dists/hardy/universe/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://mirror.rootguide.org/ubuntu/dists/hardy/multiverse/source/Sources.bz2](http://mirror.rootguide.org/ubuntu/dists/hardy/multiverse/source/Sources.bz2) Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead. [/COLOR]

What is wrong? and how to solve the problem? Thanks!

---

### Post by Pumalite on 2008-05-06
Are you 'updating' or 'upgrading'?
If you are upgrading, you need to remove all third parties from your /etc/apt/sources.list

---

### Post by lilkeith07 on 2008-05-06
I just did a clean install of 8.04 and went to update and got these same errors.

---

### Post by Pumalite on 2008-05-06
I've had 15 updates today. All flawless.

---

### Post by Aearenda on 2008-05-13
Here's a possible solution for the original poster:
[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)

---

