---
title: "LTS to LTS?"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by snowpine on 2009-12-21
How can I upgrade from 8.04 to 10.04?

Just tried 'do-release-upgrade -p' and nothing happened.
'do-release-upgrade -d' seems to go to Karmic.

(I'm using CrunchBang, if it makes a difference.)

Output of cat /etc/apt/sources.list:

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

I did not think it was possible to go directly Hardy->Karmic without passing through Intrepid and Jaunty?

---

### Post by orlox on 2009-12-21
I believe it's completely possible to upgrade from LTS to LTS directly. However, this requires work for both karmic and lucid that as far as I know, still hasn't been done.

---

### Post by ranch hand on 2009-12-21
I do not believe that is a good thing to try yet at all.

If your Hardy is up to date it is equal to 8.04.3.  There is another "release" coming; 8.04.4.  That will have some added help for that upgrade.

I also am sure that the integration of what ever is needed in 10.04 is not there yet.

Someone, here on this forum, said that they had done the upgrade.  I suppose you could get lucky.

I have Hardy on here and there is no way I am risking it at this point.  When I do try it it will be with a new install of Hardy so I can see if it works before doing it to my current install.

---

### Post by snowpine on 2009-12-21
LTS to LTS is the most important upgrade... get it together, Canonical... clock's ticking! ;)

---

### Post by VMC on 2009-12-21
> **snowpine said:**
> How can I upgrade from 8.04 to 10.04?

Just tried 'do-release-upgrade -p' and nothing happened.
'do-release-upgrade -d' seems to go to Karmic.


Output of cat /etc/apt/sources.list:
...

All your sources.list point to karmic. Have you tried changing to lucid?

---

### Post by snowpine on 2009-12-21
> **VMC said:**
> All your sources.list point to karmic. Have you tried changing to lucid?

My understanding is that Hardy would update to Lucid (not Karmic); that is why I'm confused. :(

---

### Post by wilee-nilee on 2009-12-21
> **snowpine said:**
> LTS to LTS is the most important upgrade... get it together, Canonical... clock's ticking! ;)

Your clock is ticking.

---

### Post by Merk42 on 2009-12-21
> **wilee-nilee said:**
> Your clock is ticking.

snowpine wants a baby?

---

### Post by snowpine on 2009-12-21
:)

---

### Post by ranch hand on 2009-12-21
All that Hardy is going to "see" at this time is 9.10 which is released.  It is not equipt to see 10.04.

If you are really set on this folly, you need to edit the sources.list yourself to read "lucid" at every instance of "karimic".  Then you need t ogo to your terminal and run;
```

sudo apt-get dist-upgrade

```
You should have the terminal at full size so that you can see any problems.  In this case I think so that you can watch an innocent OS go up in flames most likely.

Yes you can update from one LTS to another.  The problem here is that we do not have an LTS for Hardy to update to.  We have an OS, that kind of works most of the time and will, in time BECOME a LTS OS release.  It is not one now and won't be for some time.

It is your box.  I certainly do what I want with mine.

We would all love to hear of the experience.  I would at least as I will be doing this with my "business" OS.

Have FUN.

---

### Post by VMC on 2009-12-22
Yea go for it. Here's what I would do. as a test, if all hell breaks loose.

Clone your LTS, then do the LTS to LTS upgrade. After the smoke clears. See if you in fact upgraded or if you can even boot. If not you can clone back to where to started. No harm, no foul.

---

### Post by ronacc on 2009-12-22
you can only upgrade in a normal manner to a released version which lucid ( 10.04) won't be for a little over 4 months . you can use the method described above ( change your source.list to lucid) but I would advise against it . You have stuck with an LTS for a reason and while lucid will be LTS when released it is currently in a very early development stage and breakage is guaranteed . If you decide to go ahead anyway follow VMC's advice and have a backup , 2 backups would be even better .

---

