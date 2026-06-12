---
title: "Can not Fetch"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by marcjboudreau on 2007-04-22
Hi All,

Have been reading the forums looking at all the problems that others are having upgrading to Feisty. I see some people are getting solutions here, but I haven't seen any help for this one yet.

Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

I'm not sure if this is due to server overload or if I've done something I shouldn't have. Anybody got any suggestions?

---

### Post by jpeddicord on 2007-04-23
Just reload your repositories (using Check in update manager) every now and then to get new, updated lists. Eventually, the problem will go away.
It is sometimes caused by a bad download, or even a corrupted mirror. Try changing mirrors from System > Administration > Software Sources to get an updated list.

Jacob

---

### Post by zvacet on 2007-04-24
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by marcjboudreau on 2007-04-24
Thanks for the responses. I've tried that line in the terminal but it hasn't worked, zvacet. 

As I've mentioned in this thread, I'm now getting a whole new error.

[http://ubuntuforums.org/showthread.php?t=420602](http://ubuntuforums.org/showthread.php?t=420602)

```

marc@marc-desktop:/$ sudo aptitude update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
```

I'm at a total loss for what I've done to do this. I've been trying to edit the sources list, but I can't see what the problem is.

---

