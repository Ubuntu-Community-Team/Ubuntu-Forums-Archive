---
title: "Can't upgrade from Ubuntu 8.04.2"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by Matt_Davies on 2014-09-25
Hello there.

I've read around, lots of posts, but nothing so far has helped.

Here's what's happening

sudo apt-get update hits loads of errors, failed to fetch loads of stuff
sudo apt-get upgrade then finds alot of stuff to upgrade, but it then can't fetch them, I guess my list is so out of date I can't find anything
sudo do-release-upgrade says there's no new releases

I need to do this urgently because of the bash vulnerability.

I've tried editing this file in a few ways

/etc/update-manager/release-upgrades

Nothing works, I'm assuming as I can't find anything in my sources.list file.  Do I need some new contents in there or something?

Any help, greatly appreciated as always.

---

### Post by Dennis N on 2014-09-25
For 8.04 it would be impossible to upgrade to anything newer without doing a new install because all the needed repositories have been closed - support for this version has ended.

You need to install 12.04 or 14.04 or one of the point versions of those (i.e. 14.04.1)

---

### Post by ajgreeny on 2014-09-25
In theory you could go from 8.04 ->10.04 ->12.04 ->14.04, but each upgrade would be adding the chance of some glitch in the process.

Do a clean install of 14.04 after backing up all your personal files, emails, bookmarks etc etc.

---

