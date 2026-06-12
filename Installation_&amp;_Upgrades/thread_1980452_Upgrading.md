---
title: "Upgrading"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Tinker1972 on 2012-05-15
Can anyone point me in the direction of instructions for upgrading from 10.04 LTS to 12.04 LTS please?

---

### Post by darkod on 2012-05-15
If your Updates option is set to Long Term releases only, the Update Manager doesn't offer upgrade to LTS from the previous LTS until the first .1 is released.

Some of the issues noticed in 12.04 can be fixed in 12.04.1, that's why the upgrade process from the previous LTS version waits until the .1 is released, which is due in July.

it might be better to wait for it. 10.04 still has updates for one year more so you can wait until July without any problem.

If you don't want to wait, you can start from terminal the Update Manager with an option for the upgrade to 12.04 with this:
sudo update-manager -d

---

### Post by jadtech on 2012-05-15
Network Upgrade for Ubuntu Desktops 10.04 LTS to 12.04 LTS (Recommended)
Note that the page under [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS) says: "It is generally recommended that users of Ubuntu 10.04 LTS wait until the first point release, due in July, before upgrading." Follow the instructions there if you want to upgrade earlier since the following instructions will probably not work until then.


this is what the documentation says  just a warning if you want to upgrade from 10.04 right now make backups ..

all you have to do right now to up grade is go to the software updater and in setting  check mark to update proposed update and pre-releases then click the check button keep updating.if the upgrade button doesn't show up go to the terminal type 

```
 sudo apt-get update
do-release-upgrade

```

just a side note if its not worth the time it takes to make  a back up  go  get the ISO burn  it to a dvd or bootable USB and do a clean install from scratch there is far less chance of having problems  ..

---

### Post by barney385 on 2012-05-15
Good Info. Thanks guys. I downloaded the new release, but now I think I'll just wait for July to roll around.

No hurries.

: )

---

### Post by Tinker1972 on 2012-05-15
Thanks for the help everybody. I think I'll wait until July, as presumably the main kinks will be ironed out.

---

### Post by Bucky Ball on 2012-05-15
> **Tinker1972 said:**
> Thanks for the help everybody. I think I'll wait until July, as presumably the main kinks will be ironed out.

+1. If you're running a production machine or just need reliability/stability this is a good idea. You might wait for the release of 12.04.1.

---

