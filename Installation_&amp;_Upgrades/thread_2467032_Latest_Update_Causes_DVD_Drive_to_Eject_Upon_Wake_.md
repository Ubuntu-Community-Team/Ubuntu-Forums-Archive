---
title: "Latest Update Causes DVD Drive to Eject Upon Wake From Sleep"
date: 2021-09-13
forum: Installation &amp; Upgrades
---

### Post by geeky-1 on 2021-09-13
Not sure how to submit this as it's not a crash, but the latest update to Ubuntu 20.04.3 LTS causes my DVD drive to eject whenever I wake my computer from sleeping.

---

### Post by guiverc on 2021-09-13
Does on my box too (*though I didn't have the issue when using 5.11 kernel if I recall correctly, it started with 5.13 for me*).

My filed bug can be found at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1942299](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1942299)

Note:  I'm on *impish* and have noticed it only on two boxes mentioned in that report.
(I don't generally suspend *focal* so it may impact me there too, I've only noticed it on my primary *impish* system, and in QA-testing *impish* as well; I didn't notice it with *focal.3* testing but that was awhile ago now*)*)


I did see a report by a *focal* user though like you, it was filed at [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1943379](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1943379)

I'd suggest you look at the second report & click the "*affects me too*".

(I haven't done that, as I've only noted it with *impish*)

---

