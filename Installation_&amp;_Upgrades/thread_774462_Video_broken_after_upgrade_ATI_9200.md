---
title: "Video broken after upgrade ATI 9200"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Shazzner on 2008-04-29
Gutsy was working fine on my laptop, then just today I upgraded to Hardy and now I can't enable desktop effects and I'm scared to change the resolution (last time it was broken I couldn't change it back).

A bunch of guides tell me to enable the proprietary driver, but nothing comes up when I go to the hardware drivers box (enable proprietary drivers is checked too).

Any ideas?

---

### Post by roolark on 2008-04-29
This sounds similar to what I was experiencing. Try following the threat I just created and see if it helps:
[http://ubuntuforums.org/showthread.php?t=774472]("http://ubuntuforums.org/showthread.php?t=774472")

---

### Post by Shazzner on 2008-04-29
I tried that, unfortunately I couldn't get anything to show up on the restricted drivers window no matter what I did.

In the package manager flgrx or whatever specifically omits Radeon 9200 for some reason I guess it's too old for it or something.

Going back to Gutsy for now...

---

### Post by Rocket2DMn on 2008-04-30
Your card is too old for the restricted drivers, so you need to uninstall them.  Here is how you enable compiz with the older ati cards using the open source drivers - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

