---
title: "Why Upgrade from 12.10 LTS?"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by rojik on 2013-05-03
Is there any advantage to stayng with 12.10 LTS for the typical non-business home user?  Can I upgrade in place keeping all my config customization etc (excepting the workspace launcher button).  Will graphics supprt remain for AMD Radeon A4 APU?  It was a struggle getting this system to run so I have "concerns".

---

### Post by 2F4U on 2013-05-03
First of all, 12.10 is NOT LTS but a regular release. The LTS release is 12.04. Even for a home user it can make sense to stay with a LTS release. All new Ubuntu release have a reduced support period of 9 month (down from 18 month), which will cause more frequent upgrades. So, if you prefer to stay longer on one release, it can make sense to stick with a LTS release.
In theory, you can upgrade from every supported release to the next one in place. I leave it to you to look through the forum on how successful these attempts are. As always, success or failure depends on your particular configuration.

---

### Post by grahammechanical on 2013-05-03
Why indeed? Do you want to upgrade every six months? Anyone who installs 13.04 will need to upgrade to 13.10 and then 14.04 because those two versions only have 9 months support. You cannot directly upgrade to 13.04. You have to upgrade to 12.10 first. With 12.10 you can be supported until 14.04 comes out and then you will have to upgrade to 14.04.

As you can see from this forum, upgrades are not as successful as people want them to be. This is why many of us who reply to questions like this recommend the LTS release and a fresh install as a way of upgrading.

You are right to have concerns. I have concerns about Nvidia drivers. I would not upgrade with a proprietary driver activated or with a system that has been modified to a large extent. Who can say if the upgrade will keep all your configuration changes? The upgrade is designed to go from default install to default install.  Most certainly disable any PPAs that you have put in and get the system back to a default set up as possible.

Regards.

---

### Post by slickymaster on 2013-05-03
Keep in mind that Canonical will support Ubuntu 12.04.x 32 and 64 bit LTS until April 2017. This means that if you plan to keep your PC hardware over a long period of time, then you should stick with Ubuntu 12.04.x LTS.

If you keep upgrading to newer Ubuntu versions, then you will increase the chances of breaking some stuff. The other thing is that you'll be upgrading every 6 months to 18 months to stick with a currently supported Ubuntu release if it is not a LTS release. You should weigh the options carefully and determine what is best for your situation.

Downgrading to an older version of Ubuntu can be done, but it is better to make a decision to stick with a specific version so long as it is currently supported over a longer period of time.

---

### Post by BcRich on 2013-05-03
I tend to agree with [COLOR=#000000]grahammechanical[/COLOR], upgrading is taken waaaay tooo litely. There are so many factors that could damage your system, make it unusable or unstable that I would not recommend upgrading. If you really want to use 13.04 I'd recommend a vanilla install on a separate partition to your current working system. If you have proprietary graphics drivers in use there is an even bigger risk involved take a look at the headings of the week's posts on this forum and you'll find lots of people uncertain of what to do regarding AMD driver issues with upgrades (myself included). It's worth considering that the promises of speed increases that come from people pushing 13.04 will probably come at the expense of taking hours of your time to get your system back to the way it was.

---

### Post by fantab on 2013-05-03
> **rojik said:**
> Is there any advantage to stayng with 12.10 LTS for the typical non-business home user?  Can I upgrade in place keeping all my config customization etc (excepting the workspace launcher button).  Will graphics supprt remain for AMD Radeon A4 APU?  It was a struggle getting this system to run so I have "concerns".

Advantages to staying with 12.04 LTS (supported until 2017) is that you don't have to upgrade until 2017 or at least until 2014 when the next LTS will be released.

I, personally, never upgrade from an existing Ubuntu to a New Version, instead I download the New version, burn it to a disk, and do a Fresh Install. Also I have two 20GB "/" partitions dedicated to Ubuntu. On one I have a LTS (12.04) and it stays there until next LTS release. On another partition I have the Latest Ubuntu version.

It is possible to upgrade and 'restore' your configs and customizations, if you learn how to BACK UP necessary files and restore them after upgrade. [Read Here]("http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330") to know what to back up.

---

### Post by monkeybrain2012 on 2013-05-03
Advantage to upgrade (actually I recommend fresh install) is that 13.04 is a lot faster (for me), but that depends on your hardware of course. It comes with newer software (which is not a big incentive for me as I get  the latest software for what I use from ppas and self compiling anyway)

Disadvantage is that it is  going to be supported for only 9 months and it will suck if 13.10 turns out to be a stinker and I have to downgrade back to 12.04 

BTW, no more upgrading (or fresh install, whatever) every 6 month, the transition from one non LTS to another is apparently going to become "rolling" (sort of) so you only need to update your software sources,though I haven't looked into the details.

Also, I have both 12.04 and 13.04 on external hard drives and/or different partitions. Will be moving some production stuffs to 13.04 and keeping them in sync with what I have in 12.04. Never put all my eggs in one basket since I like to test different distros and versions. :)

