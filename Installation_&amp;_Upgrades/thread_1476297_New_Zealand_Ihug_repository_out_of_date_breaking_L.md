---
title: "New Zealand Ihug repository out of date breaking Lucid installs?"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Pathos_ on 2010-05-07
I've had all sorts of upgrade problems going to lucid from 9.10 via the Distribution upgrade system but I've got a working system now.

I use the New Zealand iHug repository and several of problems that I've had indicate that the lucid binaries are out of date (from March rather than the latest release)

Heres an example of a discrepancy:

[http://mirror.ihug.co.nz/ubuntu/pool/main/l/linux/?C=M;O=D]("iHug Linux Directory")
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/?C=M;O=D]("Archive.ubuntu.com Linux Directory")

I performed all upgrades available on the iHug repository and then when switching to archive.ubuntu.com I had 944 packages to upgrade.

I'm really worried that other ubuntu users in New Zealand may be finding the issues I had. First time I restarted my mouse and keyboard weren't working at the login screen. I had to go into recovery mode, remove openoffice due to some kind of cyclical dependency, then do a apptitude full-install to fix it.

---

### Post by zvacet on 2010-05-07
Stick with  archive.ubuntu.com or maybe some closer mirror.Probably it is just temporary server issue,but it is good you let it know.

> emove openoffice due to some kind of cyclical dependency

I believe it is called dependency hell.You  can solve it by installing all dependencies at once.For example

```
sudo apt-get install dep1 dep2 dep3
```

---

### Post by Pathos_ on 2010-05-08
> **zvacet said:**
> I believe it is called dependency hell.You  can solve it by installing all dependencies at once.For example

```
sudo apt-get install dep1 dep2 dep3
```

I'm not exactly sure what was going on but it happened when doing Aptitude Full-Upgrade. The old openoffice packages were all flagged for removal and the new ones were all flagged to be installed. Aptitude would bomb out every time.

---

### Post by byronical on 2010-05-14
Great to know as I had numerous problems after upgrading to lucid from the ihug mirror. Just noticed recently that some links at IHUG were giving 404 errors so changed my software source to [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) and redid the upgrade. Hopefully all will be well now.

---

### Post by lisati on 2010-05-14
I'm not sure which my machine is set to (possibly citylink), but there are other mirrors available in NZ. I haven't noticed any problems yet.

---

### Post by Pathos_ on 2010-05-26
I got a response from iHug (17th May - I haven't been checking my emails) and they have fixed a glitch in their script and the respository should be upto date.

:popcorn:

---

