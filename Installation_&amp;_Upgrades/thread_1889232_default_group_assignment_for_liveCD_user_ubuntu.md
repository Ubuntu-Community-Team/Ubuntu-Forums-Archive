---
title: "default group assignment for liveCD user ubuntu"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by mbradlcu on 2011-12-01
Hi Folks,
I've created a live iso using this url:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")

The image includes ubuntustudio-audio packages. The problem is that the default ubuntu user (guessing this has something to do with casper) isn't included in the audio group, so using jack real time isn't available even as the image uses the rt kernel. (it's available after re-logging in with my wonky init script, but that won't do for the folks I'd like to share this with)

I've been able to add a (wonky) init.d usermod script that restarts gdm but I'd like to know if anyone knows a proper fix that would assign user ubuntu to group audio.

I tried adding usermod to rc.local but apparently the gui session is started before rc.local, and anything in rc2

thanks in advance for any insight into this challenge!

---

