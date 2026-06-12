---
title: "upgrades"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by dlab41 on 2013-04-29
what does this mean?   "Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages) 404 not Found     some index files failed to download. They have been ingnored, or old ones used instead" this keeps on popping up when i try to upgrade my system by useing 1:update manager 2:byobu terminal

---

### Post by howefield on 2013-04-29
In this case, it means the repository does not exist, as 11.04 is now end of life so the repositories are moved to old-releases.

I'd recommend upgrading to a currently supported version, is this a possibility ?

---

### Post by dlab41 on 2013-04-29
can't upgrade to a current supported version also i can't do sudo apt-get -f install   sudo apt-get update   sudo apt-get dist-upgrade have had tryed to use the update manager and byobu terminal

---

### Post by Bucky Ball on 2013-04-29
> **dlab41 said:**
> ... i can't do sudo apt-get -f install   sudo apt-get update   sudo apt-get dist-upgrade ...

You wouldn't have much luck with any of these. As Howefield mentioned, 11.04 is kaput. Reached end-of-life in October last year. If you want something that is supported long-term (five years) upgrade to 12.04 LTS.

Is there a reason you can't install a supported release?

---

### Post by grahammechanical on 2013-04-29
Does this error message stop the upgrade from taking place? I guess that you are using Ubuntu 10.10 (Maverick) and are trying to upgrade to 11.04 (Natty) which you have to do if you are to get to a Ubuntu this is still supported (12.04 Precise). I ask if you can just ignore those error messages and keep upgrading from each upgraded Ubuntu.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184)

Regards

---

### Post by dlab41 on 2013-05-03
can not update nor upgrade at all nor can i use update manager to upgrade nor i can not install, update.dist-upgrade from using byobu terminal   yes i know that 11.04 is kaput yet i still can get on and off the net,,,when i try do the above stuff from both places from using the update manager anf the byobu terminal i keep on getting this message "Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binar-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binar-i386/Packages) 404 not Found     some index files failed to download.They have been ingnored,or oldones used instead" also i have tried to use auto remove to try and fix the problem and i can not install nothing at all

---

### Post by dlab41 on 2013-05-03
yes the error message stops the upgrade from taking place also i am using Ubuntu 11.04

---

### Post by Bucky Ball on 2013-05-03
11.04 ran out of support in October last year so you will not be able to update/upgrade anyhow. I suggest you upgrade to a supported release if you want to avoid problems (11.04 has not had any updates, including security updates, in over six months). 12.04 LTS is the current long-term support release, supported until April 2017 and rock solid.

I have mentioned this previously so leaving you to it to either battle on with what is a fairly useless quest or upgrade to a supported release. Good luck.

---

