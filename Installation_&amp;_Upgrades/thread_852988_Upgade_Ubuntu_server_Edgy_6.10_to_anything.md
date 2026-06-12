---
title: "Upgade Ubuntu server Edgy 6.10 to anything?"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by neerolyte on 2008-07-08
I've got a server box currently running Ubuntu Edgy 6.10 (it hasn't been updated in a long time).

By using old-releases.ubuntu.com in my apt/sources.list file I have been able to upgrade using aptitude to the latest edgy packages but I can't do a release upgrade using "do-release-upgrade" due to lots of 404s on the archive.ubuntu.com domain (which isn't in my source file anywhere).

Current apt sources:
```
$ cat /etc/apt/sources.list  | awk '$1~/^d/'
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy universe
deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
deb http://au.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://au.archive.ubuntu.com/ubuntu/ feisty universe
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
```

do-release-upgrade snippet:
```
Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]


Restoring original system state
```

Is there a way to upgrade this box to anything more current without having to rebuild?

---

### Post by avtolle on 2008-07-08
[https://help.ubuntu.com/community/FeistyUpgrades#Network%20upgrade%20for%20Ubuntu%20servers%20(recommended]("https://help.ubuntu.com/community/FeistyUpgrades#Network%20upgrade%20for%20Ubuntu%20servers%20%28recommended")) provides a method to go from 6.10 server to 7.04 server (as an example).

EDIT: Also, [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion) gives more information, and some links that you may find helpful.

---

### Post by neerolyte on 2008-07-09
As I already mentioned "do-release-upgrade" (otherwise known as a network upgrade) is non-functional.

I'm going to try a cdrom upgrade, but it seems that a I can't upgrade from 6.10 to 7.10 (I've already tried that CD) so I'm now downloading the 7.04 CD. Although CD based upgrades are a pain with no cd-rom drive :/

---

### Post by neerolyte on 2008-07-09
Still no luck, I can't do a cd-rom upgrade

```
$ sudo /mnt/ubuntu-7.04-server-i386.iso/cdromupgrade
can't load DistUpgradeViewGtk (No module named pygtk)
can't load DistUpgradeViewKDE (No module named qt)

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


A fatal error occured
Please report this as a bug and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.
Traceback (most recent call last):

  File "/tmp/tmp.rCOWbg7768/feisty", line 56, in <module>
    app.run()

  File "/tmp/tmp.rCOWbg7768/DistUpgradeControler.py", line 1025, in run
    self.fullUpgrade()

  File "/tmp/tmp.rCOWbg7768/DistUpgradeControler.py", line 935, in fullUpgrade
    if not self.prepare():

  File "/tmp/tmp.rCOWbg7768/DistUpgradeControler.py", line 284, in prepare
    'Yes'

TypeError: askYesNoQuestion() takes exactly 3 arguments (4 given)

```

Any ideas?

---

### Post by jpgeerets on 2008-07-09
i have the same problem

---

### Post by zvacet on 2008-07-09
Maybe [this]("https://help.ubuntu.com/community/FeistyUpgradesManual") can be helpful to you.

---

### Post by avtolle on 2008-07-09
When you mentioned the "do-release-upgrade", there was not a mention of doing the installation of the (I think it is called)update-manager-core, thus why I gave the link. I'm wondering if your "workaround" has put your system in a position that the only way to upgrade is a fresh install of 8.04?

---

### Post by neerolyte on 2008-07-10
> **avtolle said:**
> When you mentioned the "do-release-upgrade", there was not a mention of doing the installation of the (I think it is called)update-manager-core, thus why I gave the link. I'm wondering if your "workaround" has put your system in a position that the only way to upgrade is a fresh install of 8.04?
I only posted a snippet, I figured I wouldn't post a _huge_ log write at the start if it might not be relevant.

What work around??? Previous to this post I had only followed documentation on the ubuntu site, none of the standard upgrade procedures were functional.

After a lot of fiddling around last night I ended up doing something very similar to what zvacet's link suggests and the system was reporting "Ubuntu 8.04.1" before I rebooted, now I just get a busybox shell after 10 minutes of failing to boot... it can wait till another day.

---

### Post by zvacet on 2008-07-10
> I ended up doing something very similar to what zvacet's link suggests and

You should follow commands from link I posted to you,not similar to that.

```
gksodo gedit /etc/apt/sources.list
```

You will see search tab>replace and replace all whatever you have (edgy or hardy)to the feisty.Save and close file.

```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```

```
sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

---

### Post by GeekBug on 2008-07-28
Try this ...

[http://ubuntuforums.org/showthread.php?t=868926&highlight=edgy](http://ubuntuforums.org/showthread.php?t=868926&highlight=edgy)

---

