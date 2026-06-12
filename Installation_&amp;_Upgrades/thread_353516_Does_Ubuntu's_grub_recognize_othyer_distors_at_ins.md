---
title: "Does Ubuntu's grub recognize othyer distors at install time?"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by rswitzer on 2007-02-04
I run several linux distros + windows on 1 hard drive, I usually install XANTROS last, because
its grub automaticly recognizes and installs other distros it finds on its grub, so you can easily have your choice of distros. Many distors dont do this, in fact are very unfriendly to other linux it finds.( manually configuring grub with several distros is not easy or fun, but if you really like a challenge, try it!)

my questio9n is, how does ubuntu behave when installed in a unused space on a HD, but windows and other linux distros are also on the HD?

Thanks in advance for any answers

Bob in Houston

---

### Post by dcstar on 2007-02-04
> **rswitzer said:**
> I run several linux distros + windows on 1 hard drive, I usually install XANTROS last, because
its grub automaticly recognizes and installs other distros it finds on its grub, so you can easily have your choice of distros. Many distors dont do this, in fact are very unfriendly to other linux it finds.( manually configuring grub with several distros is not easy or fun, but if you really like a challenge, try it!)

my questio9n is, how does ubuntu behave when installed in a unused space on a HD, but windows and other linux distros are also on the HD?

Thanks in advance for any answers

Bob in Houston

I haven't had any problems with Ubuntu detecting Windows installations, but I can't say if it picks up other Linux installations ok.

---

### Post by cidhus on 2007-02-05
Installed Edgy 6.10 last night. I have two Windows (one on hda and another on hdb), SuSE 10.0, Slackware 9.1 and 10.0, and Crux 2.2. Edgy picked up both Windows but nothing for the other Linux distros. Only a line in grub "Other OS", which fails when I select it on boot without any option to select a specific Other OS. Guess I get to bone up on info grub. LILO was so much simpler.

---

### Post by louieb on 2007-02-05
Its hit and miss, and when its a hit you wind up editing menu.lst anyway. The entry for other linux distro is :
Unknown Linux on hd# or something like that.

---

