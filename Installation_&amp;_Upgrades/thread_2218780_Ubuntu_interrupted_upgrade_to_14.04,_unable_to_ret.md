---
title: "Ubuntu interrupted upgrade to 14.04, unable to retrieve"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by prapanch on 2014-04-21
I tried to update from Ubuntu 12.04 to 14.04 using the update-manager. But the upgrade process stopped midway due to insufficient disk space. I cleared up enough space, and tried to resume by
    > sudo update-manager -d 
But now, the update manager doesn't show the ubuntu 14.04 upgrade option now.
I tried the following
    > sudo apt-get autoremove
    sudo apt-get clean
    sudo apt-get update && sudo apt-get dist-upgrade
None of these help. Please help.

---

### Post by jcdenton21 on 2014-04-25
I am having the same problem
I cancelled the update while fetching packages as it was slow and also received the message that the system wil be restored to pre-upgrade state and I can continue wi release-upgrade later

well I can not

> martin@Martin-NTB:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
martin@Martin-NTB:~$ uname -a
Linux Martin-NTB 3.8.0-39-generic #57~precise1-Ubuntu SMP Tue Apr 1 20:04:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
martin@Martin-NTB:~$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
No new release found
martin@Martin-NTB:~$ 



how can I continue and upgrade to 14.04?
please help

---

### Post by John Jason Jordan on 2014-04-25
These are examples of why Ubuntu should never have made it impossible to do a dist-upgrade from the live DVD.

Aside: If you use the live DVD and click on Install, you will get to a place where it sees your existing installation of a prior Ubuntu and offers the option to do the upgrade. If you select the upgrade option and continue you may think you are doing the upgrade from the live DVD, but in fact, it will still fetch every single file from the net connection. It is no longer possible to do a dist-upgrade without a net connection. Curses on Ubuntu for this.

As for solving your problem, a similar situation happened to me several years ago - my cable modem decided to die in the middle of the upgrade. I was able to recover by using a dpkg command over and over again. Unfortunately, I cannot remember exactly what it was - something like dpkg-reconfigure-all. The dpkg utility will fix all broken packages. Hopefully someone else here can clarify what I am talking about.

---

### Post by jcdenton21 on 2014-04-26
I tried PXE booting 14.04 as that notebook does not have optical drive and I don't have a spare USB flash drive that I could format and use for installation

after initiating installation it did not provide me option to upgrade currently installed 12.04 on HDD
[ATTACH=CONFIG]252517[/ATTACH]

I was expecting something like this to appear [IMG]http://www.liberiangeek.net/wp-content/uploads/2012/04/upgrade_cd_percise_3_thumb.png[/IMG] source: ([http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-11-10-using-ubuntu-cd-dvd/](http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-11-10-using-ubuntu-cd-dvd/))

any other ideas how to upgrade the system

---

