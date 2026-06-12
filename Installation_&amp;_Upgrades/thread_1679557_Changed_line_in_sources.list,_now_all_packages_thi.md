---
title: "Changed line in sources.list, now all packages think they are locally-installed"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by weblordpepe on 2011-02-01
Hi there guys. I have an issue which is preventing my upgrade from 10.04 to 10.10:

Initially, I upgraded to 10.04 no problem. However, I wasn't sure why the upgrade-manager didn't show me that 10.10 was available to upgrade. 

Not realizing that its not a LTS release and the upgrade-manager was configured to show only LTS releases I did something stupid: I replaced all instances of **lucid** in my */etc/apt/sources.list * with **maverick** and ran **apt-get update**.

Now I have a very serious problem:

It still didn't show me that the new Ubuntu is available and I cannot **apt-get dist-upgrade**.
Almost all the packages installed in my system show up under **installed (manual)** and **installed (local or obsolete)**.

I have now configured upgrade-installer to show **ALL** releases, yet I still cannot upgrade to 10.10 due an error stating:> An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

I have reverted all mentions of **maverick** back to **lucid**, and ran **apt-get dist-upgrade**. Still can't upgrade.

**apt-get install**ing one of these packages does not download it from the repository, so I am concerned about doing the entire 3GB of packages.

Now after removing a non-important package, clearing the cache, and redownloading it, it still shows in **installed (manual)**I get this error from synaptic when trying to rebuild the index:> GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

Okay I am stumped. What information can I provide to you guys which will help? I am assuming that a fresh sources.list, and fresh repository keys appropriate for a 10.04 ubuntu, along with some way to trick all installed packages that they came from the repository would be in order?

Update: I have used an online program ([http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)) to generate a new sources.list. I am still suffering the same horrible error message from the update-manager. Help!

My latest step will be to download an ISO of Ubuntu 10.10 and add it a repository source, and see if I can upgrade from the ISO

---

### Post by weblordpepe on 2011-02-01
> **weblordpepe said:**
> Hi there guys. I have an issue which is preventing my upgrade from 10.04 to 10.10:

Initially, I upgraded to 10.04 no problem. However, I wasn't sure why the upgrade-manager didn't show me that 10.10 was available to upgrade. 

Not realizing that its not a LTS release and the upgrade-manager was configured to show only LTS releases I did something stupid: I replaced all instances of **lucid** in my */etc/apt/sources.list * with **maverick** and ran **apt-get update**.

Now I have a very serious problem:

It still didn't show me that the new Ubuntu is available and I cannot **apt-get dist-upgrade**.
Almost all the packages installed in my system show up under **installed (manual)** and **installed (local or obsolete)**.

I have now configured upgrade-installer to show **ALL** releases, yet I still cannot upgrade to 10.10 due an error stating:

I have reverted all mentions of **maverick** back to **lucid**, and ran **apt-get dist-upgrade**. Still can't upgrade.

**apt-get install**ing one of these packages does not download it from the repository, so I am concerned about doing the entire 3GB of packages.

Now after removing a non-important package, clearing the cache, and redownloading it, it still shows in **installed (manual)**I get this error from synaptic when trying to rebuild the index:

Okay I am stumped. What information can I provide to you guys which will help? I am assuming that a fresh sources.list, and fresh repository keys appropriate for a 10.04 ubuntu, along with some way to trick all installed packages that they came from the repository would be in order?

Update: I have used an online program ([http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)) to generate a new sources.list. I am still suffering the same horrible error message from the update-manager. Help!

My latest step will be to download an ISO of Ubuntu 10.10 and add it a repository source, and see if I can upgrade from the ISO

I made an entry in /etc/apt/preferences to pin every package (*) to version 'release 10.04' and priority 1001, then did an apt-get upgrade. It then returned all packages to 10.04 versions.

I still got the error, but when checking the web for other occurances of the update-manager errors I found this: There's actually a bug unrelated to this which was preventing my install. Its the **xserver-xorg-video-nouveau** package which was moved from Base to Universe or something half way through development of 10.10 or something.

An entry for this package was found in my **/var/log/dist-upgrade/apt.log** file.
I found out about this bug from: **[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/614993](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/614993)**

This can now be marked as solved.

---

