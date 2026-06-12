---
title: "unresolvable problem when calculating the upgrade"
date: 2014-09-16
forum: Installation &amp; Upgrades
---

### Post by ccurvey on 2014-09-16
Trying to upgrade from 13.10 to 14.04.  I did have other packages installed (cinnamon, postgresql, chrome, others). They have all been unchecked in the panel in Synaptic.  (However, if I do check them, I'm not given the option to remove them.)

I moved /var/lib/apt/lists to lists.old, then created a new lists/partial, and apt-get update.  (I saw a thread on that, don't have it in front of me.)

Still nothing.  There are many lines about "broken packages" in /var/log/dist-upgrade/main.log.  Libclutter and libcolgl seem to repeat a number of times.

Any clues for the clueless?

---

### Post by Bashing-om on 2014-09-16
ccurvey; Maybe ?

Let's suppose that 13.10 was NOT fully updated at the time it went End-O-Life, and as such now the upgrade can not proceed.
What I would try:
a) ALL PPAs remain disabled;
b) ANY proprietary drivers reverted to open source;
c) screen saver disabled;
d) Source.list file edited to reflect "old-releases", as per:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

E) You do have your data backed up ? Yes !

Now see what results:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo do-release-upgrade

``` If in the update/upgrade (1st 2) there are errors reported, stop and fix the errors ! And perhaps at this point give serious consideration to doing a fresh clean install of release 14.04 - but the call is always yours.

[INDENT][INDENT]where there is a will, there is a way
[/INDENT][/INDENT]

---

### Post by ccurvey on 2014-09-23
thanks for the help, Bashing-om.

I've tried what you said, to the best of my ability.  There are no errors (and nothing to update) for steps 1-3.

When I run "sudo do-release-upgrade", many things scroll by.  The only error that I see is when it tries to download "Translation-en_US".  I get this error for trusty/main, trusty/multiverse, trusty/restricted, trusty/universe.

It is trying to download from [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)

Does that spark any thoughts?

---

### Post by Bashing-om on 2014-09-23
ccurvey; Humm ...

I was thinking that the upgrade path from 13.10 was still open, even though 13.10 is End_Of_Life. ??
Before we try the EOL upgrade procedure let's make sure of the sources:
post back - between code tags - the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Take a look, clean things up, and try again .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

