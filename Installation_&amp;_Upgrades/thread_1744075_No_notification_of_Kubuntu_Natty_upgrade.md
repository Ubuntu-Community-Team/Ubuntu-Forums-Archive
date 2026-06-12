---
title: "No notification of Kubuntu Natty upgrade"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2011-04-30
I'm running Kubuntu 10.10.  Now that Natty is out, I should be getting a notification of it -- but I'm not.  I tried all the obvious ways of fetching the upgrade, but none of them did anything:

1. I went into Synaptic and did a Reload / Mark All Upgrades.  No sign of the Natty upgrade.  I tried disabling repositories and reloading, then enabling repositories and reloading.  None of these actions made any difference.

2. I went into KPackageKit and tried to upgrade from there.  I made sure that Show Distribution Releases was set to normal.  No help there.

3. On the command line I tried:

    sudo apt-get update
    sudo apt-get upgrade

No better luck there either.

I asked about this in the Kubuntu forum but didn't get a response that would help me solve the problem.  Does anyone here know why I'm not seeing the upgrade notification?

---

### Post by markofealing on 2011-05-05
Same here!

I've got one PC which only notifies me of updates but no distribution updates and another which notifies me of dist updates but refuses to upgrade.

So far I'm ranting the upgrade process for Kubuntu 10.10 to 11.04 as 0 out of 10.

If this is the Kubuntu experience, then Kubuntu is definitely not desktop ready for the average user.

---

### Post by pwabrahams on 2011-05-05
First, I'll mention that the best test of the availability of the upgrade online is to execute **do-release-upgrade** in a command-line window.  If that doesn't work, nothing else will as far as I can determine. I haven't seen that fact disputed in all the threads on the subject.

I've been asking without anyone answering, in several threads, what the mechanism is for issuing the notification automatically.  Understanding that would help explain why many people, but not a majority, are having the no-upgrade problem.  What separate the fortunates from the unfortunates?  I was running three different Kubuntu 10.10 systems, two in different partitions on a single machine and the third on a different machine.  All three had the problem.  I've upgraded the three with the Alternate CD method.  That works fine but shouldn't be necessary.

A useful experiment, which I might get to do myself, is to do a fresh install of 10.10 Kubuntu and then immediately invoke **do-release-upgrade**.

---

### Post by pwabrahams on 2011-05-05
As an experiment, I created a new virtual installation of Kubuntu 10.10 (the x86 version).  As soon as the installation was fully updated, the notification appeared unbidden, just as it was supposed to.  That raises two possibilities: (1) it's a 32-bit vs. 64-bit issue, or (2) the problem is caused by something in one of the non-default repositories.

---

