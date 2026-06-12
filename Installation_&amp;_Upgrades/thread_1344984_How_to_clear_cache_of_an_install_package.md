---
title: "How to clear cache of an install package"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by TennTux on 2009-12-03
Since nobody seems to be answering my larger issue, I figured I'd break out one of my smaller questions that may help me find the issue.

When I uninstall Eclipse with the clean option and then reinstall it, it does not download the package, it just installs from cache.

I generally use Synaptic but do not see an option to removed the downloaded install package. Am I missing something?

I am willing to use apt-get if it will help, however, all I can see is apt-get clean which I believe will remove every package not just the specific one(s) I want to clear. Is there another way? Or do I have to remove every one?

---

### Post by i.r.id10t on 2009-12-03
apt-get clean

And then apt-get update

And then apt-get install eclipse

---

### Post by Bjalf on 2009-12-03
go to **/var/cache/apt/archives** and delete it?

---

### Post by TennTux on 2009-12-04
I was able to clear the cache by deleting files from /var/cache/apt/archives by using Bjlaf('s) suggestion.

I still have work to do on my larger issue, but Thanks for this help.

---

