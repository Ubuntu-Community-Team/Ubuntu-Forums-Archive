---
title: "Upgrade to 16.04 ?"
date: 2015-11-10
forum: Installation &amp; Upgrades
---

### Post by DJonsson2008 on 2015-11-10
Using apt-get update and apt-get upgrade I surprisingly find one workstation running 16.04.

The machine is running faster, some applications understandably don't run.
Most of the applications I need to run do run though.

I'm wondering 

* Is it possible to rollback to 15.10?

* Should I keep this install and sign up for the 16.04 testers mailing list to 
   report bugs?

* Is there a setting I should set in Synaptic to avoid further upgrades beyond
  15.10 on other machines.

Any advice appreciated.

---

### Post by TheFu on 2015-11-10
Those commands should never change a release, unless specifically asked to be a pre-release tester.
16.04 isn't even alpha stage now. I wouldn't touch it  - did my bleeding-edge time from 1993-1998.

I cannot imagine how anyone would get 16.04 today without taking more than a few manual steps to change the repositories on the system.  Just don't see that happening by accident.

As for rolling back, just restore from the backup made prior to the update that forced 16.04. Easy.

---

### Post by grahammechanical on 2015-11-11
There is a command that will upgrade to a development release and I have seen one post on this forum of a user who run that command on a Ubuntu 14.04 install and now has a dis-functional 16.04 development version.

See Upgrading to the Development Releases.

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

Running do-release-upgrade with the -d switch will do it for you. That being said I run the development version every day. It is stable but I do expect breakage between now and release day in April 2016. If you decide to keep Xenial Xerus then follow events in the Ubuntu Development Version section of this forum.

Regards.

---

### Post by Bucky Ball on 2015-11-11
> **grahammechanical said:**
> There is a command that will upgrade to a development release and I have seen one post on this forum of a user who run that command on a Ubuntu 14.04 install and now has a dis-functional 16.04 development version.



Exactly. And the other things mentioned above.  

Did you issue this command in a terminal?

```
sudo do-release-upgrade -d
```

There is no rollback to 15.10 or anything else. 16.04 LTS or a clean install I'm afraid.

If you keep the install, please post any support requests in ***Ubuntu Development Version*** section of these forums. You are a tester by default. Expect unexpected breakage and frequent updates. Not advisable to use this release on a production machine. 

Having said that, never enough testers, so if you're game and have the time and nothing to lose by testing or have another partition you can install 14.04 LTS or 15.10 on, both directly upgradeable to 16.04 LTS, keep testing 16.04 LTS and reporting. That will be appreciated. 

There should be nothing to change in Synaptic. You upgraded via Synaptic to 16.04 LTS? Please confirm how you did upgrade. Was it like this:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

And to make absolutely sure you are now on 16.04, and I guess you are:

```
lsb_release -a
```

:)

---

### Post by TheFu on 2015-11-11
From the apt-get manpage:
```
dist-upgrade
           dist-upgrade in addition to performing the function of **upgrade**,
           also intelligently handles changing dependencies with new versions
           of packages;
```

No need to run both (update/dist-update) commands.
Just sayin'

---

