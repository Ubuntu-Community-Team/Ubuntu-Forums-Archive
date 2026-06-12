---
title: "Version upgrade from command line?"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by gastur on 2008-05-23
Good day!

I have upgraded kubuntu from 7.04 to 7.10 last year, and from 7.10 to 8.04 this year on a couple of computers using GUI version upgrade tool. And it always failed at some points of upgrade process, so every time I had to run dpkg and apt to finish the whole thing. Though these troubles didn't lead to any system malfunctions, I dislike GUI upgrade tools more and more.

So, tell me please, what is the way to do version upgrade not using GUI tools?

Will it be enough to change repositories in /etc/apt/sources.list to the new version, and then run:

sudo apt-get update
sudo apt-get dist-upgrade

Or more configuration has to be done?

Thanks in advance! (I have one more system to upgrade, and I don't want the same troubles anymore - despite they are relatively easy to deal with).

---

### Post by dstew on 2008-05-23
I think the command is **do-release-upgrade**. Check this [ Wiki page]("https://help.ubuntu.com/community/HardyUpgrades#head-e7f287c730b93116f89de7ea7e05efbe95fa6dd1"). Look down the page for the information on upgrading server systems.

---

