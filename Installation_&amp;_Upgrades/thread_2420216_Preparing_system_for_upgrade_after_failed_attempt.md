---
title: "Preparing system for upgrade after failed attempt"
date: 2019-06-01
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2019-06-01
This is a desktop. The upgrade process from 16.04 to 18.04 seemed to be working until stalled in the install phase, before cleanup.

I continued to work on it, and eventually killed it. I restored from a clone copy.

I need to try again to upgrade, and I really need to know every detail on how to prepare the computer for the cleanest, most problem free, update. I need to make sure I forget nothing - For example: sudo apt-get update sudo apt-get autoremove sudo apt-get autoclean or instead sudo apt-get clean, ANYTHING else I can to to clean, prepare, check / fix errors, etc. before I try again. I'm not a wizard with strong knowledge of terminal command lines, but can follow clear instructions providing specific commands.

It's been suggested that I remove non-Ubuntu-repository software (ie. anything else added, any PPA's or 3rd party sources). How do I identify those, and if they're not in the Ubuntu Repository, how do I remove them with no remaining traces or trash?

Also on this machine (but not the almost identical one that did upgrade successfully) I have used Xdiagnose (in the repository), which caused it to add what looks like terminal commands, or at least visibility of them, to startup. I'm thinking I should remove this, but how do I remove it's lingering effects causing the (additional?) commands to show up?

---

### Post by Rubi1200 on 2019-06-01
Hi,

first of all you should be using apt not apt-get as apt is more up to date as far as package management is concerned.

PPAs: go to Software Sources >> Other and uncheck anything there.

Post the output of this after removing the PPAs:

```
cat /etc/apt/sources.list
```

Xdiagnose can be removed with this command:

```
sudo dpkg --purge --force-all xdiagnose
```

This will purge it but without removing dependencies that may be needed by other packages.

I have successfully upgraded from 16.04 to 18.04 using the following commands:

```
sudo sed -i 's/xenial/bionic/g' /etc/apt/sources.list
```

```
sudo apt update && sudo apt full-upgrade
```

But before doing this please post the cat output so we make sure the sources.list is clean and ready to go.

Thanks.

---

### Post by RogerDavis on 2019-06-01
AS REQUESTED - 
----------------------
```
roger@roger-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial main restricted
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-updates main restricted
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial universe
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial universe
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-updates universe
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial multiverse
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial multiverse
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-updates multiverse
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-backports main restricted universe multiverse

deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-security main restricted
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-security main restricted
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-security universe
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-security universe
deb [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-security multiverse
deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

# deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main # disabled on upgrade to xenial
roger@roger-desktop:~$
```

AM HOLDING FOR FURTHER INFO AFTER THIS POINT - 
------------------------------------------------------------
```
[sudo] password for roger: 
(Reading database ... 366852 files and directories currently installed.)
Removing xdiagnose (3.8.4.1) ...
Purging configuration files for xdiagnose (3.8.4.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1.1) ...
roger@roger-desktop:~$
```

---

### Post by Rubi1200 on 2019-06-02
Just to be on the safe side I would also remove the following because they are not supported:

```
## N.B. software from this repository may not have been tested as## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.picosecond.org/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirror.picosecond.org/ubuntu/ xenial-backports main restricted universe multiverse
```

Can also be done from Software Sources and just uncheck the backport lines.

After that you should be able to use the commands I mentioned and hopefully the upgrade will go smoothly.

I see from your other posts you have cloned backups so in the event this does not work you can restore and we try again.

One other thing I thought of late last night was whether you installed any other desktop environments or themes?

Those can also mess up an upgrade but if you did not add then I believe this should be okay to go ahead with.

---

### Post by RogerDavis on 2019-06-02
I did uncheck the items in the Software Sources under "Other Software" and posted info below.  Is that what you mean by "Backport"?  I can't find any place that "Backport" is specifically mentioned in except in lines already unchecked, and in "Updates, Unsupported Updates, Xenial Backports, which I haven't unchecked yet, so I'm at a loss.  Can you direct me more specifically to what remains to be done?  The URL " [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-backports main restricted universe multiverse deb-src [http://mirror.picosecond.org/ubuntu/](http://mirror.picosecond.org/ubuntu/) xenial-backports main restricted universe multiverse " gets me a "Not Found".  I find there is a tool called "PPA Purge" when I search "how do I disable backports in ubuntu +16.04".  Should I use this?