### Post by ranch hand on 2009-12-22
> **ronacc said:**
> you can only upgrade in a normal manner to a released version which lucid ( 10.04) won't be for a little over 4 months . you can use the method described above ( change your source.list to lucid) but I would advise against it . You have stuck with an LTS for a reason and while lucid will be LTS when released it is currently in a very early development stage and breakage is guaranteed . If you decide to go ahead anyway follow VMC's advice and have a backup , 2 backups would be even better .
Yep, good advice.

Like I say, I will try it one of these days.  I have room on my drives to install a new install with NO data on it at all unless I put it there for test purposes.

There is no way that my Hardy is going to be abused that way after all this time.

---

### Post by 23meg on 2009-12-22
LTS to LTS upgrades *are supported*, as they have been before, but not really testable at this point. I'll post a call for testing when they are.

---

### Post by snowpine on 2009-12-22
Thanks for the replies everyone. This is not my main "box", in fact it is a fresh Hardy install on a virtual machine I created specifically for testing this upgrade. I (wrongly) assumed that because 10.04 alpha has been released that we could upgrade to it and start testing.

And I still do not understand why do-release-upgrade went directly from 8.04->9.10 when every post I've ever read on the topic (including several I wrote myself) says that's impossible unless you upgrade sequentially 8.04-8.10-9.04-9.10. I hope Canonical fixes this ASAP because I see it generating a lot of confusion. :)

---

### Post by 23meg on 2009-12-22
> **snowpine said:**
> 
And I still do not understand why do-release-upgrade went directly from 8.04->9.10 when every post I've ever read on the topic (including several I wrote myself) says that's impossible unless you upgrade sequentially 8.04-8.10-9.04-9.10. I hope Canonical fixes this ASAP because I see it generating a lot of confusion. :)

Because you've modified your Hardy sources.list to point to Karmic repositories. I don't know why you did that, but it's an unsupported upgrade path. There's not much that can be done to "fix" this situation, as do-release-upgrade is behaving as told.

By the way: if you're using an Ubuntu derivative, rather than Ubuntu itself, it's a good idea to look for support in the derivative's own support channels.

---

### Post by snowpine on 2009-12-22
> **23meg said:**
> Because you've modified your Hardy sources.list to point to Karmic repositories. I don't know why you did that, but it's an unsupported upgrade path. There's not much that can be done to "fix" this situation, as do-release-upgrade is behaving as told.

By the way: if you're using an Ubuntu derivative, rather than Ubuntu itself, it's a good idea to look for support in the derivative's own support channels.

I did not edit sources.list in any way. do-release-upgrade -d *told* me it was upgrading to lucid (it started downloading files with names like lucid.tar.bz) but to my surprise I ended up with Karmic instead. I hate Karmic and was hoping to skip it altogether, that's why I was surprised and disappointed... my computer lied to me. Try it yourself if you don't believe me... :)

---

### Post by 23meg on 2009-12-22
> **snowpine said:**
> I did not edit sources.list in any way. do-release-upgrade -d *told* me it was upgrading to lucid (it started downloading files with names like lucid.tar.bz) but to my surprise I ended up with Karmic instead. I hate Karmic and was hoping to skip it altogether, that's why I was surprised and disappointed... my computer lied to me. Try it yourself if you don't believe me... :)

That's probably a bug with cleaning up the sources.list during the release upgrade. Note it down to be filed once we're testing Hardy to Lucid upgrades, if it persists.

---

### Post by snowpine on 2009-12-22
> **23meg said:**
> That's probably a bug with cleaning up the sources.list during the release upgrade. Note it down to be filed once we're testing Hardy to Lucid upgrades, if it persists.

Cool, thanks. I am marking this thread solved with the understanding that LTS to LTS upgrade is not yet supported.

According to the sticky (which I should have read before posting!) upgrade testing will begin in February.

---

### Post by slakkie on 2009-12-22
> **23meg said:**
> LTS to LTS upgrades *are supported*, as they have been before, but not really testable at this point. I'll post a call for testing when they are.

That would be nice. I want to see how the upgrade will perform on my server.

---

### Post by ranch hand on 2009-12-22
It would also be nice to know when the ISO testing for Hardy's 8.04.4 is due.

---

### Post by slakkie on 2009-12-22
I think you can run -proposed repo's to see what is coming.

