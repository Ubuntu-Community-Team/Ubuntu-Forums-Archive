---
title: "errors with updating"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by lonelypauly on 2006-11-21
ive seen this at least half a dozen times when i update...is any of this important?

> Reading package lists... Error!
W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
E: Dynamic MMap ran out of room
E: Error occurred while processing xserver-xephyr (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


---

### Post by ReaderRat on 2006-11-21
You can't get stuff from the repos without a public key:
KEY Public HowTo get
          **[http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773](http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773)**

---

### Post by lonelypauly on 2006-11-22
thats it eh? and i thought i screwed something up.  thank you :)

---

