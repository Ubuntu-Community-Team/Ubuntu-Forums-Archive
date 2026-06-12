---
title: "partial upgrade crashiing!"
date: 2009-06-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by meeples on 2009-06-03
i just checked my update manager and it said the regular blahblah blah not all updates can be installe blah blah partial upgrade.

so i click upgrade. and it gets just gets to the bit where it downloads packages and then it just closes.

so i tried "sudo apt-get upgrade" which updated some packages but i still need to do the partial upgrade which isnt working.

anyone else having this?

---

### Post by fifth on 2009-06-03
Have you tried apt-get dist-upgrade?

---

### Post by 23meg on 2009-06-03
Do not perform partial upgrades when testing the development branch. Make sure your mirror is up to date, and just wait until the archive stabilizes and all dependencies can be satisfied.

---

### Post by meeples on 2009-06-03
> **fifth said:**
> Have you tried apt-get dist-upgrade?


ah right, yea i tried but i couldnt remember the code i tried distro-upgrade, and distribution-upgrade lol

> **23meg said:**
> Do not perform partial upgrades when testing the development branch. Make sure your mirror is up to date, and just wait until the archive stabilizes and all dependencies can be satisfied.

oh. see before now ive been going with, if ubuntu says so then do it. lol. ok i wont do the partial upgrade. THANKS.

---

### Post by davideotape on 2009-06-03
> **23meg said:**
> Do not perform partial upgrades when testing the development branch. Make sure your mirror is up to date, and just wait until the archive stabilizes and all dependencies can be satisfied.

That's interesting, and certainly the first time I've heard anything of the sort. Thanks for warning me. I don't recall this info being displayed anywhere though, so I'll check all the upgrading documents again to see if I've missed anything.

Could I also ask what the difference between apt-get upgrade and apt-get dist-upgrade is. I'm neither an command line or update manger person; it's synaptic all the way for me :D

---

### Post by super.rad on 2009-06-03
from "man apt-get"
> **update**
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.

**upgrade**
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

**dist-upgrade**
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

---

### Post by davideotape on 2009-06-03
Thanks for that :D So dust-upgrade is like a partial upgrade in update manager then, and upgrade is just normal update. That's another one of linux's great mysteries solved for me :)

---

### Post by psyke83 on 2009-06-03
> **davideotape said:**
> Thanks for that :D So dust-upgrade is like a partial upgrade in update manager then, and upgrade is just normal update. That's another one of linux's great mysteries solved for me :)

Not quite.

Using "apt-get upgrade" is always the safest option - it won't elect to install new packages to satisfy any new dependencies. Using this may cause packages to be held back, though.

Using "apt-get dist-upgrade" will upgrade packages including any new dependencies. Usually this works properly... however, if the repository is in an inconsistent state (e.g. when a series of packages which depend on each other are being built, but all haven't yet been uploaded), this may cause vital packages to be removed. This scenario can occur quite frequently during the development process

When you see a "Partial Upgrade" in the Update Manager, this is the equivalent of a dist-upgrade when the repository is in an inconsistent state. Except for some specific cases where you are certain that some packages should be removed, you should **never** allow a Partial Upgrade to occur.

23meg, I thought that you had a sticky explaining this stuff for earlier development releases, can you resurrect it? :)

---

### Post by 23meg on 2009-06-03
> **psyke83 said:**
> 
23meg, I thought that you had a sticky explaining this stuff for earlier development releases, can you resurrect it? :)

I'm working on that; it will be posted soon.

---

### Post by ranch hand on 2009-06-05
I am relatively new to Linux.

We are working here with an alpha1 release.  It seems to me that a little bit conservative approach is the obvious way to go.

Be careful to read any warnings and then do wome reseach before doing anything.  The repos need to be updated and then checked to see if it works.  If it is not, give the poor buggers a chance to fix it.

---

### Post by Nullack on 2009-06-05
IMHO your better of not doing a dist-upgrade and waiting for the repos to be updated properly. Theres no magic way around configuration item dependencies.

---

### Post by cariboo on 2009-06-05
If I get a notification of a partial update, and I don't want to wait for the dependencies to catch up I use:

```
sudo aptitude safe-upgrade
```

It hasn't let me down so far.

---

### Post by ranch hand on 2009-06-06
> **cariboo907 said:**
> If I get a notification of a partial update, and I don't want to wait for the dependencies to catch up I use:

```
sudo aptitude safe-upgrade
```

It hasn't let me down so far.
Now, I knew that I joined these forums for some reason.

This is a new command to me.  I MUST try it.  Geeze linux is fun.

---

### Post by jkohler2 on 2009-06-17
I had the same issue with partial upgrade.

Thank you for the command line answer.

John

---

### Post by xebian on 2009-06-18
Partial update does not buy you anything.  If there is one, it's breakage.  Since when does apt-get or aptitude has partial-update option?

---

### Post by douham on 2009-06-18
I had not heard of the cmd "sudo aptitude safe-upgrade" before. I've been hanging at partial upgrade for a while. Dist-upgrade told me it was going to remove "hot-key setup". No big deal but i used aptitude safe-upgrade, got over 100 MB of updates and well, my hotkeys still work.
(haven't tried to set up any hotkeys yet though!)

---

### Post by super.rad on 2009-06-18
> **douham said:**
> I had not heard of the cmd "sudo aptitude safe-upgrade" before. I've been hanging at partial upgrade for a while. Dist-upgrade told me it was going to remove "hot-key setup". No big deal but i used aptitude safe-upgrade, got over 100 MB of updates and well, my hotkeys still work.
(haven't tried to set up any hotkeys yet though!)
Hotkeys is supposed to be removed

---

### Post by jerrylamos on 2009-06-18
Just tried Update "Manager" which complained about "partial upgrade".
Having been burned by that before, that is "now I get to re-install", I didn't.

Tried sudo apt-get upgrade and sudo apt-get upgrade which said 6 packages being held back so I did "n".

sudo apt-get dist-upgrade didn't complain about anything, said some packages would be removed.  They looked innocent.  I then replied "Y" and the floodgates opened with a massive amount of changes, claimed 198 upgrades, 55 newly installed, 1 removed.  The removal is something about hotkeys I think.

Now to re-boot to see what's broken....

Jerry

p.s. Reboot went O.K., Firefox up, maybe the mirror got updated in time.  Now to check some more functions.

---

