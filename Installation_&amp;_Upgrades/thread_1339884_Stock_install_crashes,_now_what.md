---
title: "Stock install crashes, now what?"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by jessiebrownjr on 2009-11-28
Back when karmic first came out, I attempted to install it on both my computers, but it failed for various reasons.. my question is, will I always have the same results if I attempt to use the ISO for a fresh install or upgrade, or has anything been changed on the ISO?

For instance on my desktop, I couldn't get the new kernel to work with 9.10, but when I loaded into the older kernel with 9.10 stuff, everything but the sound worked...

what are my options besides using the 9.04? One thing I tried was booting into the recovery portion and doing sudo apt-get upgrade. It would download upgrades etc, but it didn't fix my problem. 

Not really sure how to proceed..  Is the ISO thats published from released always going to be the same, or is it ever upgraded to fix bugs?

---

### Post by lemming465 on 2009-11-29
The long term support releases do get new ISO spins periodically, e.g hardy heron is up to 8.04.3.  Unless there is something hideously dire, the 6-month releases tend to just get replaced by the next version, rather than re-spun.  If a 9.04 install works, but not a 9.10 install, you could try doing a 9.04 install followed by *sudo update-manager -c* to do an upgrade in place.  That would pull down the later versions of the 9.10 packages than you'd get off the 9.10 install CD's, which might fix your problem.  However, since you said that *apt-get upgrade* didn't help, I'm not optimistic about that.  Is there a problem with just running 9.04 for a while?  It's fully supported for another year, after all.

---

### Post by jessiebrownjr on 2009-11-30
I'm not sure if I ran a fresh install on my system last time.. I'm also confused because im 99.9% sure I checked the ISO/media before I tried to boot last time off the 9.10 live CD to test it out last time. I downloaded the KDE version of 9.10 recently this time. Burned, booted and it worked. I'm hesistant to install for obvious reasons. I was thinking that maybe my desktop upgrade(i upgraded last time for sure that failed) failed because of Nvidia drivers that I had installed last time because it would Hang before X started and just give me a blank screen. Are there any fundamental differences that would cause a KDE install to work, but not a gnome upgrade (besides that driver issue I have a sneaking suspicion about)?

There isn't any downfalls to me sticking with 9.04, I've done a bit of work with it lately and got it how I like it, but I like the "latest and the greatest" for random reasons hehe.

---

### Post by lemming465 on 2009-11-30
You can always re-check a CD to see if it validates again, in case of doubt.  If a 9.10 live CD passes validation and runs all of your devices the odds are good that an installed version from that CD will too.  Not 100%, but very good.  I like to test with a live CD before upgrading just for that reason.

There isn't likely to be a difference in device support between Gnome and KDE versions; they use the same kernel, same pulseaudio, and same X server underneath; it's just the look & feel that is different.

Unfortunately, the combination of pressures on the Linux video landscape is leading to a lot of trauma currently, and it will be 2012 or 2013 before it all shakes out.  Most distributions are moving toward "kernel mode setting", for a variety of good reasons.  X device drivers are trying to add 2D and 3D acceleration features, and switch from proprietary binary drivers to open source drivers.  There is a lot of churn under the hood, and one can't take for granted that just because X worked in a previous release that it still does in a new one.  Usually it gets better for most people, but worse for a justifiably annoyed minority.   E.g. with Ubuntu 9.10, somewhere around alpha 5 or alpha 6 they broke the ATI video on a Toshiba satellite A215 laptop I have.  I reported the bug in launchpad, and it was fixed for me by the beta, but not everyone has been so lucky.

---

### Post by jessiebrownjr on 2009-12-01
> **lemming465 said:**
> You can always re-check a CD to see if it validates again, in case of doubt.  If a 9.10 live CD passes validation and runs all of your devices the odds are good that an installed version from that CD will too.  Not 100%, but very good.  I like to test with a live CD before upgrading just for that reason.

There isn't likely to be a difference in device support between Gnome and KDE versions; they use the same kernel, same pulseaudio, and same X server underneath; it's just the look & feel that is different.

Unfortunately, the combination of pressures on the Linux video landscape is leading to a lot of trauma currently, and it will be 2012 or 2013 before it all shakes out.  Most distributions are moving toward "kernel mode setting", for a variety of good reasons.  X device drivers are trying to add 2D and 3D acceleration features, and switch from proprietary binary drivers to open source drivers.  There is a lot of churn under the hood, and one can't take for granted that just because X worked in a previous release that it still does in a new one.  Usually it gets better for most people, but worse for a justifiably annoyed minority.   E.g. with Ubuntu 9.10, somewhere around alpha 5 or alpha 6 they broke the ATI video on a Toshiba satellite A215 laptop I have.  I reported the bug in launchpad, and it was fixed for me by the beta, but not everyone has been so lucky.

Yeah my laptop's intel chipset driver wouldn't let me run the beta or the newest xorg update for a long time because it was broken...

---

### Post by jessiebrownjr on 2009-12-01
ok, I got home and burned the GNOME version of 9.10 verified it and attempted to boot off live.. it is indeed crashing in the same spot my upgraded version of 9.10 was.. it starts to load Gnome/x.. it is stuck with the circular cursing that isn't moving, looks like its stuck in place.. The screen behind the cursor is black/white checker mini pattern or just gray I guess you could say. 

im pretty sure I posted this earlier but the KDE version of 9.10 booots perfectly.. What is the difference folks? I must know! :-)
I'm not familiar with KDE but I'm tempted just to install it because of this issue.

I have a working install of 9.04, I don't want to risk installing this and doing terminal upgrades (unless anybody knows if that fixes it). Anybody have any knowledge about this subject, or some command line guru info that I can type to find out what is going on? Thanks in advance..!

---

### Post by jessiebrownjr on 2009-12-02
yawn, the disc checks out for no errors (twice) but it keeps crashing on the partition manager... Now what :-(

---

### Post by lemming465 on 2009-12-04
If Gnome is dying but KDE is OK, I'm suspicious that Compiz is messing up.

---

### Post by lemming465 on 2009-12-12
Crashing on the partition manager is unusual.  Have you tried running memtest86+ for a while (at least 20 minutes, maybe overnight) to see if you have any flakey memory?

---

