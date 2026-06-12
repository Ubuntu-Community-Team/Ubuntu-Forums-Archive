---
title: "Can't upgrade to 16.04"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by timswait on 2016-05-07
I'm currently running 15.10 on a desktop:
```
tim@Upstairs:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 15.10
Release:        15.10
Codename:       wily
```
However, I'm not getting any option to upgrade to 16.04 I had "Show distribution releases" set to "Long term support releases only" but I've also tried "Normal releases" but still Muon Update Manager keeps telling me "The software on this computer is up to date" and not mentioning that a new release is available or giving me any option to install it (Even after clicking "Check for updates". Is there some way to force it to check again more carefully or something!

---

### Post by vasa1 on 2016-05-07
> **timswait said:**
> I'm currently running 15.10 on a desktop:
...

However, I'm not getting any option to upgrade to 16.04 I had "Show distribution releases" set to "Long term support releases only" but I've also tried "Normal releases" but still Muon Update Manager keeps telling me "The software on this computer is up to date" and not mentioning that a new release is available or giving me any option to install it (Even after clicking "Check for updates". Is there some way to force it to check again more carefully or something!

Hi,

Have you tried out Kubuntu 16.04 by using a Live USB? If not, you should to make sure that 16.04 plays well with your hardware.

Also, please remember that 16.04 has been recently released and may still have bugs. This is important if the computer in question is being used for important work. If you're somewhat conservative, you may be better off waiting for the first point release sometime in July or August 2016.

You mentioned that Muon isn't offering the 15.10 > 16.04 upgrade. If you really want to go ahead, check out the section titled *Upgrade After Ubuntu 16.04 LTS Is Released* in [http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-15-10-to-16-04-lts](http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-15-10-to-16-04-lts). It offers a way to proceed if the GUI route doesn't work.

Needless to mention that you'll have backed up all your personal files before proceeding!

---

### Post by timswait on 2016-05-07
Typing
```
sudo do-release-upgrade
```
I get:
```
Checking for a new Ubuntu release
No new release found

```

---

### Post by timswait on 2016-05-07
I've got a feeling there's something "not quite right" about this computer. When I upgraded it to Wily there was a power cut while it was upgrading which upset the process. I managed to recover it, and it is now fully updated and not showing any broken packages, but it still seems to keep having random minor issues. I was hoping the upgrade to Xenial would fix them, but I guess this refusal to see the upgrade is related.

---

### Post by Bucky Ball on 2016-05-07
> **timswait said:**
> I was hoping the upgrade to Xenial would fix them ...

This is very rarely the case. :|

Unless it's hardware related, i.e. more recent drivers are in the newer version and your hardware needs them to work correctly, upgrading a broken OS to a newer one gets you a newer broken OS.

---

### Post by timswait on 2016-05-07
Putting in:
```
sudo do-release-upgrade -d
```
Seemed to work, it has now updated to 16.04 :)

---

