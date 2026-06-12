---
title: "Getting stuck during Upgrade on Ubuntu 14.04"
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by Deeks22 on 2015-12-17
Hi everyone,

I currently have to administrate some Ubuntu Server machines and I'm having trouble with [FONT=courier new]apt-get upgrade[/FONT]. I'm trying to upgrade a machine running 14.04, which hadn't been updated/upgraded for a very long time. While [FONT=courier new]apt-get update[/FONT] works just fine, the upgrade-process gets stuck at the point where it seems to restart the ssh service, saying [COLOR=#6A6A6A][FONT=arial]**ssh stop**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial][B]waiting
[/B][/FONT][/COLOR]
From there on, the upgrade won't continue. I'm **not **running the upgrade via a ssh session.

As I'm not familiar with Linux in general, the immediate problem is, how to stop the upgrade process without breaking anything as a simple [COLOR=#111111][FONT=Consolas]Ctrl+C[/FONT][/COLOR] won't do it. Another, basically identical machine stops at the exact same point during the upgrade process.
Any ideas on how to narrow down the problem?

---

### Post by Bashing-om on 2015-12-17
Deeks22; Hello;

As always the foundation is what does the package manager report ?

These reports start with what :
```

sudo apt update
sudo apt upgrade

```
advise.
Please post these outputs - Between code tags . We then see where to start looking for the fault(s) .

[INDENT]together
[INDENT][INDENT]we can
[/INDENT][/INDENT][/INDENT]

---

### Post by Deeks22 on 2015-12-18
For some reason, the machine went through with the upgrade today. Unfortunately, I can't tell what was the problem in the first place. 
However, I went on and did a full release upgrade afterwards, which resulted in the machine being "bricked" due to this bug [http://ubuntuforums.org/showthread.php?t=2300859&p=13401065#post13401065](http://ubuntuforums.org/showthread.php?t=2300859&p=13401065#post13401065)
Therefore I had to setup the machine again from scratch, now as a 15.10 Ubuntu.

However, I'd still like to know, how to abort an upgrade that got stuck/froze, without breaking anything.

---

### Post by Bashing-om on 2015-12-18
Deeks22; Yeah !

That nuclear solution always works !  But, I must say in my opinion that solution is for wussies, and those short on time . Often faster to (RE-)install than to find and fix.

As to the why in you last episode, tough to make a call with out seeing the terminal outputs and examining the log files. The finger of suspicion is pointed at proprietary software from 3rd party sources .

As to:
> 
how to abort an upgrade that got stuck/froze, without breaking anything.

Again there is no one nor an easy answer . Time and experience to know when and what is hanging and what to do to recover at some point where the update process was when the hang up happened .

Open another terminal may be of great help to "look" at things.
A key combo ctl+c to terminate a present process might be acceptable, depending on what stage the process is at . And then examine to see the cause of the hang. There is a reason, just maybe not so easy to find ( the system will at least give hints as to why and where) and may not be so easy to fix. It all just depends.

[INDENT][INDENT]the more complex
[INDENT][INDENT][INDENT][INDENT]the more difficult to find
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

