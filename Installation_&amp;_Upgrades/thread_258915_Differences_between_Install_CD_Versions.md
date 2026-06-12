---
title: "Differences between Install CD Versions"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by daxelrod on 2006-09-16
Is there a simple way to determine, preferably while booted from the desktop (or alternate install) CD if the CD contains Ubuntu 6.06 or 6.06.1? It appears that all the documentation on the 6.06.1 CD refers to itself as 6.06.

Also, is there a comprehensive list of changes in 6.06.1 from 6.06?

One of the reasons I'm curious is that I think I remember reading that there have been changes to the installer from 6.06 to 6.06.1.

Thank you!

---

### Post by mostwanted on 2006-09-16
The changes between 6.06 and 6.06.1 are bug and security fixes. You can't really make a feature list, it would be an incredibly boring read :)

It doesn't matter if you install 6.06 or 6.06.1 - downloading the batch of updates in the update manager will upgraade you to the latest version of Dapper right away anyway.

---

### Post by daxelrod on 2006-09-16
> **mostwanted said:**
> downloading the batch of updates in the update manager will upgraade you to the latest version of Dapper right away

My concern is fixes that were made **to the OS installer itself**. You're saying that if I run the update manager on the livecd prior to installation, it will update the installer? What would you recommend doing on the alternate install CD?

> **mostwanted said:**
> You can't really make a feature list, it would be an incredibly boring read :)
You underestimate my capacity for geeky fascination. :)

---

### Post by mostwanted on 2006-09-16
> **daxelrod said:**
> My concern is fixes that were made **to the OS installer itself**. You're saying that if I run the update manager on the livecd prior to installation, it will update the installer? What would you recommend doing on the alternate install CD?

Erh, no obviously that's not possible ;)

Any changes there might have been to the installer have been small bug fixes. Doesn't the installer on 6.06 work on your computer? Is that the problem?

If you're seeking major changes, wait until version 6.10 is out (it will be in a month).

---

### Post by daxelrod on 2006-09-16
> **mostwanted said:**
> Erh, no obviously that's not possible ;)
I could see it being possible from the livecd, because it uses unionfs.

> **mostwanted said:**
> Doesn't the installer on 6.06 work on your computer? Is that the problem?
I haven't seen any problems with the installer yet (because I haven't actually installed just yet), but I figure it's probably a good idea to install from the most-bugfixed version of the installer. :)

---

### Post by mostwanted on 2006-09-16
> **daxelrod said:**
> I could see it being possible from the livecd, because it uses unionfs.

Hm, well now when I think about it, there's a chance that might be possible. Of course, an updated Update Manager is probably gonna need a ton of dependencies as well so if it's possible to do something like that you'd still need a good deal of RAM.


> **daxelrod said:**
> I haven't seen any problems with the installer yet (because I haven't actually installed just yet), but I figure it's probably a good idea to install from the most-bugfixed version of the installer. :)

Yeah, but if it works anyway? :) I haven't had problems with the 6.06 installer since the late alpha versions of it.

---

### Post by daxelrod on 2006-09-16
> **mostwanted said:**
> Of course, an updated Update Manager is probably gonna need a ton of dependencies
Just to be clear, I'm talking about bugfixes to the program that does the initial install of Ubuntu, not apt or Update Manager.
> **mostwanted said:**
> Yeah, but if it works anyway? :) I haven't had problems with the 6.06 installer since the late alpha versions of it.
I have seen posts from others with very similar hardware to mine indicating I might have a problem with the original 6.06 installer. Thank you for your vote of confidence as to its effectiveness, however.

I don't mean to sound unappreciative of your help (it's been both extremely fast and informative, and I thank you for that) but I'm still looking for an answer to my original question. A doc pointer to the differences between 6.06 and 6.06.1 might do the trick, but I seem to be unable to find so much as a changelog.

---

### Post by mostwanted on 2006-09-16
> **daxelrod said:**
> Just to be clear, I'm talking about bugfixes to the program that does the initial install of Ubuntu, not apt or Update Manager.

I have seen posts from others with very similar hardware to mine indicating I might have a problem with the original 6.06 installer. Thank you for your vote of confidence as to its effectiveness, however.

I don't mean to sound unappreciative of your help (it's been both extremely fast and informative, and I thank you for that) but I'm still looking for an answer to my original question. A doc pointer to the differences between 6.06 and 6.06.1 might do the trick, but I seem to be unable to find so much as a changelog.

Sorry, yes I meant the installer of course :)

I'm not sure where you'd get a changelog. And also, the changes between 6.06.1 and 6.06 are very numerous but also very small and usually come from upstream, so it's difficult to track changes and make an actual changelog.

If it can narrow down your search, you need to find changes for "Ubiquity" which is the name for the Ubuntu installer.

---

### Post by daxelrod on 2006-09-16
Thanks, that does help a little.

I was able to find [the 6.06.1 release announcement]("http://www.ubuntuforums.org/showthread.php?t=233444"), but it doesn't have quite enough information to tell me how to determine the difference between 6.06 and 6.06.1.

I guess I could look for versions of ubiquity released by the data of the announcement, and look at the version number for ubiquity on the livecd.

---

### Post by daxelrod on 2006-09-18
The 6.06.1 desktop CD, if you press F1 immediately upon seeing the Ubuntu logo and before boot, it displays "This is a live CD-ROM for Ubuntu 6.06 built on 2006.08.06.1".

If you do this with the 6.06 desktop CD, it says it was built on "20060531."

---

### Post by daxelrod on 2006-09-30
I've since noticed that the CDs sometimes mount on other OSes with a label that tells you if they're .1 or not. After more experimentation, I'll write up a Howto for this.

---

