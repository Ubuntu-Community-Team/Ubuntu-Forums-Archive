---
title: "Ubuntu 10.10 Update error"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by indranama on 2011-04-07
Hi all, 
When I try to update packages in my ubuntu 10.10, it checks the repos and finally give me the following error.

```
W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

I tried changing server location to USA also (I'm in Sri Lanka) but same error occurs.

Anyone know what is wrong?

---

### Post by mörgæs on 2011-04-07
There are some suggestions in this thread:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

Some people recommend simply booting the router and the machine as a first step.

---

