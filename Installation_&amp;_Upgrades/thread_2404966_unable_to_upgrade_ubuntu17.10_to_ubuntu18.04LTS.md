---
title: "unable to upgrade ubuntu17.10 to ubuntu18.04LTS"
date: 2018-10-30
forum: Installation &amp; Upgrades
---

### Post by kwalters on 2018-10-30
My prime PC is 64 bit AMD dual core running Ubuntu 17.10.  I tried to download the 18.04  ,iso file then use that to make a bootable USB stick to install it.  When it failed to work several times (would not get as far as the live screen where you choose Try or Install), I decided I must have downloaded a faulty .ISO file.  I downloaded a fresh one and found the same problem again.  

Since then I have tried every alternative I could think of (burn bootable DVD and use that;  burn it at slow speed; try dd instead of .iso: try the Windows image burner; none of these worked

Eventually, when I had been stuck in 17.10 for long enough, it announced that 17.10 was not supported any more, and would I like to upgrade to 18.04LTS.  I accepted this, and the process started, then stopped and announced that the upgrade tool could not be used to upgrade Zesty to Bionic.

In sum then, I cannot do a fresh install and cannot upgrade.  Am I stuck with 17.10 for life?  I should be grateful for any suggestions.

kwalters

---

### Post by Bashing-om on 2018-10-30
kwalters; Hello -

What do you want to do for the upgrade ? A fresh clean install of 18.04 certainly has its advantages. BUT, the EOL 17.10 repo remains to this time on line and has not been moved:
 [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

You decide where we place our efforts to assist, as either way "should" work.


[INDENT][INDENT]and away we will go
[/INDENT][/INDENT]

---

### Post by again? on 2018-10-30
You will need to change your repositories to the old-releases archive before attempting an update.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

