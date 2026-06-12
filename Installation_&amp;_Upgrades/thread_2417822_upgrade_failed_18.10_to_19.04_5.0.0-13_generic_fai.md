---
title: "upgrade failed 18.10 to 19.04 5.0.0-13 generic failed"
date: 2019-04-27
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2019-04-27
I only have Ubuntu 18.04 LTS installed.  Upgraded to 18.10, went ok. Then upgraded to 19.04.  

Then at the end, I got an error that the Linux-image-5.0.0-13-generic failed.  

I did a quick search and found a bug, but it seems that is related to VM. and the solution was to run xxx before restart.  I did not get an option to run anything, the install just failed and kicked me back to the desktop. 


I'm in the process of doing general updates to 18.10, then I'll attempt to redo the upgrade.

Any other suggestions?

d

---

### Post by DuckHook on 2019-04-28
My upgrade was fine and has been without a hitch in a string of 6 (going all the way back to Xenial). However, it's in a tinkerer's partition on a LVM that contains a pristine snapshot and is brought back to strict default every time before I do-release-upgrade. In other words, it is hardly the typical use case.

These forums contain experiences that are all over the map. Some people are like me and experience effortless upgrades going on half-a-dozen times. Others crash and burn every single time. The common success factors tend to be:

[LIST]
[*]Plain vanilla mainstream HW components that are neither too old nor too new.
[*]Absolutely no PPAs or third party repos added&#8212;ever.
[*]No goofy apps or utilities, especially those that modify at the system-level, even from the official repos.
[*]Standard default config files with minimal or no customizations. If you've layered on additional DEs, all bets are off.
[*]Dumb luck.
[/LIST]
So, the usual procedures apply:

[LIST]
[*]Back out all PPAs and 3rd party repos.
[*]Put your system back to as close to default state as humanly possible.
[*]Unmount all esoteric file systems: xfs, zfs, btrfs, raid, yadda-yadda-yadda.
[*]Upgrade over a wired connection. WIFI is just asking for trouble.
[*]**Make good proven backups.** (See my sig)
[*]Cross your fingers and toes.
[/LIST]
Good luck!

---

### Post by Rubi1200 on 2019-04-28
Unfortunately, the most common threads here are booting issues and upgrade issues.

If you follow the advice from DuckHook you should be good to go in most scenarios.

I have a slightly different approach, which may or may not work depending on your setup:

1. I keep a test partition where I can first try the next release before deciding to upgrade

2. I stick to LTS releases only for production

3. I often choose the minimal install option and add only what is absolutely necessary for my needs

4. I do clean installs not upgrades (for the reasons mentioned above) because I make few changes whether adding software or "tweaking," and therefore a clean install is the safest route for me

In the past 13 years that I have been using Ubuntu, since Dapper Drake in 2006, I have NEVER had the types of issues found here on the forums with so many failed upgrades.

If you need more help, please ask as we are more than happy to try and help.

---

### Post by claven123 on 2019-04-28
It said to restart to take effect. And viola after the restart, it 19.04 loaded.

Yes, I pretty much do those things as stated.  I have been on LTS for some time, but wanted to go back to frequent releases.  In the past I've done fresh installs, but it's a pain in the bottom to add all the programs etc.... so, upgrades are 'easier' if all goes well.  Crossing toes and fingers.

My laptop (dual boot) upgrade (18.40 LTS, 18.10, 19.04) went without a hitch....  


Years ago, I did the separate /home partition, haven't done it recently.

d

---

### Post by Rubi1200 on 2019-04-28
Glad things worked out in the end.

Please mark the thread Solved.

Thanks!

---

