---
title: "Ubuntu upgrade to 10.10 freezes"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by UncleLuis on 2010-12-10
Hello,
Today I decided to do the upgrade from 10.4 to 10.10.
Unfortunately the upgrade has frozen for the last few hours (after it has completed ~60% of job)...

The problem is with xorg, when I log through ssh to the computer I see the xorg process takes 30%.
Please help, I really would appreciate any help/advice concerning what I could try not to 'smash' the OS... I am not an expert.

During the upgrade I have experienced only 1 error with no space left on the device (it exceeded the estimations) but I have freed additional 2GB and it continued for some time.

Thank you.

---

### Post by sonialiggi on 2011-09-26
HI,

I have a similar problem, I'm trying to update from 9.10 to 10.4 but it froze while "Preparing to replace portmap 6.0-10ubuntu2 (using .../portmap_6.0.0-1ubuntu2.1_amd64.deb).

Any solution/suggestions?

Thanks

---

### Post by vinterkind on 2011-09-26
[LEFT]Could you explain a little bit more ?

You've started the upgrade via the update-manager and you've encountered the problem that 
it does ...

a) nothing ?
b) something, but I don't know what ?
c) something I think I can describe ..

Are there details ? Screenshots ? 
Can you change shells ? 

Architecture is amd64 i guess ?
Have you properly updated Ubuntu 9.10 via update-manager before upgrading ?


[/LEFT]

---

### Post by sonialiggi on 2011-09-26
Yes, the Architecture is amd64 and yes, I updated Ubuntu 9.10 via update-manager before upgrading.

The upgrade started properly, doing all the stages (preparing to upgrade, setting new software channels, getting new packages) without any error, but when it arrived to the step "installing the upgrades" it just froze.
I've tried to kill the process, but instead of dying it started again the process, and it stuck again on the installation while "installing new version of config file /etc/init/portmap.conf".

here is the screenshot of the distribution upgrade window

---

