---
title: "updating to intrepid"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by VideoAddicted on 2010-01-24
I would like to upgrade my ubuntu from Hardy to Intrepid. All the posts I've looked at say that you can do it through the update manager, but I can't seem to find the way to do that, does anyone have any more detailed instructions on how I should go about upgrading?

---

### Post by chewearn on 2010-01-24
Go to:
System > Administration > Software Sources > "Updates" tab

Find the last item in the dialogbox: "Release Upgrade".  Make sure it's set to "Normal releases".

Then, try Update Manager again.  The Upgrade button should appear in the top.

Make sure you have backed up your entire install before proceed; because once you upgraded, there is no easy downgrade.

---

### Post by VideoAddicted on 2010-01-24
I followed those instructions and no update button appeared in Update Manager.  Anything I may have missed?

---

### Post by qjb on 2010-01-24
The changelogs.ubuntu.com server was down I think. It seems to be working again.

---

### Post by kansasnoob on 2010-01-24
> **VideoAddicted said:**
> I would like to upgrade my ubuntu from Hardy to Intrepid. All the posts I've looked at say that you can do it through the update manager, but I can't seem to find the way to do that, does anyone have any more detailed instructions on how I should go about upgrading?

Please, if it's not too late, wait for Lucid!

You'll be much happier :)

---

### Post by texaswriter on 2010-01-24
Kansasnoob> Is Lucid gonna be an LTS?

---

### Post by Deuce1912 on 2010-01-24
@ VideoAddicted: if you still want to upgrade, but don't want to wait for Lucid, then you should type this into terminal:

```
sudo update-manager -d
```

@ texaswriter: Yes Lucid is going to be a LTS.

---

### Post by texaswriter on 2010-01-25
Sweet, 3 months to wait... being a newer user to Linux [<year], I've yet to see a new LTS, so definitely excited.

---

### Post by chewearn on 2010-01-25
> **texaswriter said:**
> Sweet, 3 months to wait... being a newer user to Linux [<year], I've yet to see a new LTS, so definitely excited.

Well, technically 3 months; but practically it will probably be more like 6 months.  Because it's quite likely Lucid would not be immediately stable on release.

Before I got flamed, I will like to remind that Hardy suffered for a couple of months after release as well.  I distinctively remembered the long threads complaining about mis-configured pulse audio, beta firefox, etc.

---

### Post by texaswriter on 2010-01-25
> **chewearn said:**
> Well, technically 3 months; but practically it will probably be more like 6 months.  Because it's quite likely Lucid would not be immediately stable on release.

Before I got flamed, I will like to remind that Hardy suffered for a couple of months after release as well.  I distinctively remembered the long threads complaining about mis-configured pulse audio, beta firefox, etc.

13 hours later and no flames... I think you are in the clear :D :popcorn::KS 

**BTW, **isn't there a way to update what repositories to pull from, say, if you have Debian Lenny and want to "upgrade" to Sid, add sid repositories, update, and than a command, hrrm dist-upgrade or something like that... I did it once, but than reinstalled with Sidux LiveCD.  Maybe that jogs somebody's memory...

---

### Post by chewearn on 2010-01-25
> **texaswriter said:**
> 13 hours later and no flames... I think you are in the clear :D :popcorn::KS 

**BTW, **isn't there a way to update what repositories to pull from, say, if you have Debian Lenny and want to "upgrade" to Sid, add sid repositories, update, and than a command, hrrm dist-upgrade or something like that... I did it once, but than reinstalled with Sidux LiveCD.  Maybe that jogs somebody's memory...

Yes, I did this once in Debian.  Change the repositories; then run "aptitude update"; then upgrade apt itself: "aptitude install apt dpkg aptitude"; then finally "aptitude dist-upgrade".

But I'm not sure if you could do the same in Ubuntu.  There might be special conditions or operations done by the Update Manager during upgrade.  The supported method of upgrading is by Update Manager.

After all, if you are able to upgrade manually with another method, you should be able to (and expected) fix any breakage yourselves.

And this the post which have "upgrade" word mentioned seven times. :mrgreen:

---

### Post by texaswriter on 2010-01-25
Oh, you are gonna get flamed for sure now, setting all these world records... 

Well, lol, if I wasn't in a semester at school already, I'd test that on my laptop, but, as such, I don't have time to reinstall ubuntu jaunty + karmic + get my wacom and wireless drivers working again. 

Given your statement about Lucid, I'll probably wait until after summer semester too to upgrade, I think I'll get like a few days in between summer and fall [if that hehe] and the interim between spring and summer will probably be too soon...

---

### Post by VideoAddicted on 2010-01-26
Lucid won't be a repeat of the disaster with karmic will it?  I heard it was a disaster when that first came out.

---

### Post by chewearn on 2010-01-27
> **VideoAddicted said:**
> Lucid won't be a repeat of the disaster with karmic will it?  I heard it was a disaster when that first came out.

First, I would have to disagree that Karmic was a disaster.  I think it worked for a lot of people, and it failed for a few.  Unfortunately, we hear more about the few than the many.

But, that's what happened with every release since I first joined ubuntuforums (maybe even before but I wouldn't know).

Back when Hardy was first released, the forums kept getting longer and longer threads about [COLOR=Red]"Hardy Failed!"  "The sky is falling!" "What are we doing?  Ubuntu is dead!!!"  "Dead and buried, I said!!!"[/COLOR]

A few months later, the complaints died down, and nowadays we hear only praises about how Hardy is the "BEST Ubuntu EVAR!!!".

I'm sure, comes April, the cycle will repeat.

---

### Post by VideoAddicted on 2010-02-02
earlier it was suggested that I back up my computer before I upgrade.  Can anyone provide more detail therein?  I'm afraid that I'm still quite new to ubuntu and don't understand how exactly I would go about something like this.

---

### Post by chewearn on 2010-02-03
> **VideoAddicted said:**
> earlier it was suggested that I back up my computer before I upgrade.  Can anyone provide more detail therein?  I'm afraid that I'm still quite new to ubuntu and don't understand how exactly I would go about something like this.

Here is the method I used.  It might not be what everyone else use, but it works for me.

1. If it's a desktop PC
I clone the harddisk containing current Ubuntu to another harddisk, using tools such as [Clonezilla]("http://clonezilla.org/") or [GParted Live]("http://gparted.sourceforge.net/livecd.php").  After cloning, I boot up to clone disk, and run upgrade.

If the upgrade failed, I swap back the old harddisk, and am back in business within minutes.

2. If it's a laptop, or if I don't have a spare harddisk
I shrink the current Ubuntu partition by half, using [GParted Live]("http://gparted.sourceforge.net/livecd.php") or Ubuntu LiveCD.  Then, I cloned the partition to the freed space.  Now, I have two identical Ubuntu partitions.  Next, I change the UUID of the cloned partition, fix various bits to boot with the new UUID, then run the upgrade.

If upgrade failed, restore Grub to boot into the old partition, and back in business with minutes.

---

### Post by VideoAddicted on 2010-02-07
thanx everybody.

---

