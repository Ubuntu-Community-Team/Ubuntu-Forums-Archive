---
title: "Spurious noise from popularity-contest / package problems"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by professorYaffle on 2012-02-05
I'm running fully updated AMD64 oneiric (which was upgraded from maverick a while back.)

Once a week I get an e-mail from the system (which, in itself is a bit weird as it comes from the cron.daily job, not cron.weekly) with some complaints from the package popularity contest. It says this:

> Subject: Anacron job 'cron.daily' on raven
Date: Fri,  3 Feb 2012 08:24:57 +0000 (GMT)

/etc/cron.daily/popularity-contest:
Package `flashplugin-downloader' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `ia32-libs-multiarch' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `nspluginviewer' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `qdbus' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
However, I *do* have those packages installed and (as far as I know) working. The packages on the system, however all have a ':i386' at the end of their names (and in most cases synaptic can't find a package of that name without the :i386 ending. So what's popularity-contest going on about? Is there something leftover from a previous distribution than needs purging or something? Other than turning it off completely how do I shut it up? Any ideas?

---

