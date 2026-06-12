---
title: "Can't upgrade from yakketty to artful"
date: 2018-01-31
forum: Installation &amp; Upgrades
---

### Post by eddieparkerami on 2018-01-31
I'm trying to upgrade from yakkety (16.10) to.. well, anything newer than yakkety, but all the upgrade commands are failing me.

sudo do-release-upgrade yields a "An upgrade from 'yakkety' to 'artful' is not supported with this tool.", and the software update center similarly tells me I can't upgrade.

Do I have to nuke and pave to upgrade off of yakkety?  Is there a way to do this inplace still?

---

### Post by westie457 on 2018-01-31
Hello eddieparkerami
   In this case it is easier and a lot quicker to clean install 17.10 using the 'something else' option in the Installer.
If you really would like to try a double upgrade where things might break and then you would have to clean install anyway we could give it a try.

Remember you will be upgrading from one unsupported release (16.10) to another unsupported release (17.04) and then to supported release (17.10). Each upgrade will take about 2 hours, whereas the clean install will take about half an hour.

Which would you like to try?

---

### Post by eddieparkerami on 2018-02-06
Hi Westie!

Well, seeing as how I'm kinda hosed no matter what, maybe let's try the double upgrade, since I've backed up everything anyhow.

How do I upgrade to 17.04 from 16.10?

---

### Post by coffeecat on 2018-02-06
> **eddieparkerami said:**
> 
How do I upgrade to 17.04 from 16.10?

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

That should get you from 17.04 to 17.10 as well.

---

### Post by eddieparkerami on 2018-02-06
Unfortunately that's the problem, the do-release-upgrade doesn't work for yakkety anymore:



> Reading cache


Checking package manager


Can not upgrade


An upgrade from 'yakkety' to 'artful' is not supported with this
tool.
=== Command detached from window (Tue Feb  6 06:44:37 2018) ===




---

### Post by qsebas on 2018-02-06
same problem here...

I've found this post:
[https://andreas.scherbaum.la/blog/index.php?url=archives/950-Upgrade-from-Ubuntu-16.10-yakkety-to-17.10-artful.html#feedback](https://andreas.scherbaum.la/blog/index.php?url=archives/950-Upgrade-from-Ubuntu-16.10-yakkety-to-17.10-artful.html#feedback)

but after doing it step by step I get the same error...

---

### Post by Frogs Hair on 2018-02-06
You can try the following , but backup before starting.

```
sudo sed -i 's/yakkety/zesty/g' /etc/apt/sources.list
``````
sudo apt update 
``````
sudo apt full-upgrade
```

---

### Post by mörgæs on 2018-02-06
> **eddieparkerami said:**
> ...since I've backed up everything anyhow.


I'd say that you are all set for a clean install.

---

### Post by jbwillia on 2018-02-06
> **qsebas said:**
> same problem here...

I've found this post:
[https://andreas.scherbaum.la/blog/index.php?url=archives/950-Upgrade-from-Ubuntu-16.10-yakkety-to-17.10-artful.html#feedback](https://andreas.scherbaum.la/blog/index.php?url=archives/950-Upgrade-from-Ubuntu-16.10-yakkety-to-17.10-artful.html#feedback)

but after doing it step by step I get the same error...

This is currently working just fine for me. Where you are probably faltering is with the line:

```
sed -i -e 's/de.archive/old-releases/' /etc/apt/sources.list
```
The "de.archive" in there is the host prefixed with the country code (de for Germany). For me in the US, I had to replace it with "us.archive" to get the substitution to actually happen. You can manually do it in a text editor if you like as well. Just also keep in mind you will have to be root or use sudo to save the changes as well. The main goal is to change all the archive host names to old-releases.

---

### Post by elmurdoque on 2018-03-26
> **qsebas said:**
> same problem here...

I've found this post:
[https://andreas.scherbaum.la/blog/index.php?url=archives/950-Upgrade-from-Ubuntu-16.10-yakkety-to-17.10-artful.html#feedback](https://andreas.scherbaum.la/blog/index.php?url=archives/950-Upgrade-from-Ubuntu-16.10-yakkety-to-17.10-artful.html#feedback)

but after doing it step by step I get the same error...


I ran into this Problem when I discovered a machine in my Office that has not been used for about half a year. Upon turning it on, I found out that it was still running yakkety.
A short while later, I found out that it has reached EOL. And only upgrades to EOL 17.04. 


Doing a step by step with the mentioned blogpost, I managed to upgrade from yakkety to zesty in a couple of minutes without any problems, but that was a dead end, no upgrade from zesty to artful.

apt update claimed everything is up to date and do-release-upgrade came back with no new releases. 


So I added the artful entry into  /var/lib/update-manager/meta-release
 
```

Dist: artful
Name: Artful Aardvark
Version: 17.10
Date: Thu, 19 October 2017 17:10:00 UTC
Supported: 1
Description: This is the 17.10 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/artful-updates/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/artful-updates/main/dist-upgrader-all/current/ReleaseAnnouncement
ReleaseNotesHtml: http://archive.ubuntu.com/ubuntu/dists/artful-updates/main/dist-upgrader-all/current/ReleaseAnnouncement.html
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/artful-updates/main/dist-upgrader-all/current/artful.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/artful-updates/main/dist-upgrader-all/current/artful.tar.gz.gpg

```

and into /etc/apt/sources.list :

```

deb http://de.archive.ubuntu.com/ubuntu/ artful multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ artful multiverse
deb http://de.archive.ubuntu.com/ubuntu/ artful-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ artful-updates multiverse
deb http://de.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse

```

After that, apt update found a lot of packages that can be upgraded and do-release-upgrade went off to fetch 17.10.

---

