---
title: "lubuntu 12.04 CD install freezes at initial loading"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by Greengoat on 2012-06-05
The standard install CD will not get past the lubuntu loading screen after I specify Install or Boot From CD. It seems that the CD drive spins up and begins to read but goes silent after a couple minutes with the little loading "dots" still. I checked the disk using the initial menu option and it says it is fine. Anyone having CD issues with this install?

Dell b130 laptop, 1GB RAM, loaded with Ubuntu 11.

---

### Post by Bucky Ball on 2012-06-05
Welcome. 

At the intro screen where you can 'Try Ubuntu', 'Install Ubuntu', etc., hit F6 and choose the 'nomodset' option. Proceed and post back. ;)

Strongly advise to 'Try Ubuntu' to see how it runs on your machine and if the nomodset option is the fix. If so, you can then proceed to install by clicking the icon on the desktop.

BTW, Ubuntu 11 what? You have 11.04 (supported until October 2012) or 11.10 (just under a year's support to go). 

LTS (long term support) releases have the longest support; 10.04 LTS has just under a year left, reliable and stable, and 12.04 LTS, which has just been released so still getting the bugs out but getting there, has just under five years support.

---

### Post by Greengoat on 2012-06-05
Thanks for the information Bucky. I know what the LTS releases mean. I just figured I would go with the most recent version of lubuntu.

My current version loaded is Ubuntu 11.10.

I have set the install options to nomodset (no splashy graphics?) and now it gets to an error related to wireless firmware, b43/ucode5.fw. Both in boot and install options.

But why does it crash over the wireless? Looking through the threads now.

---

### Post by Greengoat on 2012-06-05
Oh my god. What a freaking headache:
[http://ubuntuforums.org/showthread.php?t=1966655&highlight=b43-phy0+ERROR](http://ubuntuforums.org/showthread.php?t=1966655&highlight=b43-phy0+ERROR)

I am switching to Lubuntu because of the usability bloat that seems to be creeping into the core Ubuntu release but this isn't instilling faith. I have booted many Ubuntu releases without a hitch before.

---

### Post by Bucky Ball on 2012-06-06
Does Lubuntu have an alternate install ISO (as opposed to the desktop)? You might try that. You might also try other options from F6. I assume it runs okay when you 'Try Lubuntu', if it has that option?

If you're feeling game you could try a minimal install and add lxde as the desktop environment. This would be bloat-free except for the apps you add. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

