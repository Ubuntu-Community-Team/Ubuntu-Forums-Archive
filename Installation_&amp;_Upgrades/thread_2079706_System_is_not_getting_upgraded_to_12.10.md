---
title: "System is not getting upgraded to 12.10"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by vichor on 2012-11-02
Hi all,

I have tried several times to upgrade from my 12.04 to 12.10 and each time I get an error and the upgrade aborts.

I have run do-release-upgrade from the terminal with this result:

```

Checking the package manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done

Calculating the changes

Calculating the changes

Upgrade could not be calculated

An unrecoverable error was detected while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

This may be due to:
* You are upgrading to a not yet released Ubuntu version
* You are using a not yet release Ubuntu version
* Non official software packages, not supplied by Ubuntu

If none of the above points apply, inform about this problem typing the command «ubuntu-bug ubuntu-release-upgrader-core» on a terminal.


Restoring the original state of the system

Cancelling
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done
=== Command detached from window (Fri Nov  2 13:31:57 2012) ===
=== Command terminated with exit status 1 (Fri Nov  2 13:31:58 2012) ===

```
Note: the above messages were partially in spanish and I have translated them. It's a free translation, though, and most probably will be different from the english ones, but I hope they will do anyway.

I have been updating my 12.04 installation with the new updates using the update-manager tool with no issues. Besides, apt-get install -f does not seem to detect any problem to be fixed. So I have no idea what could be preventing to upgrade to 12.10.

Any ideas anyone?

Thanks!

---

### Post by dino99 on 2012-11-02
sudo gedit /etc/apt/sources.list

change each "precise" by "quantal", and deactivate extra archives( like ppa) untill upgrade is made (to avoid conflicts)

A possible reason to non upgraded might be that the system is set to only use LTS (watch synaptic tabs)

---

### Post by vichor on 2012-11-02
I am giving it a try... changed to quantal in sources.list and now running dist-upgrade. Let's see what happens ;)

---

### Post by vichor on 2012-11-03
It tool a while but finally it's updated. Now writing from quantal and no problem in sight (not counting the annoying blank screen stuff which I know more or less how to handle).

Thanks!!

---

