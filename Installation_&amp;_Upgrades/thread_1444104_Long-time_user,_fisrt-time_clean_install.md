---
title: "Long-time user, fisrt-time clean install"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by LeBurt on 2010-03-31
Hi all,

I've been using Ubuntu since Gutsy Gibbon and have always upgraded when new releases came out. Every now and then however I read that people prefer a clean install over an upgrade (although the reasons are never quite clear). Also, I'm tempted to try KDE for a change and therefore am thinking I'll switch to Kubuntu, even if only for one release. With 10.04 around the corner, now's the time to start thinking about it.

Has anyone had a bad experience with a clean install on top of an existing one? I mean, you can do that, right? Are the home folders well preserved? Other than backing those up, are there any other steps I should take before I scrap everything?

I'd appreciate some hints from people who have been there.

---

### Post by gare on 2010-03-31
hi ,

clean install asfaik refers to wiping your hard drive & installing a new distribution in that space.  

The LiveCD should take care of that for you.  

If you have your /home directory backed up somewhere else, you should be all set! Just copy it back in after the install.


(I am milking a hardy install at work; trying to get it to love the new lucid upgrade with luck so far, but have no real expectations ....)

---

### Post by oldfred on 2010-03-31
See my recent post here on my conversion:
[http://ubuntuforums.org/showthread.php?t=1443814](http://ubuntuforums.org/showthread.php?t=1443814)

I can add additional information if you want.

---

### Post by LeBurt on 2010-04-01
Thanks, I'll look into this.

@oldfred: funny that you wanted to go from KDE to Gnome while I'm contemplating the opposite. What made you want to go that way?

---

### Post by oldfred on 2010-04-01
I installed KDE over the top of my Ubuntu and just did not like it. I never was able to total uninstall it as I like K3b and kmymoney so I still have a lot of KDE libraries that I need. I may reinstall in one of my spare partitions to try it again but it is not a priority.

---

### Post by tommcd on 2010-04-01
> **LeBurt said:**
>  Every now and then however I read that people prefer a clean install over an upgrade (although the reasons are never quite clear).
I am one of those people.
The rationale for doing a clean install instead of a dist-upgrade is that the clean install is the most fail safe method to upgrade your system. This is because you are starting your root partition off from a clean slate, instead of doing all the upgrading that is necessary to get from one version to the next. If you have a separate home partition (as you ideally should) all your data and user settings will be saved, so a clean install is not that big of a deal compared to a dist-upgrade.
There is certainly nothing wrong with trying the dist-upgrade route though. If it works ok for you then all is well. However, many people spend many days or even weeks trying to fix a multitude of problems with botched dist-upgrades with little success. 
(I believe that many, if not most, of these problems are caused or exacerbated by all of the third party repositories that so many people seem to be compelled to add to their systems). 
references:
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
These people would be better off with just doing a clean install imo.

---

