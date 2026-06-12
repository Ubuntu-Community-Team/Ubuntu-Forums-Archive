---
title: "Upgrade Today Made My Wubi Go Back to Being UnBootable..."
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by marley07 on 2010-06-07
Alright. Quite Frankly, I'm Pissed. I reinstalled my wubi and upgraded it to 10.04 because of previous problems (See Link: [http://ubuntuforums.org/showthread.php?t=1494217]("http://ubuntuforums.org/showthread.php?t=1494217")). 

**Link's Short Background: ** It was originally not booting wubi and would almost instantly restart and revert back to the dual boot selection menu.

**SO,** I reinstalled Wubi and upgraded to the most recent version. This was great and all was well with the world until I installed the updates that came in today or last night. NOW IT'S DOING THE SAME THING AGAIN! Except now it shows an error message (normal...I was getting a few of them saying it couldn't find things...More detail is in the link above) but the error message blips so fast it's unreadable before the automatically forced restart.

Please Help...This is ridiculous.

---

### Post by bcbc on 2010-06-07
You installed again with 9.10. Did you replace the buggy wubildr as per [this link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")?

If this doesn't solve your problem I'll give you instructions for chroot'ing into your wubi and running updates, update-grub etc. I don't know if this will solve your problem, but I found the same thing happened to me in a test install of wubi and somehow got it working again.

Finally, it seems to me that wubi is not very reliable with 10.04 (or to be more precise, 10.04 seems to not be very reliable on some systems/configurations). It may be better to go with a traditional dual boot if you are planning to go longterm with ubuntu. Or just stick with 9.10 for a while.

---

