---
title: "Will there be a kernel 2.6.22 for Edgy?"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by Aramis on 2007-07-10
Hi y'all,

for the past few days I have been trying to get my wireless card to work on my University Wireless Service [[thread]]("http://ubuntuforums.org/showthread.php?t=496447"). I eventually decided to post my problems directly with the developers, and now it seems that a solution is in sight: a new version of the kernel [[ link ]]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=24601").

Now because of work related reasons, I do not wish to upgrade to Gusty just now, and therefore I am wondering if the latest kernel will be available to Edgy users.

Cheers,

Ar@mi$

---

### Post by spd106 on 2007-07-11
As you will have probably realised by now there definitely will not be a 2.6.22 kernel for Ubuntu 6.10 (Edgy ), nor will there be one for Ubuntu 7.04 (Feisty). So you will have to build a kernel yourself. There are a couple of guides around this forum for doing it with the Ubuntu patches so that it will work better than the vanilla one. I recently saw one in the networking and wireless forum, though I recommend that you follow up on the serial monkey forum as they will be able to help you with card specific modifications.

If you can wait for the next Tribe release's live cd, then that might be a good test run as it looks like the serial monkey rt2x00.pci driver is included. Whether it will work or not I have no idea.

---

### Post by Gremlinzzz on 2007-07-11
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
:guitar:

---

### Post by Aramis on 2007-07-12
Hi,

**spd106**, I remembered upgrading my kernel a couple of times since I managed to install Ubuntu on my laptop, and same again for the various VMware appliances I run. Now, I am too new to Linux to know straight away that, in the case of Ubuntu, kernel versions are tied to a specific distro. Indeed, I had time since the my earlier post to search a little more, and it is clear from the packages.ubuntu.com site that each release has a kerel available.

As for the compiling of the Kernel, it is something I would rather avoid; Or at least not do it on my laptop. It is old ! Way old Oct 2002 (Samsung A10).

I also had the idea of using a liveCD that contains the already made kernel to test out the latest rt2x00 drivers... sadly I ran out of space on my CD-Rw :| However, if you say that the next version of the LiveCD might provide me with a suitable test platform, then I guess I will be patient :)

@**Gremlinzzz**, thanks for the link, I bookmarked it :)

Ar@mi$

---

### Post by spd106 on 2007-07-12
You'll have to use a 700MB CD-R to burn the desktop iso as it's too big for a 650MB CD-R. It's also a good idea top check the file size before you start the download because the pre-release cds sometimes even run over the 700MB limit.

Generally once a release hits kernel freeze, approx two weeks before the official release date, there won't be any more updates except for serious bug fixes and security updates. That means no more new features.

When you have seen a sub-version bump there will have been no new features added it's usually a signal that the ABI has changed and that kernel modules must be rebuilt. Those who use build ndiswrapper from source will be able to tell you all about that:(

You might want to track the kernel changelog on Launchpad during Gutsy's development, that way you can see when new features are added or when important changes are made.
[https://launchpad.net/ubuntu/gutsy/+source/linux-source-2.6.22/+changelog](https://launchpad.net/ubuntu/gutsy/+source/linux-source-2.6.22/+changelog)

---

### Post by Aramis on 2007-07-12
Re,
> **spd106 said:**
> You'll have to use a 700MB CD-R to burn the desktop iso as it's too big for a 650MB CD-R.


well of course I know that :rolleyes:... at the time I was not careful that is all. I was writing my PhD thesis at the same time, all that download/burn stuff happen behind the scene.
> **spd106 said:**
> 
 It's also a good idea top check the file size before you start the download because the pre-release cds sometimes even run over the 700MB limit.


as above, however it is interesting to know that dev versions are larger.

> **spd106 said:**
> 
Generally once a release hits kernel freeze, approx two weeks before the official release date, there won't be any more updates except for serious bug fixes and security updates. That means no more new features.

noted. It will be a very good day, the day some wireless card support LEAP/PEAP out of the box - or almost - in Ubuntu.
> **spd106 said:**
> 
When you have seen a sub-version bump there will have been no new features added it's usually a signal that the ABI has changed and that kernel modules must be rebuilt.

Oops you are talking mandarin to me there, man. A bump like from 2.4.xxx to 2.6.xxx ? I don't know what ABI means :|

> **spd106 said:**
> 
 Those who use build ndiswrapper from source will be able to tell you all about that:(

I never hab much luck with this application myself.

> **spd106 said:**
> 
You might want to track the kernel changelog on Launchpad during Gutsy's development, that way you can see when new features are added or when important changes are made.
[https://launchpad.net/ubuntu/gutsy/+source/linux-source-2.6.22/+changelog](https://launchpad.net/ubuntu/gutsy/+source/linux-source-2.6.22/+changelog)
noted. Thanks.

On a side note, I see that gusty is up for final release in October... maybe I will be finished writing up my doctorat by then <sights>

Thanks again for the info,

Ar@mi$

---

