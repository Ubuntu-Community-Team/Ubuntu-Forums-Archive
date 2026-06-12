---
title: "[SOLVED] Error while automaticly updating."
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by wenuswilson on 2008-07-08
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

with this in the textbox

> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

i am connected to the internet so that doesn't seem to be the problem.
an exclaimation icon keeps appearing in my toolbar and when I check for updates this is what happens.

anybody know what's wrong?

---

### Post by pofigster on 2008-07-08
I've never actually gotten an upgrade over the internet to work.  Something is always screwed up.  I've chosen to instead make a separate /home partition so I can just do a fresh install.  It's a pain, but, not as bad as it has been for me upgrading the "normal" way.

---

### Post by avtolle on 2008-07-08
That repository is for Edgy, support for which ended IIRC in April this year. If you are running 8.04 (or 7.04 or 7.10), you should edit your /etc/apt/sources.list and either comment out the line that refers to that repository by placing a # before it, or you might delete it. If you are still running 6.10, you should upgrade. HTH.

---

### Post by zvacet on 2008-07-08
@ **wenuswilson**

In your source list replace **archive.ubuntu.com** with **old-releases.ubuntu.com**

```
sudo apt-get update && sudo apt-get upgrade
```

After that you will be able to upgrade to Feisty.Maybe it is better solution to install Hardy.

---

### Post by wenuswilson on 2008-07-09
> **zvacet said:**
> @ **wenuswilson**

In your source list replace **archive.ubuntu.com** with **old-releases.ubuntu.com**

```
sudo apt-get update && sudo apt-get upgrade
```

After that you will be able to upgrade to Feisty.Maybe it is better solution to install Hardy.

Way odd -- using Hardy, and have been since it came out.



[Solved] I fore some reason had an edgy universe or multiverse -- I added for some reason and then forgot about it.

---