EDITED: If you need to keep your settings, instead of doing "upgrade", make a separate /home partition so when you do a fresh install (that will eventually happen if not now), do not touch it (just reinstall over the / partition) You should also remove obsolete settings from your configuration files before you do that. "Upgrade" tends to be disastrous  if you have modified your system by installing from ppas and installing proprietary drivers, third party software etc. And "upgrade" also takes a long time during which many things can go wrong: if internet stops working or your dog unplugs the power chord during it you are toasted.

---

### Post by rojik on 2013-05-03
For whatever reason I failed to notice that 12.10  is not LTS.  Please point me to a faq or primer on how to roll back to  12.04. I think I made a serious mistake.  This continuous version chrning is antitetical to my concept of practical stability.

---

### Post by monkeybrain2012 on 2013-05-03
There is no rolling back as far as I know. Back up your files (or your home directory) and make a fresh install is the only way to go (as far as I know)

---

### Post by silvagroup on 2013-05-03
Have been using Ubuntu since 7.04 and my experience has been that everything after 11.10 upgrades will increasingly trash your system, and 13.04 is stirctly alpha. I know it's released but I have not been able to get it working. Well that also pretty much goes for everything past 12.04 again just varying levels of screwing things up.
Thank goodness I still had (hate to admit this) Windows installed on one PC or else I would be pretty much without any completely functional systems.
The one good thing Connical has going for them right now is Linux Mint it works far better than any of the latest Unbuntu renditions.
Will soon be testing a Debian install hoping that it is stable.
So if your system is functioning at 12.04 LTS stay there !!!!!!!!
My 2 cents worth.

---

### Post by fantab on 2013-05-03
> **monkeybrain2012 said:**
> There is no rolling back as far as I know. Back up your files (or your home directory) and make a fresh install is the only way to go (as far as I know)
+1.
However, my suggestion will be to create another partition, if you can, of about 20-25GB and install 12.04 on it.

---

### Post by rojik on 2013-05-04
Asolute Agree with you but now I'm stuck on 12.10.  Ive got four systems running, Three  XP and one Ubu-Linux.  I've been curious about all the good I've been reading about Mint.  Perhaps I can switch to a Mint long term version if there is such a thing.  This cycle of breaking and repairing Linux system upgrades is very psycho.  Very annoying.   I've got better things to do.   XP stability has been miraculous and it does everything well.  I used Win2K ( also a superb OS ) until about 2008, then overlapped XP and XPSP3 since about 2005.  This philosophy of constant chrning every 6 months seems weird.  There is a fallacy among secular "progressive"  techies that arbitrary "newness" and constant novelty, change and roiling of the market is somehow good.  I'd prefer gradual subtle refinement and stability.  This is a fundamental dichotomy in life philosophy.  Now I'm trapped between the death of support for XP and the constant churning of Linux.  And I understand MS wants to convert to a cloud service subscription model which I refuse to participate in.  A stable Linux would would provide about 90% of my general computing needs. If "they" would just leave it alone over five year intervals it would be great. What a farcical age we live in.

---

### Post by ibjsb4 on 2013-05-04
You mention Mint.  Has Gnome_classic been mention?  Looks like gnome2 (Ubuntu 10o4).  It can be installed on 12.04, 12.10 and 13.04 and chosen at login.  To install:

```
sudo apt-get install gnome-session-fallback
```

---

### Post by kurt18947 on 2013-05-04
I tend to think of non-LTS releases as betas.  I know that's not technically true but that's how I think of it. I'm running 13.04 on a few boxes and it's working well for me.  I didn't have much luck with 12.10's stability I suspect due to Nvidia drivers.  I have a 12.04 install that I kept updated but don't 'play' with so I feel I can count on that one when it 'needs to work'.  If my 13.04 install breaks, I'm not up the proverbial creek without the proverbial paddle.

I suspect that Canonical views non-LTS releases as opportunities to release new things like MIR into the wild and get them well tested before incorporating them into the next LTS release.  That seems like a sensible way to do things but if that's the way it works,  it should say to users to not have too much confidence in non-LTS releases.

---

### Post by silvagroup on 2013-05-20
Fantab's suggestion is the way to do it. That's how I knew Mint would work. Tested in a partition first. Did same for 13.04.
Still haveing a few issue with 13.04 but for the most part it's become functional. Hopefully few bugs still existing will also be taken care of with updates. Had to do a fresh install to get 13.04 to work. Update did not do the trick at all. And after sevearl updates it's at least functional.

---

