---
title: "Unable to boot Ubuntu"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by eXtink on 2010-08-25
I just installed Ubuntu 10.04 on my pc using Wubi (also tried the normal way, but not today :D) and i cant bootup Ubuntu. The bootup freezes when the 5 dots are flashing. When i startup in Safe Graphic Mode (or something like that, bad memory :D) I see 3 suspicious lines which contain:
- init: ureadahead-other main process (2850) terminated with status 4
- init: ureadahead-other main process (2851) terminated with status 4
- init: ureadahead-other main process (2852) terminated with status 4
Please someone help me with my first meeting with Ubuntu :P LOL


Thanks in advance!
eXtink :D

PC:
Intel e8400
MSI P45 Neo2-FR
OCZ 1066mHz memory (dont know the exactly type :D)
ASUS GTX 275
Samsung F1 320GB
Samsung F1 750GB

---

### Post by lechien73 on 2010-08-25
Welcome to Ubuntu :)

The 'ureadahead' error could be a bit of a red herring. Status 4 means that it has just a specified mount point didn't have files that were needed during boot. It's more likely that the boot problem is being caused by your graphics card.

That being said, if you can log in to the console and post the output of the following command, it will help us to see if it is ureadahead that's causing the problem:

```
cat /etc/fstab
```

It has been documented that ureadahead can hang if you hibernated Windows rather than shutting it down fully, or if your Windows partition name contains a space.

Also, does the Live CD boot ok for you? If you select to try Ubuntu without installing, does that work alright?

---

### Post by eXtink on 2010-08-26
Ok, i did what you said and he couldnt find the file :S

> Also, does the Live CD boot ok for you? If you select to try Ubuntu without installing, does that work alright?
Nope this also dont work, he also freezes on the same point :(

---

### Post by Rubi1200 on 2010-08-26
Are you able to download and burn another CD? Perhaps on a friend's computer?

If yes, try the previous version as a LiveCD:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Also, take a look here:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677)

Other people have been experiencing similar problems. Have a look if anyone suggests a workaround.

---

