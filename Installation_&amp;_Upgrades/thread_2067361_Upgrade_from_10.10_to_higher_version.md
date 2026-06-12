---
title: "Upgrade from 10.10 to higher version"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by shashankgaur on 2012-10-06
Hello 

I am using ubuntu 10.10 currently and I was trying to upgrade to higher version but the update manager is not showing option for that. I also tried it using the terminal (sudo apt-get upgrade) and it is not working.

Also earlier I was having problem with some PPA to update the system before upgrading it.
It was related to the following PPA and I unchecked it from the Software Sources
[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu)

But now there is no option of upgrading and from terminal also it is not working.

Please help me in upgrading to higher versions.

Thank you

---

### Post by darkod on 2012-10-06
First of all, sudo apt-get upgrade DOES NOT upgrade the ubuntu version to a higher one. It is used to update/upgrade the packages to the latest version in the repositories.

You don't get the option to upgrade in Update Manager because 10.10 is EOL (end of life). It is not supported any more and the repositories are closed. Not only that you can't upgrade, you can't update the packages any more.

There is a way to upgrade a version that is EOL but even if you do upgrade to 11.04, what will you do? Continue upgrading to 11.10, 12.04?

So many online upgrades in a row almost always create issues and instability.

You can try upgrading with the cd directly (I think it's best to use the Alternate cd for that if I remember correctly), in that case you can skip versions and upgrade directly to the one you want, of course with the cd of the same version.

You can also consider backing up your data and making a new clean install of 12.04 LTS.

In case you don't want to do any of this, and insist of trying an internet upgrade, the instructions for EOL upgrades are here:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But you better either do a clean install or upgrade with the cd.

---