---

### Post by ranch hand on 2009-12-22
> **slakkie said:**
> I think you can run -proposed repo's to see what is coming.
Say what?  How do you do this?

---

### Post by slakkie on 2009-12-22
> **ranch hand said:**
> Say what?  How do you do this?

```

# Uncomment deb-src if you really need them

## Keepers
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

# Optional, but recommended
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

# Optional, remove if you don't like them
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

# Medibuntu repositories, check http://www.medibuntu.org/ for more details
deb http://packages.medibuntu.org/ hardy free non-free

```

Like that :)

---

### Post by ranch hand on 2009-12-22
OH, I guess I never looked at that closely.  I can't get to my Hardy right  now, it is on a turned off HDD, I remember seeing that entry.  I do not know if I uncommented it or not.

I did check in the Jaunty sources.list.  It is not there.  I wonder if that is a LTS thing.

Hardy was my first exposure to Linux and Ubuntu.  I just cleaned up my sources list because I really had it screwed up.

I think that tomorrow I am going to install Hardy on my test platform and get it updated (I think I have 8.04.1 but it may not be that new).  I really want to watch this happen.  One awfully big jump.

This will not, however, let me know when the testing period for the ISO for 8.04.4 is going to be.  That is what I really want to know.  I should find the link to the mailing list.

---

### Post by slakkie on 2009-12-22
> **ranch hand said:**
> OH, I guess I never looked at that closely.  I can't get to my Hardy right  now, it is on a turned off HDD, I remember seeing that entry.  I do not know if I uncommented it or not.

I did check in the Jaunty sources.list.  It is not there.  I wonder if that is a LTS thing.

Hardy was my first exposure to Linux and Ubuntu.  I just cleaned up my sources list because I really had it screwed up.

I think that tomorrow I am going to install Hardy on my test platform and get it updated (I think I have 8.04.1 but it may not be that new).  I really want to watch this happen.  One awfully big jump.

This will not, however, let me know when the testing period for the ISO for 8.04.4 is going to be.  That is what I really want to know.  I should find the link to the mailing list.

-proposed and -backports are not limited to LTS versions. All versions have them. -proposed has been used by the KDE devs for the changes in update-manager(-core?) and adept-manager in Hardy (to allow 8.04 to 9.10 upgrades). They pushed the packages first into -proposed and from there it went to -updates.

I've never seen a testing image of LTS point releases (having run dapper and hardy).

---

### Post by 23meg on 2009-12-22
[QUOTE=slakkie]-proposed and -backports are not limited to LTS versions. All versions have them. -proposed has been used by the KDE devs for the changes in update-manager(-core?) and adept-manager in Hardy (to allow 8.04 to 9.10 upgrades). They pushed the packages first into -proposed and from there it went to -updates.[/QUOTE]

-proposed is used for all [stable release updates]("https://wiki.ubuntu.com/StableReleaseUpdates"). They go into -proposed first, and are subject to preliminary testing among people who have enabled -proposed, and are copied to -updates once the fix is verified.

[QUOTE=slakkie]I've never seen a testing image of LTS point releases (having run dapper and hardy).[/QUOTE]

Perhaps you didn't look at [http://iso.qa.ubuntu.com](http://iso.qa.ubuntu.com), then.

There will most likely be a [testing day]("https://wiki.ubuntu.com/Testing/UbuntuTestingDay") dedicated to 8.04.4. I'll post an announcement here in due time.

---

### Post by Trapper on 2009-12-22
Well, just for my own curiosity, I did an upgrade to lucid from an 8.04.3 install that was an okay sacrifice and was going to go anyhow. It failed miserably.:)

---

### Post by ranch hand on 2009-12-23
Oh great, saved by 23meg again, thanks a lot.  It is one I do not want to miss.

-proposed must not be a default entry in the sources.list.  I am on 9.04 right now and do not have it and it is not in my other 9.04 either (This is my main drive and I have 2 of them so I can try dicey stuff on the "other" one so I don't screw this one).

I will have to add that to something and see what it does.  Sounds neat.

---

