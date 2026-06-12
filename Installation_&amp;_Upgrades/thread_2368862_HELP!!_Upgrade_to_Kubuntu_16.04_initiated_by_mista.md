---
title: "HELP!! Upgrade to Kubuntu 16.04 initiated by mistake!!"
date: 2017-08-16
forum: Installation &amp; Upgrades
---

### Post by pubalapoub on 2017-08-16
Hi everybody,

I did a terrible mistake this morning (not well awaken) by clicking the button to upgrade my Kubuntu 14.04 to release 16.04, while I was just intending to upgrade some packages :(

As soon as I discovered my mistake, I closed the window that had opened in panic (initial window preparing the distribution upgrade), but a "xenial" process was still running on my machine, so I wisely let it finish its work. Then, a new window opened, telling me that something like 138 packages required upgrade, and asking my permission to install them. I CLICKED "CANCEL" and there I am... totally despaired :(

**I will avoid rebooting my machine considering its current state (what will happen at reboot??) until I get some expert advices from you guys.**

I checked my /etc/apt directory, the contents of the following files/folders have already been updated:

sources.list.distUpgrade
*sources.list.d/*
sources.list

Updated files in /etc/apt/*sources.list.d*/ directory:

mondorescue.sources.list
mondorescue.sources.list.distUpgrade
openrct2-nightly-trusty.list
openrct2-nightly-trusty.list.distUpgrade
opera-stable.list
opera-stable.list.distUpgrade
qtox.list
qtox.list.distUpgrade
steam.list
steam.list.distUpgrade
ubuntu-wine-ppa-trusty.list
ubuntu-wine-ppa-trusty.list.distUpgrade

**What can I do to definitely CANCEL that distribution upgrade?**

And once that's done (crossing fingers...), what would need to be done to go back to the previous version of the above apt (source lists) files?

Many thanks in advance to any of you who will be able to bring assistance in this desperate situation!

---

### Post by Autodave on 2017-08-16
While waiting for an answer from some one more knowledgeable than myself, make sure that you get all of your needed files copied to an external source for safe keeping.

May I ask why you do not want to upgrade to 16.04?

---

### Post by pubalapoub on 2017-08-16
> **Autodave said:**
> May I ask why you do not want to upgrade to 16.04?
Hi Autodave,

several reasons, the most important one being that my PC is equipped with an AMD graphics card (Radeon R7 370), well supported by the previous AMD proprietary driver. As you probably know, AMD started rewriting their driver(s) from scratch last year and from what I understood, my card wouldn't be supported by the new binary driver. Since Kubuntu 14.04 is still supported until April 2019 (and works perfectly well), there is absolutely no urgency for me to upgrade to a more recent distribution (and losing the good support of my GPU in the process).

I don't have much time until next week-end to troubleshoot my current problem (my holidays are over), otherwise I would start gathering infos about the Ubuntu dist-upgrade process on my own, to understand how it works and what was done this morning (that would need to be reverted manually). I know mid-August is not the best period to get help from people who master the topic :) So until I can get support from someone or dedicate time to this issue myself, I can just cross fingers hoping that I won't face a power cut in the next few days... (_update_: read next post of mine)

_Addendum_: another good reason (I believe) for not upgrading is that I don't trust dist-upgrade processes very much. I read about post-upgrade issues so many times that I would preferably go for a fresh install of a new LTS release on a separate disk partition, then copy my personal data from the old partition.

---

### Post by pubalapoub on 2017-08-16
Ok, as 1 mistake wasn't enough in a single day, I've made another  one by shutting down my PC inadvertently (using the keyboard shortcut I  know so well, since I use it every day...) :razz:

 _Outcome_:  my PC / Kubuntu 14.04 started normally. Phew! Now I know I can shut  down my PC without fearing anything bad at restart, that's good news.

I remember reading this morning something like "*third party repositories were disabled and should be re-enabled manually after the upgrade*" to 16.04. Maybe this is the sole reason for some files in /etc/apt  being modified. I'll check this as soon as I have some time to dedicate  to it.

---

### Post by vasa1 on 2017-08-16
Well, all the best! Your reason for staying with 14.04 is spot on.

In any case, I do hope you constantly back up your valuable stuff.

---

### Post by pubalapoub on 2017-08-17
Hi vasa1,

English is not my native language, I guess "spot on" means my reason is a very good one?... :)
Anyway, I was very unhappy at the time discovering soon after the purchase of my gfx card that AMD was breaking everything... and the support of my new card was endangered in the mid to long term. Although AMD's motivation was a good one (release most of their driver's code as open source). I had spent so much time comparing the pros and cons of NVidia vs AMD cards... (including price, Max TDP, OpenGL support...)

As to backing up my data regularly, you're totally right, this is important (Autodave mentioned that point as well). That said, in the context of this thread, I don't fear much since even if the upgrade to 16.04 had been triggered and had failed - in a way or another - there would be  good chances that I could still have access to my personal data (using a live-USB key for e.g. to copy them to another drive). But your recommendation remains valid, anyone should backup his data from time to time. The following point is out-of-scope of this thread, but I've been wondering recently if backup tools _based on rsync_ would work correctly if the destination drive/partition is an NTFS one? I doubt it... but I didn't spend time figuring this out yet. Traditionally, I backup my most important directories manually (keeping several backup copies on the destination drive), which is not the fastest way to backup my data, but at least I keep total control of the backup process. On the other hand, rsync would be much more efficient (backup duration would be shortened for instance).

---

### Post by pubalapoub on 2017-08-17
So I finally took a look at the contents of modified files in /etc/apt. Apart from files which name ends with *.distUpgrade (not existing previously, but being an exact copy of the same file without this extension), **nothing changed**. Even 3rd party repositories are still **enabled**, contrary to my previous understanding. So everything is fine :)

Sorry for the wrong alert... I'll set this thread as "solved".

---

