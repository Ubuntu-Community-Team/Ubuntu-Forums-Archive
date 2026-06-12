---
title: "Intermittent hangs during boot after upgrade - 'still angry after 101 spins&quot;"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2013-05-29
I have Intermittent hangs during boot after upgrade to 13.04. 

Sometimes a black screen, sometimes the first Ubuntu screen incomplete, but most notably sometimes this message
- 'still angry after 101 spins, halt"

It is now running, so I can look at log files if someone can point me in the right direction.

I had problems with Ubuntu 12.04 earlier, and thought Xubuntu might be a better choice. See my earlier problem, which could be relevant:  [http://ubuntuforums.org/showthread.php?t=2148929](http://ubuntuforums.org/showthread.php?t=2148929)

Hardware:
  Home built PC, no HW changes for a long time.
  AMD X2 processor
  ATI HD 5450 1 GB graphics card

Help!

Where do I go from here? Where do I look?

I would appreciate some advice.

---

### Post by hans12345 on 2013-05-31
I re-installed, seemed clean enough, did a reboot and again:
 "still angry after 101 spins" 
Rebooted again, and it worked.

Has anyone an idea on where to look?

---

### Post by hans12345 on 2013-06-03
I still have boot problems. Normally after 3 or 4 boots it starts up OK.

Another common boot error message (other than the one above) contains the phrase:

...   DMA_Pusher-ch 0 get ...

Where should I be looking in my logs? What do I look for?

---

### Post by hans12345 on 2013-06-05
I'm beginning to believe it is the 'nouveau' driver.

Is this my problem?

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1098316](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1098316)

---

### Post by hans12345 on 2013-06-15
Fixed by setting NOMODESET.

Thanks to post :

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by LewRockwell on 2013-06-20
Thank you for your thread, posts, and reference links!

---

