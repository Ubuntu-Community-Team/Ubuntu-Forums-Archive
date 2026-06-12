---
title: "Can't use RAID1 to install Ubuntu Desktop 11.10"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by misterbk on 2012-03-04
I suppose you could call this a feature request, and I suppose you could say I have a "special use" scenario, but isn't that what Linux is all about?

Here's my story.  Attempting to use "hardware" RAID volumes with my new motherboard isn't working, and very likely is not going to.  (I have given up on this, and this is not the point of my post, this is here to keep people from saying 'Use your mobo RAID' as a solution.)

I've had this problem with Linux installs before.  For some reason, even though the motherboard should only be exposing a RAID1 volume that was created using its setup utility, and even though the Ubuntu installer sees that (down to the volume name I gave it), the actual install only goes to one disk.  (How I have no f-ing idea... I think I should blame the motherboard? Or Linux? This one is beyond me.)  I have verified this by virtue of the fact that after unsuccessfully installing several times, the second disk did not have anything on it.

Anyway, so long story short, the motherboard "hardware" RAID doesn't work.  **Obvious solution: Software Raid**, which Linux is supposedly very good at.

***But Ubuntu has chosen to remove the RAID options (mdadm etc.) when installing Desktop edition.***

Now, I know for a fact I am NOT the only user who uses RAID on their desktop, and I know that Ubuntu Server is not the correct choice for my use.

So, at some point in the future, can we maybe have that in Desktop, like it is in Server?

Reference link:
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html]("https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html")
    ^---- This works only in Server, but really ought to be in Desktop as well.

Specifically, in Step 5, there is no option for "physical volume for RAID" and we cannot later "Configure Software RAID" and "Create MD device".

To avoid confusing people with too many options, it seems natural you could have the "Configure Software RAID" option only show if more than one volume has been set with "physical volume for RAID", and an error message prevent continuing the install if only one volume has been set with "physical volume for RAID" or if sizes don't match.

I don't want to install Ubuntu Server because this is a home entertainment box, set up to start playing MP3s and/or launch Pandora at a certain time of morning, play Hulu on the TV, and run emulator games.

Note: I am not including my hardware details, because I don't want support with my motherboard raid in this thread.  (I gave up on it.)  What I want is to be able to configure software RAID during Ubuntu Desktop install.

---

### Post by darkod on 2012-03-04
For RAID and/or LVM installs you need to use the Alternate Install CD, not the standard live cd. It installs the same desktop system but the installer is text based (Not GUI) and it has better support for raid.
In fact, even though dmraid is included in the live cd, you should still use the alternate for installing on fakeraid too.
For software raid with mdadm, go with alternate cd.

---

### Post by misterbk on 2012-03-04
> **darkod said:**
> For RAID and/or LVM installs you need to use the Alternate Install CD, not the standard live cd. It installs the same desktop system but the installer is text based (Not GUI) and it has better support for raid.
In fact, even though dmraid is included in the live cd, you should still use the alternate for installing on fakeraid too.
For software raid with mdadm, go with alternate cd.

Isn't this a useful-enough and common-enough feature that we should be able to do this without needing a completely different install disk?

---

### Post by darkod on 2012-03-04
Fakeraid seems a lot more common than software raid.
But anyway, I can't answer this, I am not involved in the development of ubuntu. It might look "easy" to us, but I have no idea how easy or difficult is to include these options in the live cd image. Note that the image is big enough right now (barely fits a CD) without these extra packages.

With the cost of CDs these days I wouldn't say it's an issue to have another one in your collection.

Also, if I am not mistaken there is the DVD edition but I'm not sure if mdadm and lvm are included, never really looked into it. The DVD edition is much bigger and might be the "all in one" disc.

---

### Post by twh7458 on 2012-03-04
Hello,

I'm new to this forum.  Can you please tell me how I start a new thread?  I have a major problem that someone I'm sure has an easy answer to.

Thanks a bunch!

Todd

---

### Post by misterbk on 2012-03-04
> **twh7458 said:**
> Hello,

I'm new to this forum.  Can you please tell me how I start a new thread?  I have a major problem that someone I'm sure has an easy answer to.

Thanks a bunch!

Todd

There's a "New Thread" button at the top and at the bottom of the list of forum posts.  It's generally bad karma to post an unrelated question in someone else's thread though, so try to avoid that.

> 
Also, if I am not mistaken there is the DVD edition but I'm not sure if mdadm and lvm are included, never really looked into it. The DVD edition is much bigger and might be the "all in one" disc. 

It looks like the DVD mostly just contains language packs, BUT it seems to include the alternate install as well as the regular install, so I might have to get that and try (yet another) install on Linux...  Including the language packs only on the DVD is an interesting little thing too.  It took me 12-ish install attempts to get this system running, and each and every time it downloaded the language packs as part of the install process.  I'd say providing the CD option is causing them more bandwidth than only hosting a DVD image.  (And CDs aren't appreciably cheaper than DVDs anyway. I actually had to go hunting for CDs to burn.)

I get that you're not involved in the distro development, just hoping someone who is sees this.  Seems like:

* Priority 1 for space usage on a Linux install disk should be support for storage options.  The Kubuntu installer has a lot of stuff on it that's less important than, and larger than, mdadm.

* Having an install process that's forked into multiple different types is less easy to maintain than having one more flexible installer.  (Maybe with an 'advanced mode' or something.)

But, that's just me.

I will say one thing positive about the new install, I cheered out loud when I saw my location detected automatically and my keyboard defaults / time zone set by default.  I hated scrolling through those lists every time before. Bravo!

---

