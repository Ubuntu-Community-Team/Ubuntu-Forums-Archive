---
title: "Bottom line: to upgrade or to reinstall, that is the question!"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by pmilin@ptt.yu on 2006-06-10
For those of us who are not experts, what would be recommendation, to upgrade from 5.10 to 6.06 or to, simply, make a clean, fresh install of 6.06?
I saw both good and bad experiences (check, for example: [http://ubuntuforums.org/showthread.php?t=187024)](http://ubuntuforums.org/showthread.php?t=187024)), and now I am confused, not capable to decide.

Best,
[email]pmilin@ptt.yu[/email]

---

### Post by BitTorrentBuddha on 2006-06-10
Try the upgrade first, if it runs sluggish then go for the reinstall, or if you don't have a lot of space on your hard drive/partition just go for the reinstall to be sure you aren't keeping unnecessary files.

---

### Post by pmilin@ptt.yu on 2006-06-11
So, if I upgrade I could expect to have garbage and/or unnecessary file? Is it possible, if upgrade would be a success, to clean everything up?

pmilin

---

### Post by BoomAM on 2006-06-11
Question:
Is the 'upgrade' function in Ubuntu in the same vain as a Windows upgrade, ie theres a high chance of having alot of rubbish left from an old version that could potentially slow down the system? Or is it 'cleaner' than that?

---

### Post by pmilin@ptt.yu on 2006-06-12
That is the very question I am wandering about. However, beside garbage in the case of successful upgrade, there is even more fundamental question regarding ratio of success vs. failure in upgrading.
Although I am now almost all the time in Ubuntu (leaving Windows for unhappy creatures), I would consider problems in upgrading as serious withdraw: it ought to be advantage of linux!?!

pmilin

---

### Post by aysiu on 2006-06-12
The likelihood of success in upgrade is directly related to how close your installation is to the default installation.

If you install Breezy and do nothing to it (remove no programs, add no programs), then you'll have very close to a 100% chance of a successful upgrade to Dapper.

The more you fiddle around with things, especially if you remove the *ubuntu-desktop* or *kubuntu-desktop* packages before upgrading, the less likely you will be to have a successful upgrade (I'm guessing, but I'd say the likelihood could drop as low as 60%).

Of course, a lack of success doesn't mean you can't use your computer. It usually just means that you have to reconfigure X or reinstall your locales or change a configuration file somewhere.

Upgrades in Linux tend to be unstable, as they happen more frequently (most major distros have upgrades twice a year) than Windows upgrades. Also, Windows isn't as flexible, so you're probably very close to the default installation, even if you have added a few programs.

That said, upgrades in Windows and Mac are not always that painless. [Here's a story about my wife's upgrade from Panther to Tiger](http://ubuntuforums.org/showthread.php?t=80341).

---