I have Cinnamon, Gnome Metacity, Gnome Flashback, and Unity installed.  I'm using Flashback, if I remember right, or just maybe Metacity, and have gone to great lengths to set it up as I like.  I was already planning to remove Cinnamon, but am a bit afraid to remove the Gnomes...

---

### Post by RogerDavis on 2019-06-02
Very Curious !!!  I appear to have two Software Centers on my system, one on the desktop, and the other in the menus.  I can find Cinnamon and Gnome desktops on the desktop one, but not the one in the menus.

Cinnamon has MANY items checked as installed, but very unclear as to which one to remove that would catch them all...

I can find Gnome Flashback, but no reference to Metacity.

---

### Post by Rubi1200 on 2019-06-02
After reviewing your posts and consulting with another highly experienced forum member I can only suggest the following.

You mixed and matched so many parts together that to attempt an upgrade is more than likely going to end in failure.

As you pointed out, remove Cinnamon and who knows what else gets removed? And that is only one environment you added, who knows what would happen if you attempt to remove other parts.

I do not see any safe way to unscramble this egg with so many themes and desktop environments.

My best advice is to backup critical data and then do a totally clean install of 18.04.

I also recommend creating a separate /home partition for personal data. That way you can upgrade next time preserving personal data and only deal with the operating system upgrades.

I also recommend not adding themes and desktop environments because this almost always complicates matters.

Pick an environment, pick a theme and stick with it.

Alternatively, if you need to play around then either use LiveCD/USBs, virtual machines or create a separate test partition where you can play around (this is what I do).

In all my years using Linux and being a member here I have not yet seen a successful upgrade with so many elements that could potentially go wrong.

I understand that having to set up personal preferences again is laborious but in this case I think the effort outweighs the risks of a failed upgrade.

Best of luck!

---

### Post by RogerDavis on 2019-06-02
It's done, through terminal.
I'll probably have detail questions a bit later, but I'm still working through the changes for now

---

### Post by Rubi1200 on 2019-06-02
What do you mean it's done?

You did a clean install or you managed to upgrade despite all the potential pitfalls?

---

### Post by RogerDavis on 2019-06-02
Fully upgraded, lost nothing, not a fresh install.  Took HOURS.  Lots of details to attend to.

Xdiagnose is gone, but the (apparently) log display during set-up is still there, I'd like to get rid of that.

One thing I don't fully understand is the start-up screen, shows a beaver outline.  My other system has a windoze like log-in.

Another is that there are about a half dozen options at log-in - SEVERAL Gnomes, Ubuntu (unity), and not Cinnamon which I removed.  Before the update there were less, even before I removed Cinnamon

I suppose I should reset all the repository settings back, but I can't find it now, it's all really different.

---

### Post by deadflowr on 2019-06-02
> I suppose I should reset all the repository settings back, but I can't find it now, it's all really different.
Just find Software and Updates in which ever menu system your logged in with.
You can also try either to find Software Sources (some still use this as the name) or run
```
software-properties-gtk
```

> Another is that there are about a half dozen options at log-in - SEVERAL Gnomes, Ubuntu (unity), and not Cinnamon which I removed. Before the update there were less, even before I removed Cinnamon
Depends on how you removed them.
If you removed certain packages but not the various *-desktop meta-packages then they'd just reinstall the missing packages to fulfill the meta-package requirements.

---

### Post by RogerDavis on 2019-06-03
I think I got the repository stuff, except there were two identical ones for GoogleEarth - but I do have both regular GoogleEarth, and Pro.  Not sure how to handle this one...

The big surprise was all the Gnome log-in choices.  All that was showing before the upgrade was Gnome Flashback and Metacity, now there are several more.

Thanks!

---

