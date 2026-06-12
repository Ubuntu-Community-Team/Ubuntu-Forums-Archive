---
title: "Version upgrade Kubuntu Gutsy"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by 1/0 on 2007-10-21
I have three computers running Kubuntu Gutsy and all of them has this one problem. One laptop has the rc1 installed, the second a fresh install of 7.10 and the third upgraded from 7.04. 

Here's the problem. As soon as I fetch updates in adept the blue double arrow icon for version upgrade appears. Why is that? They either run 7.10 rc1 or 7.10 and shouldn't have to upgrade from 7.10... Fine if the upgrade went wrong but a fresh install?

Am I misunderstanding this icon? I pressed it on the upgraded computer and it uninstalled a bunch of packages and removed all my locals, s.a. keyboard configuration.

I have tried to find similar posts in the forum but there are quadrillions of them when I search.

---

### Post by CptPicard on 2007-10-21
Seems to be an Adept bug:

[https://bugs.launchpad.net/ubuntu/+source/adept/+bug/153889](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/153889)

Just relax, the system is up to date, and I'm sure this will be fixed shortly, as a lot of people seem to be having the problem. :)

---

### Post by 1/0 on 2007-10-21
Thanks mate! Good to know its something I can disregard for now. Every time I click it, it uninstalls a bunch of packages...

---

### Post by wolfger on 2007-11-10
It may well be fixed... there is an update to Adept. Unfortunately, the Adept on the fresh install fails every package upgrade or install I try. I am now stuck with a fresh install of Gutsy that's nearly worthless. :-(

---

### Post by dscherry on 2007-11-10
Hi,
I didn't have the exact same problem you described, but I did have problems with Adept while upgrading two different PC's.  I was able to get past my problems with two different methods.  If you're comfortable with the command line, you can reduce the chance of other problems by logging out (not shut down), then log in on the non-gui terminal (Ctrl-Alt-F1) to run an upgrade.  If you don't like the command line, then quit as many gui apps as you can, then run the following in Konsole.

First method:
$sudo apt-get update
$sudo apt-get dist-upgrade

If this succeeds, you can restart with...
$sudo shutdown -r now

If it doesn't succeed, you can try
$sudo do-release-upgrade

This may tell you there isn't any release to upgrade to, which means this isn't going to help.  But if it views your problem as an upgrade issue, then it should complete what Adept couldn't.

In the event that this command doesn't go to completion,
 you can run it again, and it will pick up where it left off (I ran it three times on one of my PC's, but wound up with a clean installation).

If it completes successfully, you can shutdown, as above.

I can't say this will be a fix for you, since the problems are a little different, but the first method is the same as what Adept does when you do an upgrade (same version), and the second is similar to what Adept does when you do a version upgrade.

Hope you're able to solve it...
Dan

---

