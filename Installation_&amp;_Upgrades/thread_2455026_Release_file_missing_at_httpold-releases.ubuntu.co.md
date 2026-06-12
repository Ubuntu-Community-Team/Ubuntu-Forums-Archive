---
title: "Release file missing at http://old-releases.ubuntu.com/ubuntu/dists/ for eoan (19.10)"
date: 2020-12-10
forum: Installation &amp; Upgrades
---

### Post by cyberguard2 on 2020-12-10
I missed the window to update my 19.10 ubuntu using the archive.ubuntu repo (lesson learn, first time on non LTS release).

I've updated my /etc/apt/sources.list as per [https://askubuntu.com/a/91821/1156635](https://askubuntu.com/a/91821/1156635) 

However the Release & Release.gpg file are missing from all the eoan directory :
[LIST]
[*][http://old-releases.ubuntu.com/ubuntu/dists/eoan/](http://old-releases.ubuntu.com/ubuntu/dists/eoan/)
[*][http://old-releases.ubuntu.com/ubuntu/dists/eoan-updates/](http://old-releases.ubuntu.com/ubuntu/dists/eoan-updates/)
[*][http://old-releases.ubuntu.com/ubuntu/dists/eoan-security/](http://old-releases.ubuntu.com/ubuntu/dists/eoan-security/)
[*][http://old-releases.ubuntu.com/ubuntu/dists/eoan-proposed/](http://old-releases.ubuntu.com/ubuntu/dists/eoan-proposed/)
[*][http://old-releases.ubuntu.com/ubuntu/dists/eoan-backports/](http://old-releases.ubuntu.com/ubuntu/dists/eoan-backports/)
[/LIST]

Is this something that can be fixed ? Does Canonical usually fix those type of error ?

Any way around it ? I just want to do a

sudo apt-get update
sudo apt-get install ubuntu-release-upgrader-core
sudo do-release-upgrade

to get upgraded to 20.10


Runing **sudo apt-get update** I get  :
[INDENT]Ign:1 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) eoan InRelease[/INDENT]
[INDENT]Ign:2 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) eoan-updates InRelease[/INDENT]
[INDENT]Ign:3 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) eoan-backports InRelease[/INDENT]
[INDENT]Ign:4 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) eoan-security InRelease[/INDENT]
[INDENT]Err:5 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) eoan Release[/INDENT]
[INDENT]  404  Not Found [IP: 91.189.91.123 80][/INDENT]
[INDENT]Err:6 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) eoan-updates Release[/INDENT]
[INDENT]  404  Not Found [IP: 91.189.91.123 80][/INDENT]
[INDENT]Err:7 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) eoan-backports Release[/INDENT]
[INDENT]  404  Not Found [IP: 91.189.91.123 80][/INDENT]
[INDENT]Err:8 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) eoan-security Release[/INDENT]
[INDENT]  404  Not Found [IP: 91.189.91.123 80][/INDENT]
[INDENT]Reading package lists... Done[/INDENT]
[INDENT]E: The repository 'http://old-releases.ubuntu.com/ubuntu eoan Release' does not have a Release file.[/INDENT]
[INDENT]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/INDENT]
[INDENT]N: See apt-secure(8) manpage for repository creation and user configuration details.[/INDENT]
[INDENT]E: The repository 'http://old-releases.ubuntu.com/ubuntu eoan-updates Release' does not have a Release file.[/INDENT]
[INDENT]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/INDENT]
[INDENT]N: See apt-secure(8) manpage for repository creation and user configuration details.[/INDENT]
[INDENT]E: The repository 'http://old-releases.ubuntu.com/ubuntu eoan-backports Release' does not have a Release file.[/INDENT]
[INDENT]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/INDENT]
[INDENT]N: See apt-secure(8) manpage for repository creation and user configuration details.[/INDENT]
[INDENT]E: The repository 'http://old-releases.ubuntu.com/ubuntu eoan-security Release' does not have a Release file.[/INDENT]
[INDENT]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/INDENT]
[INDENT]N: See apt-secure(8) manpage for repository creation and user configuration details.[/INDENT]
[INDENT]

