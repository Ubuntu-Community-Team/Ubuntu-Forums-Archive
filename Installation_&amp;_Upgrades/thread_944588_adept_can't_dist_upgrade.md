---
title: "adept can't dist upgrade"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by propedor on 2008-10-11
Hi guys,

Background:
Yesterday I got myself into trouble, originally I was running Kubuntu Gutsy with KDE 4.0 (didn't set that up myself).  I had a *lot* of trouble upgrading, apt-get was failing on some bogus-looking python2.5/python2.5-minimal dependencies so I removed some stuff hoping reinstalling packages would help; then cupsys couldn't install and was required by every little thing I needed (most importantly kubuntu-desktop and stuff like apt-show-versions).  Eventually I got everything working by downloading the 8.04 Alternate ISO, extracting the upgrader manually (when the cdromupgrade script called tar it couldn't find the file?), editing the python so it would decide to install kubuntu-desktop instead of bailing, and running the Hardy upgrade from there.  Amazingly, that worked without a hitch, KDE 3.5 is running wonderfully on 8.04 now.

But the reason I'm running Linux (it's inside VMWare Player actually) is to try out KDE 4.  I tried installing kubuntu-kde4-desktop but kdm didn't work and neither do the KDE4 programs.  Then I came across this page: [https://help.ubuntu.com/community/IntrepidUpgrades/Kubuntu](https://help.ubuntu.com/community/IntrepidUpgrades/Kubuntu) , and I'm figuring Ibex should run KDE4.1 more successfully, so I tried to follow their steps to upgrade.

The problem:
I actually encountered this back where I was trying to get from Gutsy to Hardy, some other page suggested to use Adept and hit Version Upgrade, and the same problem is happening with Version Upgrade now when I use
```
kdesudo "adept_manager --dist-upgrade-devel"
```
Dialogs: "New version available" -> Next, "Release announcement" -> Next, "Downloading" (it downloads) -> "Ready to upgrade" -> Finish.
Nothing happens (expected: upgrade starts).

Here's the funny part, it looks like the problem is just that the upgrader needs Adept to be closed before it can run!  When I've run Adept from the console and hit Finish I get:
```
[some numbers]
Reading state information: Done

Unable to get exclusive lock

This usually means that another package management application (like
apt-get or aptitude) [sic] already running. Please close that application
first.
```

After all the ridiculous problems I solved already, this one looks really minor.  But I can't find any info on how to get around it.  I'd be willing to wait to upgrade until 8.10 comes out for real, but given the Version Upgrade didn't work to get to 8.04 either, I doubt I'll be in a better position just by waiting till the end of October.

Questions:
1) Can I just run the upgrade program Adept downloaded?  Where is that, what is it called?
2) Can the Adept problem be worked around?  Is it a bug?

Thanks for any help.

---

### Post by propedor on 2008-10-14
No replies... Is my description hard to read?  Should I be asking KDE?

---

