---
title: "New server installation won't boot"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by tdixon on 2007-04-01
I've been running Debian flawlessly on my old P1 166 MHz PC for the last year or two. I installed Ubuntu Server 6.10 and the install went perfectly. When I rebooted, it went into GRUB then started to load Ubuntu then my screen shut off and the computer restarted. It reboots every time as soon as it gets to "Starting up..." Does anybody have any ideas for me?

Thanks,
Trevor

---

### Post by peregrine on 2007-04-01
Format and start over....thats probably the easiest way. but..

Did you try booting into the 'safe' mode on the GRUB? and figuring out what the logs say?

Otherwise you could maybe try booting a live cd, Damn Small probably, and seeing if you can't edit the files manually and reading the logs that way?

Goodluck

---

### Post by wpshooter on 2007-04-01
Your computer probably does not have enough memory/ram to run regular Ubuntu.

Perhaps you might try Xubuntu.  But if it's a P1, I am not sure that even that is going to install.

Good luck.

---

### Post by tdixon on 2007-04-01
I've tried it in safe mode and it did the same thing. I also tried it with 6.06 and it does the same thing, though it has slightly different verbose. It says something about initr.d and then says the word "boot" then restarts. I guess I have some weird hardware incompatibility. I do only have 64mb of RAM. It's very little, but I would think that wouldn't prevent it from getting five seconds into booting. It's not trying to boot into a GUI is it? I just want a bash shell.

Trevor

---

