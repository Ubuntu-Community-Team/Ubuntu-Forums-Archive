---
title: "disco to focal not supported with this tool"
date: 2020-10-02
forum: Installation &amp; Upgrades
---

### Post by josephfg on 2020-10-02
Hi.  I am trying to upgrade to the latest version of Ubuntu.  I am running it on an HP laptop.  I have some screenshots.

I tried to go through the updater, I got to the upgrade screen,  authenticated, but then it gave the message that is the subject line of  this post: "An upgrade from 'disco' to 'focal' is not supported with  this tool."

What shall I do?

---

### Post by CelticWarrior on 2020-10-02
You should do your backups if not done already and install from scratch, not upgrade, because it isn't possible (by normal ways).
19.04 is EoL and could only upgrade to 19.10, also EoL, an from there finally to 20.04.

---

### Post by CelticWarrior on 2020-10-02
And you should know that very well already: [https://ubuntuforums.org/showthread.php?t=2435464](https://ubuntuforums.org/showthread.php?t=2435464)
Advice from expert users should NOT be dismissed with a "[COLOR=#000000]I am pretty new to all this" and then come back 9 months later like that conversation never existed.[/COLOR]

---

### Post by ajgreeny on 2020-10-03
If you're  sure you want to risk the possible problems, and provided you have good, usable backups of all your important personal files, you could try manually editing the /etc/apt/sources.list file, replacing every instance of disco with focal then running the update and upgrade commands.

I suspect this will leave you with an OS that is unstable and possibly unusable, but you may have learned useful lessons by the end.

However, I would also recommend biting the bullet and doing a clean install. Don't forget, you still must have those good backups before starting!

---

### Post by josephfg on 2020-10-05
@ajgreeny, fortunately I did not have to go that route.
@CelticWarrior, thank you for calling me out on my ignorance of the past.  I found out the hard way.  I did not realize how key it is in Linux to use the up-to-date release.  i have another machine, so fortunately I was able to create a bootable thumb-drive with that.  Otherwise, I'd have been in big trouble!  Over the course of time, after Disco was discontinued, the performance went steadily downhill until I finally decided to upgrade.  OK! Lesson learned.  From now on, I keep it up to date.  Thanks!

---

### Post by CelticWarrior on 2020-10-06
Any OS and within it software like web browsers must be kept up to date.

---

