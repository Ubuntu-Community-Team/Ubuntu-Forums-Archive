---
title: "I want my delta debs"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Miguel on 2010-04-22
Dear all,

I just ran an update this evening when I came home, and lo and wonder, after the RC unfreeze there were several updates. It turns out one of them was a texlive update, and I got a full texlive updated install. This accounted for most of the 462 Mb in packages I had to download. Curious about what would trigger a texlive update, I got this:

```

$ cat /usr/share/doc/texlive-latex-extra/changelog.Debian.gz | gunzip | head -n 8
texlive-extra (2009-7ubuntu3) lucid; urgency=low

  * debian/control: Drop purifyeps from texlive-extra-utils'
    Recommends to Suggests; purifyeps and a bunch of dependencies are
    in universe.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Thu, 22 Apr 2010 09:44:10 +0000

```

Oh, cool. 400 Mb downloaded in order to change some rules from "recommends" to "suggest". Very cool. I mean, in the four months I've been living in london, it seems that broadband and beer are the only affordable things. Nevertheless, it must be bad (c) for the environment and for Canonical having to support such downloads just because a small rule change. 

I really think that delta debs should be implemented as fast as possible, for both Debian and Ubuntu. I can't think it makes any kind of economic sense the way it works now. I mean, if for some chance you change a small bit in nautilus, another one in openoffice and another one in texlive, you may end up forcing 500 Mb of updates on your users for what could essentially be a 200 kB update. Such an unnecessary hammering of the servers make my head hurt.

EDIT: As a plus, delta debs may make life bearable on dialup users, as well as people with restricted download quota.

---

### Post by psyke83 on 2010-04-22
Total agreement here.

