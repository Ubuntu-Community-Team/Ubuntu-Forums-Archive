---
title: "Upgrade Ubuntu 18.04 to 20.04 ... short report"
date: 2021-12-29
forum: Installation &amp; Upgrades
---

### Post by megalonyx on 2021-12-29
This is not a question, just a short report of the experiences I made.

Few days ago I upgraded our server OS 18.04 using "do-release-upgrade" to 20.04. Easy, fast (approx. 30 minutes), successful, but with one unexpected result. After the installation finished, some parts of PHP7.2 were missing and MySQL5.7 was removed nearly completely. Instead, the upgrade installed PHP8.0 and MySQL8.0 - and the MySQL configuration did not finish properly. This was a little bit annoying.

Fine thing if there is newer software that comes automatically with the upgrade. But ... call me conservative or old-fashioned: the operating system should never, never, never interfere with the installed application software. The OS developers cannot know what we are doing out there! Well, they might suggest switching to the newer versions; they might even install newer versions; removing existing versions is suboptimal.

 As our current wiki software version depends on PHP and MySQL, I had to reinstall the previous versions (which was pretty easy, of course) in order to get the wiki online again.

I don't know whether this happened because I made a mistake (as far as I remember I had no choice regarding PHP or MySQL), or if it is part of the default upgrade process or whatever. I just wanted to mention here: after upgrading, check your application versions!

---

### Post by Impavidus on 2021-12-29
Normally, the OS doesn't interfere with the installed application software, other than installing bugfixes. But a release upgrade is the exception. The new release of Ubuntu comes with new software and abolishes some old. For some software (python comes to mind), multiple versions may be supported simultaneously for a few Ubuntu versions. Much of that is mentioned in the [release notes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes), but not every detail, so you may have to look up some details beforehand. I think the upgrade tool tells you what software it's going to install, upgrade or remove before it actually starts, where you can still cancel. Of course, one day support for the old versions of PHP and SQL will be dropped entirely, so you have to migrate eventually.

---

