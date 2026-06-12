---
title: "Software updater acting a bit strange"
date: 2016-02-09
forum: Installation &amp; Upgrades
---

### Post by PaulBx on 2016-02-09
I'm on 14.04 LTS; today the updater wanted a 15.10 CD/DVD even though I have notifications in "Software & Updates" set to notify me for LTS versions only.

I probably don't want to go to 15.10 as I heard the update path is arduous. I hope the update directly to 16.04 LTS is not too bad.

I've read people saying not to update at all, but to do a fresh install. I hope that if an update is offered, it works. I don't have a separate /home partition so a fresh install looks difficult to me. Maybe I could rearrange things but I have everything encrypted so I'd just prefer to leave as is.

Anyway I am wondering if I should just ignore Software Updater until 16.04 LTS is available, since I want nothing to do with 15.10.

---

### Post by kansasnoob on 2016-02-09
Did you add something from a 15.10 live DVD at some point? Maybe have a look at software settings and see if it's looking for software from such a source:

[ATTACH=CONFIG]267219[/ATTACH]

Had you recently followed some nefarious tutorial?

---

### Post by Bucky Ball on 2016-02-09
As kansasnoob mentions, I was wondering if you have the 15.10 install media ticked somewhere. In any case, ignore the Software Updater. No idea why it's doing it, but you don't want to go there. Wait for 16.04 LTS. If you do have the 15.10 install media ticked, untick. 

The 'whether to upgrade or clean install' is under perpetual debate and you will hear it all if you open that jar. I, personally, have never had an issue with one, but I run a fairly 'vanilla' system with maybe one PPA installed manually. Switch off all PPAs you've installed, try and get to fairly vanilla, do an update/upgrade of your system prior to the upgrade would be my only advice there.

(Apart from BACKUP all valuable data. You say if you need a clean install it would be a hassle because you don't have a separate /home partition? It makes no matter whether you do or don't, you only have one copy of your valuable data and that is not good. You need to work out someway of doing regular backups quite apart from your support request or anything to do with upgrading. You have no backup of your data right now and if that drive dies right now so does your data. Advise you start saving and get an external hard drive or large USB dongle.)

---

### Post by grahammechanical on 2016-02-09
Are you sure Update Manager is asking for a 15.10 CD/DVD and not offering to upgrade to 15.10? I think that some have been seeing that offer. If so, ignore it. Ubuntu 15.10 only has 9 months support which started in October. So, if we are on 15.10 we will need to upgrade to 16.04 in the summer. That will be 2 upgrades for any one on 14.04.

If we are on 16.04 we can upgrade directly to 16.04 a few weeks after it is released. That means only one upgrade. Of course, 14.04 still has years of support left. So, there really is no hurry to upgrade.

Regards.

---

### Post by PaulBx on 2016-02-10
It was ticked. Sure don't know how it got that way. I unticked it and it complained:
"The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software."

Not sure what that means...

Of course I do backups, image backups of the whole drive. I'm not reckless...  :)

> Are you sure Update Manager is asking for a 15.10 CD/DVD and not offering to upgrade to 15.10?

The verbiage was, "CD/DVD 'Lubuntu 15.10_Wily Werewolf_-Release AMD64 (20151021) is required"

I installed a few things a week ago, maybe they are new in 15.10 or something. mpt-tools, pv:amd, htop... Oh well, probably not that important. Anyway with that 15.10 unticked, software updater now works as expected.

---

### Post by vasa1 on 2016-02-10
> **PaulBx said:**
> It was ticked. Sure don't know how it got that way. I unticked it and it complained:
"The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software."

Not sure what that means...
That's not a complaint. It's a simple statement telling you to reload for the change(s) you've made to take effect. Somewhat like the "Apply" button seen in other programs.

---

### Post by Bucky Ball on 2016-02-10
You should agree to do the update when you change anything in Software and Updates. Do an update now is best.

---

