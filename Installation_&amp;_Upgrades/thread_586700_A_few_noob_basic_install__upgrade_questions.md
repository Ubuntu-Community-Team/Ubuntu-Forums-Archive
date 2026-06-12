---
title: "A few noob basic install / upgrade questions"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by bhold on 2007-10-22
I'm new to Linux desktop - bought a Dell earlier this summer pre-loaded with Feisty. Since then I have re-partitioned, and re-installed a dual boot environment with Feisty and Suse 10.2. I've read through the forums and community docs and have some basic questions about the Ubuntu new release process.

1. I downloaded the 7.10 i386 desktop iso a few days ago. Got a good md5sum check so burned an install disk but have not yet installed. I looked at the contents of several mirrors before doing so. Options available to me were ii386 or amd64 / desktop or server / alternate cd.

- What exactly is the difference between the alternate cd and the "normal" cd? They are approximately the same size but I never found anything that describes the difference. I chose the normal (not alternate) iso, hope this was correct. Why would someone select alternate and what would be different?

- Where is the live cd I hear so much about? I did not see a download option for this at any of the mirrors I looked at? Did I miss something?

- In one thread I also read about a dvd-sized download that would pack in a lot of repository contents so as to minimize network activity during the actual install or upgrade. Sounds like a good idea to do this then let the install / upgrade process run with minimal chance of disruption due to network issues. But I did not see any option for this type of download. Is there a certain mirror I need to go to for this?

2. I have been following the thread regarding tips for installing or upgrading to 7.10. One comment I see often is to wait a month, the developers will fix bugs. What will be the logistics of this if true? Will there be new iso files available for download at some point? New workarounds and updated release notes? New post-install patches? All of the above? How have new release bugs been handled in the past?

OK, thanks a lot for any enlightenment I can get on the above, it will really help me get a handle on how I plan to move forward to 7.10 and future releases. Maybe others will find this useful also. These forums have been a GREAT source of info so far.       -- Bob

---

### Post by mivo on 2007-10-22
The Live CD is the "desktop" CD. Unlike the alternate CD, it has a graphical installer and you can try out Ubuntu before you install it (it runs slower since it loads everything from the CD). There are sometimes issues with installing it from within the live environment (rarely), in which case the alternate CD is the better choice (there is no live environment, just a text-based installer).

---

### Post by EagleRock on 2007-10-22
> **bhold said:**
> 
- What exactly is the difference between the alternate cd and the "normal" cd? They are approximately the same size but I never found anything that describes the difference. I chose the normal (not alternate) iso, hope this was correct. Why would someone select alternate and what would be different?

As mivo said already, the live cd is the "normal" cd that boots into Ubuntu before you install.  Alternate is for special cases where you have trouble with the live cd.

> **bhold said:**
> 
- In one thread I also read about a dvd-sized download that would pack in a lot of repository contents so as to minimize network activity during the actual install or upgrade. Sounds like a good idea to do this then let the install / upgrade process run with minimal chance of disruption due to network issues. But I did not see any option for this type of download. Is there a certain mirror I need to go to for this?

If I'm not mistaken, the alternate CD packs more repos onto it since it doesn't have the liveCD on it.  If you're very worried about network traffic, the alternate might work.  Though, honestly, you can install Ubuntu fine and simply update after the install.  Synaptic is a blissfully easy front-end to apt-get, after all.

> **bhold said:**
> 
2. I have been following the thread regarding tips for installing or upgrading to 7.10. One comment I see often is to wait a month, the developers will fix bugs. What will be the logistics of this if true? Will there be new iso files available for download at some point? New workarounds and updated release notes? New post-install patches? All of the above? How have new release bugs been handled in the past?

The updates are done through post-install patches.  I don't think they do revisions on the CDs themselves at all.  You should be fine using the burned CD you have right now.

> **bhold said:**
> 
OK, thanks a lot for any enlightenment I can get on the above, it will really help me get a handle on how I plan to move forward to 7.10 and future releases. Maybe others will find this useful also. These forums have been a GREAT source of info so far.       -- Bob

Glad to hear you're liking Ubuntu, and best of luck to you!

---

