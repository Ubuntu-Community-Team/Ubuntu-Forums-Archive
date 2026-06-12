---
title: "old-releases.ubuntu.com missing 16.10 update-manager-core?"
date: 2018-02-21
forum: Installation &amp; Upgrades
---

### Post by Elif on 2018-02-21
Hello,

I'm trying to upgrade an old server on 16.10 to a modern release.

However, i am missing `do-release-upgrade` because i do not have `update-manager-core` installed.

Since apt was obviously not working with the archive./security. sources, i changed over to old-releases.ubuntu.com and `apt-get update; apt-get upgrade` runs clean.

However, I am getting:

```
After this operation, 1,430 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://old-releases.ubuntu.com/ubuntu yakkety-updates/main amd64 python3-update-manager all 1:16.10.10  404  Not Found
Err:2 http://old-releases.ubuntu.com/ubuntu yakkety-updates/main amd64 python3-distupgrade all 1:16.10.10  404  Not Found
Err:3 http://old-releases.ubuntu.com/ubuntu yakkety-updates/main amd64 ubuntu-release-upgrader-core all 1:16.10.10  404  Not Found
Err:4 http://old-releases.ubuntu.com/ubuntu yakkety-updates/main amd64 update-manager-core all 1:16.10.10  404  Not Found
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/pool/main/u/update-manager/python3-update-manager_16.10.10_all.deb  404  Not Found
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/python3-distupgrade_16.10.10_all.deb  404  Not Found
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-core_16.10.10_all.deb  404  Not Found
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_16.10.10_all.deb  404  Not Found

```

As output from `apt-get install update-manager-core` and indeed, those packages are not available if i browse here:
[http://old-releases.ubuntu.com/ubuntu/pool/main/u/update-manager/](http://old-releases.ubuntu.com/ubuntu/pool/main/u/update-manager/)

Is it an oversight that packages for 15. and 17. releases are there, but not 16.?

Is there an official alternative source where I can find these? or is there a bear i can poke to get the packages added to old-releases?

I'm about out of ideas, so it's likely that i'll just provision a new server on 17.10 unless someone can help me

thank you,
eli

PS here is my apt sources.list with comments removed, in case i have made a mistake:
```
deb http://old-releases.ubuntu.com/ubuntu/ yakkety main restricted

deb http://old-releases.ubuntu.com/ubuntu/ yakkety-updates main restricted

deb http://old-releases.ubuntu.com/ubuntu/ yakkety universe
deb-src http://old-releases.ubuntu.com/ubuntu/ yakkety universe
deb http://old-releases.ubuntu.com/ubuntu/ yakkety-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ yakkety-updates universe

deb http://old-releases.ubuntu.com/ubuntu/ yakkety multiverse
deb http://old-releases.ubuntu.com/ubuntu/ yakkety-updates multiverse

deb http://old-releases.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse

deb http://old-releases.ubuntu.com/ubuntu/ yakkety-security main restricted
deb http://old-releases.ubuntu.com/ubuntu/ yakkety-security universe
deb-src http://old-releases.ubuntu.com/ubuntu/ yakkety-security universe
deb http://old-releases.ubuntu.com/ubuntu/ yakkety-security multiverse

```

---

### Post by DuckHook on 2018-02-22
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. The use of [QUOTE] tags in lieu of [CODE] tags introduces [URL] artifacts into your output, which I have also corrected.

As to your issue: first of all, if you are running a server and especially an "old" one, then the first and most obvious piece of advice is to not run standard releases. The best release for old servers is an LTS, the latest being Xenial (16.04). The reason LTS releases are supported for 5 years&#8212;vs 9 months for standard releases&#8212;is to avoid the very upgrade treadmill that is causing you so much grief.

I don't know why *update-manager-core* is missing from the old-releases repos. It may be something that the maintainers have simply overlooked. It is just as mysterious why you don't already have it in your system. My understanding is that it is installed by default with Yakkety. In any case, you can download the *.deb* file from here: [https://launchpad.net/ubuntu/yakkety/amd64/update-manager-core/1:16.10.10]("https://launchpad.net/ubuntu/yakkety/amd64/update-manager-core/1:16.10.10") Look for the link under "Downloadable files" and pay attention to the dependencies.

Note that above advice comes with no testing or personal experience of the process on my part. I have no Yaketty install to test this on, so using this *.deb* file is at your own risk. Please note the warning and read the **!!BACKUP FIRST!!** link in my sig.

---

### Post by Elif on 2018-02-22
Duck:

thank you for pointing out launchpad.net

despite your strangely dogmatic attitude to the contrary, there are reasons people upgrade to non-LTS releases.

for posterity, here is the solution (old-releases also missing deps) that worked for me:
```

wget http://launchpadlibrarian.net/304025083/python3-distupgrade_16.10.10_all.deb
wget http://launchpadlibrarian.net/304025084/ubuntu-release-upgrader-core_16.10.10_all.deb
wget http://launchpadlibrarian.net/212262291/python3-distro-info_0.14build1_all.deb
wget http://launchpadlibrarian.net/316160954/python3-update-manager_16.10.10_all.deb
wget http://launchpadlibrarian.net/316160955/update-manager-core_16.10.10_all.deb
dpkg -i python3-distupgrade_16.10.10_all.deb ubuntu-release-upgrader-core_16.10.10_all.deb python3-distro-info_0.14build1_all.deb python3-update-manager_16.10.10_all.deb python3-update-manager_16.10.10_all.deb update-manager-core_16.10.10_all.deb
apt-get install -f

```

Also, the reason do-release-upgrade was not included, is

it doesn't work.

there does not appear to be an upgrade path from 16.10. Personally, I find this absurd, and since now i have to reprovision this host now anyway, i will be switching to another distro. Enjoy your high horse, Duck.

```

do-release-upgrade

Reading cache

Checking package manager

Can not upgrade 

An upgrade from 'yakkety' to 'artful' is not supported with this 
tool. 
=== Command detached from window (Thu Feb 22 17:13:20 2018) ===
=== Command terminated with exit status 1 (Thu Feb 22 17:13:30 2018) ===


```

---

### Post by QIII on 2018-02-22
And with that...

Closed.

---