Delta updates are already used in recent Windows releases, and Fedora has its own RPM-based implementation: [http://fedoraproject.org/wiki/Releases/FeaturePresto](http://fedoraproject.org/wiki/Releases/FeaturePresto)

---

### Post by VMC on 2010-04-22
This is one of the rare gems as far as topics go here on testing!

I couldn't agree more. Oddly I was thinking about this very idea and what was it called in Red Hat or Fedora or whoever implements this, just when I booted up. If they can do it how come we can't?!

---

### Post by cariboo on 2010-04-22
I would suggest you check [Brainstorm]("http:///brainstorm.ubuntu.com/"), to see if anyone has created something about delta debs, as whiprush checks the ideas before UDS and creates a digest for the devs to look at during the conference.

---

### Post by 23meg on 2010-04-22
> **cariboo907 said:**
> I would suggest you check [Brainstorm]("http:///brainstorm.ubuntu.com/"), to see if anyone has created something about delta debs, as whiprush checks the ideas before UDS and creates a digest for the devs to look at during the conference.

No need; there's already an approved blueprint for this, but it got deferred as it was deemed too risky for Lucid.

[https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)

---

### Post by Miguel on 2010-04-22
OK, I've had a look and it's one of the very first brainstorm ideas proposed:

[http://brainstorm.ubuntu.com/idea/13/](http://brainstorm.ubuntu.com/idea/13/)

I had already heard about "Delta rpms", which from Psyke's link it seems the correct name is "presto". This all makes it more painful. I understand it can be difficult, like, I don't know, applying 3 patches over a binary file. Indeed, that doesn't sound very healthy. But there must be a way to implement it in a robust way. 

Perhaps make it so that if more than three patches have to be applied, the full package will be downloaded, or implementing a checksum of the altered files to more or less guarantee integrity.

---

### Post by splicerr on 2010-04-22
Might also think about introducing delta package lists. Just ran update-manager to check for updates, ifconfig says I downloaded ~11MB just to get the package lists. For me it's not a problem, but if you are on mobile and pay by the MB or have a slow connection.

---

### Post by Miguel on 2010-04-22
> **splicerr said:**
> Might also think about introducing delta package lists. Just ran update-manager to check for updates, ifconfig says I downloaded ~11MB just to get the package lists. For me it's not a problem, but if you are on mobile and pay by the MB or have a slow connection.

This has been in Debian testing for aaages. I heard some arguments against it in ubuntu is that in Debian packages are synchronised twice a day, while in ubuntu they aren't. Apparently, this makes it more difficult to create incremental package lists.

---

### Post by Rubicon_82 on 2010-04-22
This idea has my total support.

I've just run into the identical issue that the OP has described with TeX Live.  I'm also one of the people with a very small monthly data quota ( < 10 GB), so I really dislike downloading 500 MB for the sake of a 500 byte addition to a changelog file.  For the time being I've pinned the offending packages at their old versions.

I have also observed this type of behaviour with the kdebase-workspace-* line of packages, where a small alteration to a recommended dependency in the kdebase-workspace package results in downloading several hundred megabytes of essentially unchanged files.

[quote=Miguel]Perhaps make it so that if more than three patches have to be applied, the full package will be downloaded, or implementing a checksum of the altered files to more or less guarantee integrity.[/quote]

How difficult would it be to implement rsync or zsync backends to apt-get?

Using zsync (instead of rsync) would cause less load on the repository servers.  Given that there will usually be a copy of the old package in /var/cache/apt/archives/, the bandwidth requirement will probably be similar to providing an actual delta-deb file.  I know that Ubuntu currently maintains zsync support for the CD images, so it shouldn't be too difficult to implement zsync on the server side for the packages/ package lists.

---

### Post by psyke83 on 2010-04-22
> **splicerr said:**
> Might also think about introducing delta package lists. Just ran update-manager to check for updates, ifconfig says I downloaded ~11MB just to get the package lists. For me it's not a problem, but if you are on mobile and pay by the MB or have a slow connection.

I'm all for reducing bandwidth, but let's clear something up:

During the development release you will download ~11MB of package lists each time the repository is updated, but after the final release it is typically a few hundred kilobytes and nothing more. Why? Because the main repository is frozen and all further updates go into the updates/backports/security (etc.) repositories.

---

### Post by Longinus00 on 2010-04-22
> **Rubicon_82 said:**
> ...

Read 23meg's post.

---

### Post by VMC on 2010-04-22
> **23meg said:**
> No need; there's already an approved blueprint for this, but it got deferred as it was deemed too risky for Lucid.

[https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)

Thanks. I've subscribed.

zsync has saved me a lot of ms's over the life-cycle of testing.

---

### Post by Miguel on 2010-04-23
The blueprint link is interesting. There are also two links towards benchmarks performed in [Jaunty](https://wiki.ubuntu.com/AptSyncInKarmicSpec/JauntyBenchmark) (from clean ISO install to current patchset) and a dist-upgrade to [Karmic](https://wiki.ubuntu.com/AptSyncInKarmicSpec/KarmicBenchmark). I'd like to know why OOo is not apt-syncable. Is there any obscure reason or is it just because the packages are using lzma or bz2 compression? In any case, it is very interesting to see how even in a full upgrade from Jaunty to Karmic you do save 43% of the bandwidth. And I fear that once you have many data packages, that percentage will only improve.

Does anybody know or have a good idea of how many packages use gzip compression instead of lzma or bz2? If having apt-sync requires gzip for all the packages, we might lose some effective space in the CD.

---

### Post by Starks on 2010-04-25
[http://brainstorm.ubuntu.com/idea/13/](http://brainstorm.ubuntu.com/idea/13/)
[https://bugs.launchpad.net/ubuntu/+bug/39416](https://bugs.launchpad.net/ubuntu/+bug/39416)
[https://wiki.ubuntu.com/apt-sync](https://wiki.ubuntu.com/apt-sync)
[http://fedoraproject.org/wiki/Releases/FeaturePresto](http://fedoraproject.org/wiki/Releases/FeaturePresto)

Every release cycle save for this one, the issue of smaller, change-based upgrades is brought up.

This needs to happen for the next release.

---

### Post by ElSlunko on 2010-04-25
Hear hear. Or is it here here.

---

### Post by Rubicon_82 on 2010-04-25
> **Miguel said:**
> I'd like to know why OOo is not apt-syncable. Is there any obscure reason or is it just because the packages are using lzma or bz2 compression?

You're right.  The OOo packages (at least for Lucid) use lzma compression for the data tarball in the deb package.

> 
Does anybody know or have a good idea of how many packages use gzip compression instead of lzma or bz2? If having apt-sync requires gzip for all the packages, we might lose some effective space in the CD.

You can use 'ar' to list the contents of the deb package.  Try running the following:
```

find /var/cache/apt/archives/ -iname "*.deb" -exec ar -t '{}' \; | grep data.tar.gz | wc -l

```

I think you'll find that many of the packages normally present on the Live CD will be using lzma or bz2 compression.  As the current images are very close to 700 MiB in size, it wouldn't be possible to change back to gzip compression.  You'd have to remove some of the packages from the CD, which I can't see happening.

---

### Post by tomcat025 on 2010-04-26
> **ElSlunko said:**
> Hear hear. Or is it here here.

You were correct the first time. It is hear hear. =D

---

### Post by psyke83 on 2010-04-26
I'm in complete agreement. Let me just point out, however - there's a recent thread already discussing this. Let's not fragment the conversation - can the mods please merge threads?

[http://ubuntuforums.org/showthread.php?t=1460414](http://ubuntuforums.org/showthread.php?t=1460414)

---

### Post by autumnraine on 2010-04-26
Yes, definitely! 

Example of why: this distribution bears a name of African origin, yet Africa is not exactly a hotbed of high-speed connections - having updates that only downloads the bits that have changed would make life so much easier for people with slow Internet connections.

---

### Post by 23meg on 2010-04-26
Threads merged.

---

### Post by iponeverything on 2010-04-26
I agree entirely. I am living where bandwidth is limited and expensive. I can get a good 3g data connection, but for $60 US a month and 5 gig/month limit. I can't afford to blow three days of bandwidth.

Usually the only updates I do on a regular basis are firefox and flash.

---

