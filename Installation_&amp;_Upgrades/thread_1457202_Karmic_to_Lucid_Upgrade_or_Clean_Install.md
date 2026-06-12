---
title: "Karmic to Lucid: Upgrade or Clean Install ?"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by RavanH on 2010-04-18
Hi,

In earlier years, everybody seemed to be giving the advice: When upgrading, do a clean install to get the most out of your new Ubuntu version and not screw up your data with a flaky upgrade process.

Is this still true or is the upgrade process so advanced by now that there is not much difference between the two approaches?

I have been using Ubuntu for a few years now and have tuned and tweaked my current Karmic to be just the way I like it. Added lots of new software that I use frequently (like Opera and other stuff that is not in Ubuntu's repos) ... so I 'd prefer to go for an upgrade. 

Unless that will not yield the benefits that Lucid promises !

Anxious to move forward to Lucid, any advise on how to do that best, will be appreciated :)

---

### Post by tommcd on 2010-04-18
> **RavanH said:**
> 
In earlier years, everybody seemed to be giving the advice: When upgrading, do a clean install to get the most out of your new Ubuntu version and not screw up your data with a flaky upgrade process.
Doing a clean install is the method I prefer. You start with a clean slate; and this is the most fail safe method for upgrading since you old install is wiped clean in the process.
Id you have a separate home partition, then all your data is safe when doing a clean install. If you do not have a separate home partition, then this would be an ideal time to create one.
> **RavanH said:**
> 
Is this still true or is the upgrade process so advanced by now that there is not much difference between the two approaches?
Many people do dist-upgrades without problems. Others encounter multiple problems. Personally, I believe that the main reason so many people have problems is because they have installed multiple 3rd party repos into their sources.list. This includes the ppa repos. Trying to carry all these 3rd party repos through a dist-upgrade seems to be a recipe for disaster.
Note that it is recommended that you should remove 3rd party repos before doing a dist-upgrade:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)
Almost *nobody* does this though. Then they blame Ubuntu for problems they have inadvertently brought upon themselves.
> **RavanH said:**
> 
I have been using Ubuntu for a few years now and have tuned and tweaked my current Karmic to be just the way I like it. Added lots of new software that I use frequently (like Opera and other stuff that is not in Ubuntu's repos) ... so I 'd prefer to go for an upgrade. 

Please understand that doing a clean install becomes easier, and goes a lot faster the more you do it. I can do a clean install, get all the updates, reinstall all the programs I use, and set things up the way I like it in about 90 minutes ... at the most. And most of this time is spent waiting for stuff to happen. During this time I can do other things, like answer threads in the Ubuntu forums!

What I would do:
First, download and burn a Lucid CD when Lucid stable is released. Then try doing a dist-upgrade from Karmic to Lucid. If the dist-upgrade works, and you have no problems, then all is well. If you find that you are facing a multitude of problems after the upgrade, then don't waste your time trying to fix it. Just do a clean install from your new Lucid CD.

---

### Post by snowpine on 2010-04-18
You can upgrade with one click in the Update Manager, once Lucid is released later this month. :)

---

### Post by shaka_zulu on 2010-04-18
I vote for clean install. I had negative experience with upgrading. It doesn't mean that this new versions will not bring improvements but you should wait to read comments a few days after official release.

---

### Post by RavanH on 2010-04-18
> **shaka_zulu said:**
> I vote for clean install. I had negative experience with upgrading. It doesn't mean that this new versions will not bring improvements but you should wait to read comments a few days after official release.

That is always a good idea. Of course I already tried the beta2 LiveCD and apart from having to install linux-firmware-nonfree seperately to get networking (I only have a ZyXEL ZyAIR cardbus wireless card), I am rather confident Lucid will be a big improvement on my laptop.

---

### Post by RavanH on 2010-04-18
> **tommcd said:**
> Doing a clean install is the method I prefer. You start with a clean slate; and this is the most fail safe method for upgrading since you old install is wiped clean in the process.
Id you have a separate home partition, then all your data is safe when doing a clean install. If you do not have a separate home partition, then this would be an ideal time to create one.

Many people do dist-upgrades without problems. Others encounter multiple problems. Personally, I believe that the main reason so many people have problems is because they have installed multiple 3rd party repos into their sources.list. This includes the ppa repos. Trying to carry all these 3rd party repos through a dist-upgrade seems to be a recipe for disaster.
Note that it is recommended that you should remove 3rd party repos before doing a dist-upgrade:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)
Almost *nobody* does this though. Then they blame Ubuntu for problems they have inadvertently brought upon themselves.

Please understand that doing a clean install becomes easier, and goes a lot faster the more you do it. I can do a clean install, get all the updates, reinstall all the programs I use, and set things up the way I like it in about 90 minutes ... at the most. And most of this time is spent waiting for stuff to happen. During this time I can do other things, like answer threads in the Ubuntu forums!

What I would do:
First, download and burn a Lucid CD when Lucid stable is released. Then try doing a dist-upgrade from Karmic to Lucid. If the dist-upgrade works, and you have no problems, then all is well. If you find that you are facing a multitude of problems after the upgrade, then don't waste your time trying to fix it. Just do a clean install from your new Lucid CD.

Thanks for your elaborate response, Tom. I do indeed have (and always had, glad to say - why the installer does not do that by default, i really do not understand) a separate home partition. So a clean install will not pose too much trouble. It is just that an upgrade would be even simpler because - as you mention - I have several other repos in my sources list that keep me up to date for other software like Opera or Picasa and such...

So I understand that is precisely what I should be worried about? Hmmmm... Thanks for the warning. I think I will take your advise to heart and first download and burn a LiveCD (of the stable release, I tried beta2 already with good results) and then try a dist-upgrade with all the "alien" repos removed :)

---

### Post by fugitivo82 on 2010-05-02
@RavanH: I totally understand your situation. Some days before I do a dist-update. I have to tell you I don't find a problem, but (a important "but") now I have to configure again 3rd part's and ppa's repos.

---

### Post by RavanH on 2010-05-03
Well, I did a dist-upgrade too and all external repo's got switched off before the process started so no problems there. Only thing is that after the upgrade, I started having random lock-ups. Not the kind of X-freezes I have my another laptop - an ASUS M24N - when not using nomodeset and nolapic boot options plus the mesa video driver instead of the intel one but complete system lockups. No response at all just have to use the on/off button to make it reboot. 

So I decided to go for a clean install but sadly, the lockups happened again. Just extremely random. No telling what-so-ever why this is happening. Nothing written in the log files just before they happen. 

Frustrating :(

The only thing that might be related it that Hibernation / Suspend to RAM is not working anymore and causes a similar lock-up when activated. Rebooting the system comes back up without networking.

Will have to investigate further... Anyway, thanks for the tips, guys!

---

### Post by Steam. on 2010-05-03
Clean install.My upgrade always gets stuck at "preparing memtest 86+" so i delete everything and download a new .iso.

---

### Post by tgalati4 on 2010-05-03
Well, it's too late now, but I advocate dual-boot.  Buy a new hard disk if you need the space, but having your working Karmic on a separate partition would have saved you some headaches.

That way you get a clean install of Lucid (whether it works or not).  You data is still intact with the existing Karmic installation.  You can always access your data in Lucid from the Karmic partition.

If Lucid doesn't work, then wait for patches to be released in a few months and use your existing Karmic installation in the meantime.

---

