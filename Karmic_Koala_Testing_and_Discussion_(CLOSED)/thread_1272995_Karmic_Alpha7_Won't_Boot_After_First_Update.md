---
title: "Karmic Alpha7 Won't Boot After First Update"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mtate5000 on 2009-09-22
Hey eveybody,
I installed alpha 7 earlier today, to test it out, and after it ran through the initial system update it doesn't want to boot up. I started the update and then left the house for awhile, and when I got back to it it was at a screen asking me what to do with grub. Since I installed grub to the same partition as alpha7, I figured let it upgrade it to "maintainers version" which was the first option. It did whatever it did and I rebooted. Now I go through my first grub to get to the new grub (I assume grub2), and choose the latest kernel and it acts as though it wants to boot in verbose, but the first line says something about "no parent file found" or something like that.
It only lasts for a moment, so I couldn't read the whole line, then my display shuts off and nothing. It doesn't do anything. I waited it out for a minute or two but that was it. I had to hit the main power button to shut it off. I also tried booting in recovery, and got the same result. I thought that there might have been a problem with grub, but everything else boots except alpha 7. Another tid-bit of info, before I updated I installed gnome shell (gnome 3? I thought), but thats all I did. That may or may not have something to do with it. Any ideas? I can just as easily reinstall, but if there is something I did or did not do that caused this issue, I would like to know.  Thanks in advance. These forums are awesome. You guys have saved my hide many times, keep up the good work!

Sorry!!! It's alpha 6. Got confused.

---

### Post by mtate5000 on 2009-09-23
Okay here's what I've found:
Karmic will not load with external usb plugged in. I had my flash drive plugged in that I used to install alpha 6. I booted into jaunty to write this post and unplugged my flash w/out thinking about it. I fooled around w/grub trying to boot directly using the uuid, which I did successfully, the tried booting back in with grub 2 and it booted. That left me scratching my head until I realized the flash wasn't plugged in. So I plugged it back in and rebooted. Low and behold, it wouldn't boot. I'll file a bug report later. If anybody else has this issue let me know, may be my machine but I doubt it. Had the same problem with iAtkos OSx86 10.5.7, but then again what problems didn't I have!?!

---

### Post by oboedad55 on 2009-09-23
> **mtate5000 said:**
> Okay here's what I've found:
Karmic will not load with external usb plugged in. I had my flash drive plugged in that I used to install alpha 6. I booted into jaunty to write this post and unplugged my flash w/out thinking about it. I fooled around w/grub trying to boot directly using the uuid, which I did successfully, the tried booting back in with grub 2 and it booted. That left me scratching my head until I realized the flash wasn't plugged in. So I plugged it back in and rebooted. Low and behold, it wouldn't boot. I'll file a bug report later. If anybody else has this issue let me know, may be my machine but I doubt it. Had the same problem with iAtkos OSx86 10.5.7, but then again what problems didn't I have!?!

Alpha 7? I think it's still on 6, no? I have a laptop that won't boot with a USB printer hooked to it, it hangs on the bios. Go figure.

---

### Post by talkingwires on 2009-09-23
Alpha 7? Are you from a future, alternative universe where the developers have added another alpha to the release cycle?

---

### Post by oboedad55 on 2009-09-23
> **talkingwires said:**
> Alpha 7? Are you from a future, alternative universe where the developers have added another alpha to the release cycle?

Man, I thought I was losing it. I spent all this time futzing with alpha 6 and I thought it was already time to start all over again. LOL!

---

### Post by ljrmorgan on 2009-09-23
> **mtate5000 said:**
> Okay here's what I've found:
Karmic will not load with external usb plugged in. I had my flash drive plugged in that I used to install alpha 6. I booted into jaunty to write this post and unplugged my flash w/out thinking about it. I fooled around w/grub trying to boot directly using the uuid, which I did successfully, the tried booting back in with grub 2 and it booted. That left me scratching my head until I realized the flash wasn't plugged in. So I plugged it back in and rebooted. Low and behold, it wouldn't boot. I'll file a bug report later. If anybody else has this issue let me know, may be my machine but I doubt it. Had the same problem with iAtkos OSx86 10.5.7, but then again what problems didn't I have!?!

I had this problem for a long time with my USB hard drive, it'd go through grub ok and start loading karmic, then it'd freeze with a flashing cursor in the top right.

It hasn't been a problem for me for a while though, a good few weeks at least.

---

