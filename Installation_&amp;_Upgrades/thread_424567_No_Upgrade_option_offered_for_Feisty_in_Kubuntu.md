---
title: "No Upgrade option offered for Feisty in Kubuntu"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Paradoxdruid on 2007-04-26
I've upgraded two of my computers from Kubuntu Edgy to Feisty, but my main desktop...  won't.

When I run Adept Manager, making sure I have edgy-updates enabled, it doesn't offer the Distribution Upgrade tool.  I have removed extraneous repos, made sure all the needed ones are present, I even rebooted the system--  I cannot get the system to offer me the upgrade.

What could I be doing wrong?  The same network was used for the other two systems, and I don't think anything is missing from my sources. 

On someone's advice, I tried adding
```
deb http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/ edgy main
```
to my repos and updating doesn't change the situation, either.

I may just wait till I have a free weekend and do a clean install--  thankfully, I always keep /home on a separate partition.  But I'd really prefer to just upgrade!

Any advice would be much appreciated.

Here's my sources.list:
```

deb http://us.archive.ubuntu.com/ubuntu edgy-updates universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ edgy multiverse 
# deb http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free 
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted 
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe 
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb http://security.ubuntu.com/ubuntu edgy-security universe 
deb-src http://security.ubuntu.com/ubuntu edgy-security universe 

#ntfs-3g & fuse-2.5 repo:
# deb http://givre.cabspace.com/ubuntu/ edgy main main-all 
# deb http://flomertens.keo.in/ubuntu/ edgy main main-all 

```

---

### Post by John Jason Jordan on 2007-04-26
> **Paradoxdruid said:**
> I've upgraded two of my computers from Kubuntu Edgy to Feisty, but my main desktop...  won't.
I had the same problem with my laptop. However, I remembered having seen the option to upgrade to Feisty at the top of the Update Manager screen. Then when I finally decided to do it the option had disappeared. It turned out that in between Update Manager had presented me with an option to upgrade Update Manager to 1.43 and I had done so. Looking in Synaptic, update-manager, properties, versions tab, I found the older 1.42 version. I did a force install of the older version. Afterwards the upgrade option reappeared in Update Manager. Kind of lame, but problem solved. :)

---

### Post by Paradoxdruid on 2007-04-27
> **John Jason Jordan said:**
> I had the same problem with my laptop. However, I remembered having seen the option to upgrade to Feisty at the top of the Update Manager screen. Then when I finally decided to do it the option had disappeared. It turned out that in between Update Manager had presented me with an option to upgrade Update Manager to 1.43 and I had done so. Looking in Synaptic, update-manager, properties, versions tab, I found the older 1.42 version. I did a force install of the older version. Afterwards the upgrade option reappeared in Update Manager. Kind of lame, but problem solved. :)

Glad that worked for you--  but I'm on a pure Kubuntu system, so I've never used Synaptic update-manager.  I use Adept Manager.  The instructions for [Kubuntu upgrades to Feisty]("http://kubuntu.org/announcements/7.04-release.php#upgrade") show Adept Manager and the new Distribution Upgrade tool (which I can't seem to access) to be the way to go.

Anyone have other thoughts?

---

### Post by Paradoxdruid on 2007-04-27
I looked at sources.list on one of my computers that had Adept correctly offer the Feisty upgrade, and the only difference was using archive.ubuntu.com instead of us.archive.ubuntu.com.

But changing that on my system still didn't work.

Could there be a flag set in some configuration file, telling it not to upgrade?

Thanks for any ideas...  I've now had 3 successful Feisty upgrades, but not being able to do it on my main system is annoying.

---

### Post by zvacet on 2007-04-28
Is your Edgy up-to-date?
[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by Paradoxdruid on 2007-04-28
> **zvacet said:**
> Is your Edgy up-to-date?
[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

Thanks for the help, zvacet.  Yes, my Kubuntu is up to date.  I've upgraded three of my systems as per the Kubuntu method at that link, using Adept Manager and near-identical sources lists on the same network.  I cannot figure out why the main desktop won't offer the option.

---

### Post by Paradoxdruid on 2007-04-28
I finally gave up onthe graphical install and used the directions at [https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual) , which was basically aptitude dist-upgrade after modifying my sources.list.

As advertised, it errored, and big time:  Midway through, dpkg failed and the root file system had become read-only.  A quick online search on another computer lead me to remount using ```
sudo mount -o remount,rw /
```
    followed by
```
sudo dpkg --configure -a
```and once everything was back on track, running dist-upgrade a few more times.  At reboot, it said my root filesystem had errors and a manual fsck was needed.  I ran it, saw some inode errors (should I be worried?) and hit yes to fix.  Then, Ctrl-D and it restarted again.

This time, it booted fine, and Feisty is up and running.  Wish the graphical tool had worked for me, but at least it worked out in the end.

---

### Post by trichards57 on 2007-04-29
I had this problem, i ran all the updates, then tried again to get the distribution upgrade tool, but it didn't do it.  My repositories were set up right, admittedly the gb mirrors in my case, but still not too different, but i got nothing.

On the off-chance i hit the update button in Adept, and it seemed to do the right thing, beacuse i then immediatly got a dialog asking if i wanted to upgrade my distribution (success!!!).

Just for information, this was working with what was origionally a copy of Dapper, which i've upgraded through Edgy to Feisty.  It was still quicker than downloading the DVD as well!

Hope this helps someone...

Trichards57

---

