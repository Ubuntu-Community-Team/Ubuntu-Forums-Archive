---
title: "Trouble installing Linux Mint 17.3 and 17.2 on ASUS machine"
date: 2016-04-01
forum: MINT
---

### Post by newmintuser2 on 2016-04-01
Hello I'm having troubles installing Linux Mint from a bootable USB drive. It usually just hangs on the logo screen until I hit an F key and then a black screen with text pops up. Here are some pictures (please forgive my filthy screen):

[http://i.imgur.com/KCIzSz1.jpg](http://i.imgur.com/KCIzSz1.jpg)

Let's say I click the first option, then that's when the logo pops up. After hitting any F key, this pops up:

[http://i.imgur.com/YD8CAyo.jpg](http://i.imgur.com/YD8CAyo.jpg)

Here's more of what it says: [http://i.imgur.com/bMiyfVy.jpg](http://i.imgur.com/bMiyfVy.jpg)

And then after that it will just hang there. I also see something that pops up that says "Error" after a string of text, but it goes by too quick for me to take a picture of it.

Also, for good measure, I'm going to throw in a picture of the advanced settings on my BIOS (since someone suggested this might be the problem):

[http://i.imgur.com/lWZ9jdm.jpg](http://i.imgur.com/lWZ9jdm.jpg)

Please be aware I am a newb so explain things as simple as possible. Thanks!

---

### Post by howefield on 2016-04-01
Thread moved to the "*MINT*" forum.

---

### Post by buzzingrobot on 2016-04-01
It's not clear if you are seeing all that during an installation attempt or as the system is booting after a successful install.

I'm afraid the BIOS screen shot doesn't convey much information.  What those earlier suggestions were probably getting at was whether the system was booting in "Legacy" mode or "UEFI" mode, which should be indicated in the section of the BIOS setup that applies to booting. (BIOS setup programs differ.)

It looks like Win8 is on the machine.  If this is an install attempt, be sure the machine shuts down completely before booting into the installer. Windows "Fast Boot" is a form of hibernation and the machine does not fully shut down.  There should be an option in BIOS setup to disable it.

Some specs about the system would be useful, as well.

Also, there's Mint's own forum at linuxmint.com.

---