Thanks 

[/INDENT]

---

### Post by guiverc on 2020-12-11
Also asked on [https://askubuntu.com/questions/1299151/no-release-file-for-eoan-on-old-releases-ubuntu-com/1299176#1299176](https://askubuntu.com/questions/1299151/no-release-file-for-eoan-on-old-releases-ubuntu-com/1299176#1299176)

I made an enquiry on #ubuntu-website, no response yet.

Personally I'd just *upgrade via re-install*, especially if this is a desktop (ie. something-else, use existing partitions and don't format, it'll note your packages, erase only system directories, install then attempt to install additional packages you had installed if available on new release). As server applications can store *conf* files in system directories, some data recovery maybe necessary there.

Stick to LTS (*long-term-support*) releases if you don't like *release-upgrading* every 6-9 months; 19.10 means the 2019-October release, so calculating the EOL date you need to *bump* release is pretty easy (10+9).

Note:  we've had two enquiries about this on askubuntu today; there is a small chance I've tagged the wrong one, but I doubt it.

---

### Post by rnovs on 2020-12-11
I also just tried the same Ubuntu 19.10 upgrade and ran into this problem. 

There are not many google results for this specific issue from before today, is it something that just broke? 
Where would be the correct place to report this, is there an issue tracker for the release repo?

I was following the steps from this tutorial:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by cyberguard2 on 2020-12-11
Yeah I switch from LTS because the version of various package for 3rd party utility in the apt-get repo was not recent enough. 

I really don't feel like re-installing since I'd have to redo my configuration. Not that it's complicated, just that it work now and can't remember exactly what I modified. (At some point I will need to learn ansible or something similar).

I'm seriously considering adding the allow-insecure=yes in front of my repo, but my head keep on winning the argument with me that it's a bad idea an somehow the old-releases could have been compromise.

---

### Post by grahammechanical on 2020-12-11
> to get upgraded to 20.10

First you have to upgrade to 20.04. And that should be possible through Software Updater. In Software & Updates>Updates tab make sure that Notify me of a new Ubuntu version is set to Any New version and not Never.

Then running update/upgrade should trigger a dialog offering an upgrade to 20.04 and then repeat the process to get to 20.10.

Regards

P.S. The old releases method of upgrading a release that has reach End Of Life is for releases that cannot upgrade directly to an In Life release. For example, 18.10 cannot upgrade to 20.04 unless it is first upgraded to 19.04 and then on to 19.10. But 18.04 can directly upgrade to 20.04 (the next In Life LTS release) and 19.10 can upgrade to 20.04 (the next In Life release)

---

### Post by guiverc on 2020-12-12
The issue has been raised at [https://discourse.ubuntu.com/t/no-release-file-for-eoan-in-old-releases-ubuntu-com/19817/2](https://discourse.ubuntu.com/t/no-release-file-for-eoan-in-old-releases-ubuntu-com/19817/2) for now..

---

### Post by fratellonero on 2020-12-12
I also have the same problem since yesterday morning :(

---

### Post by fratellonero on 2020-12-14
Consulting the site:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

it is possible to retrive a mirror for eoan Release such as the follow:

[http://mirror.fairway.ne.jp/ubuntu](http://mirror.fairway.ne.jp/ubuntu)

I solved in this way ;)

---

### Post by ActionParsnip on 2020-12-14
If you boot the Focal install media an upgrade should be offered. Be sure you backup your important data before starting, in case of catastrophe

---

### Post by joel-ostraat on 2020-12-14
As of about 7:15 am CST (UTC-6) on 2020-12-14, the Release file exists on [http://old-releases.ubuntu.com/ubuntu/dists/eoan/](http://old-releases.ubuntu.com/ubuntu/dists/eoan/).

---

### Post by aydv on 2020-12-18
after going to this link, what to do now? how to run `update` now?

---

