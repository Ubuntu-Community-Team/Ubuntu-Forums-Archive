---
title: "Problem upgrading from 9.10 to 10.04 via update manager"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by diablonstuff on 2013-02-26
Hi all.

I am trying to update an old laptop through the update manager from Ubuntu 9.10 to Ubuntu 10.04.3.  When I try and do this, I am getting an error that stops the update.

```
W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  main&nbsp;/binary-i386/Packages in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  Unable to find expected entry  main&nbsp;/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

It looks to me like it is looking for us.archive.ubuntu.com when it should be looking for old-releases.ubuntu.com.  Of course I could be completely off track here.  Please some one help.  I want to get this laptop up to date.  Thanks a lot.

---

### Post by SuperFreak on 2013-02-26
I believe 10.04, 10.10, 11.04 are no longer supported platforms

---

### Post by diablonstuff on 2013-02-26
I think you are right, but does that mean that there is no way of updating with the update manager? I would think that there would still be some legacy support.

---

### Post by SuperFreak on 2013-02-26
That I do not know, but there will be no updates if you can install it. ie update manager will not install  Security updates for an OS that is no longer supported.
If it is an issue of not having the hardware to run the latest version you could install Xubuntu or Kubuntu. 12.04 is the latest version of Ubuntu that is LTS (and is supported till 2017.12.04 comes in Xubuntu or Kubuntu versions.

---

### Post by diablonstuff on 2013-02-27
It's not that I can't run the new system. It's just that update manager makes you upgrade in steps. I was just hoping to be able to update without having to wipe the drive and doing a clean install

---

### Post by Topsiho on 2013-02-27
I think the only sensible thing to do is to do the clean install. You are lucky that the point-release 12.04.3 has just (somewhere mid february) been released, so after installing this you will not be confronted with a too large load of updates.

When you do a clean install, and if you don't want to loose your personal files, you must back these up (double-dutch for backup these), to later put them back into your home map.

Doing all kinds of things to only end up with an obsolete and not supported version of Ubuntu is, well, is not very advisable :)

Please consider putting your /home into it's own partition, that helps with a future clean install.

Topsiho

---

### Post by diablonstuff on 2013-02-27
I never thought of putting my /home in its own partition, but that is a really good idea.  Thanks.  I guess I will just have to do the clean install.  At least that will be faster than waiting for update manager to do it.  Will mark as solved.

---

