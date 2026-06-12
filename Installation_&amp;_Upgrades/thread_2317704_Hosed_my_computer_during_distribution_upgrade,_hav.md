---
title: "Hosed my computer during distribution upgrade, have I recovered properly?"
date: 2016-03-18
forum: Installation &amp; Upgrades
---

### Post by merockstar on 2016-03-18
Hi, I just ran a distribution upgrade in an attempt to get an SNES emulator to work as described in this thread: [http://ubuntuforums.org/showthread.php?t=2317564](http://ubuntuforums.org/showthread.php?t=2317564)

in the middle of the upgrade, my computer (which I need to open up and clean out because it's been having heating problems) overheated and died in the middle of the process. all the downloading had finished but the installation scripts hadn't. 

oops

anyway I rebooted and ran in safe mode. from that command prompt I ran sudo apt-get -f install and it appeared (to me) to be installing the rest of the stuff it had downloaded for the upgrade. so i let that finish, reboot, and I get a GUI again, hooray!

it appears to be running as 15.10 now. I logged in okay and everything, and then ran a sudo apt-get update, and a sudo apt-get upgrade. there were quite a few packages left to install so that's what's happening as I type this.

is there anything else I need to do to ensure I've properly recovered from the scenario described?

also, since it didn't make it to the "cleaning up" stage of the upgrade, is there anything I should run to make sure I don't have a bunch of outdated packages laying around taking up disk space?

---

### Post by Edison_James on 2016-03-18
It sounds like you have everything under control. Regarding the overheating, it may need a new cooling fan rather than a cleanout.

---

### Post by merockstar on 2016-03-18
> **Edison_James said:**
> It sounds like you have everything under control. Regarding the overheating, it may need a new cooling fan rather than a cleanout.

Thanks Edison, I'll consider myself reassured.

Regarding the overheating, I've never been really mechanically inclined. If I try to fix it it'll end up missing ten screws and feel a lot flimsier, so I think I'm just gonna put it off until next payday and take it to somebody to look at it.

Since I'm on the forums babbling anyway right now, any bets on whether or not the dist-upgrade will fix my 35 minute freezeup problem with ZSNES?

---

### Post by oldos2er on 2016-03-18
Run ```
sudo apt-get update; sudo apt-get dist-upgrade
```

---

### Post by merockstar on 2016-03-18
> **oldos2er said:**
> Run ```
sudo apt-get update; sudo apt-get dist-upgrade
```

thank you for pointing that out. wasn't sure if running it again would result in getting upgraded to some kind of beta version or not.

---

### Post by grahammechanical on 2016-03-18
You may notice a list of packages that you are advised can be removed. This is the apt-get recommend command to remove them

```
sudo apt autoremove
```

The dist-upgrade command does not upgrade to the next version of Ubuntu. It upgrades the existing version bringing packages that have been held back for some reason. I just mention that to give clarity.

Regards.

---

### Post by merockstar on 2016-03-18
> **grahammechanical said:**
> You may notice a list of packages that you are advised can be removed. This is the apt-get recommend command to remove them

```
sudo apt autoremove
```

The dist-upgrade command does not upgrade to the next version of Ubuntu. It upgrades the existing version bringing packages that have been held back for some reason. I just mention that to give clarity.

Regards.

what's the difference between an upgrade and a dist-upgrade? apparently a dist-upgrade is what I thought an upgrade was.

---

### Post by oldos2er on 2016-03-20
From man apt-get: ```

upgrade
           upgrade is used to install the newest versions of all packages currently installed on the system
           from the sources enumerated in /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no circumstances are currently installed
           packages removed, or packages not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without changing the install status of
           another package will be left at their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles
           changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution
           system, and it will attempt to upgrade the most important packages at the expense of less
           important ones if necessary. The dist-upgrade command may therefore remove some packages.
```

---

### Post by montag dp on 2016-03-20
Plain upgrade will hold back packages if bringing them up-to-date means other existing packages have to be removed or new packages have to be added. dist-upgrade will do both of those things.

---

