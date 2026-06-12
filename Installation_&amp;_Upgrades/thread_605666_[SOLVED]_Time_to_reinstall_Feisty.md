---
title: "[SOLVED] Time to reinstall Feisty"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by CyberBob on 2007-11-07
I'm disappointed that it has come to this, but I think I'm going back to the 7.04 Feisty release.  I had everything working as I needed it to, and after upgrading to Gutsy a small printer I heavily depend upon (see [http://ubuntuforums.org/showthread.php?t=597682](http://ubuntuforums.org/showthread.php?t=597682) ) and also now my installation of TeX no longer works.

Frankly, since I'm going to have to do a fresh install of the OS I may even go with Debian Etch.  I really only blame myself for the problems I have because nobody twisted my arm to do the distro upgrade - I just let myself get lured into it because it was the newest release.  I've done each of them as they have been released since Hoary Hedgehog and I have been impressed with each version.  I wish I could say the same about Gutsy ...

---

### Post by jtekUSA on 2007-11-07
Like you, CyberBob, I am strongly considering moving back to Feisty Dawn as everything worked great on my Dell laptop and now it does not since moving to Gusty Gibbon.  Wireless and external monitor being the biggest headaches - it works until I reboot and then it does not.  In 7.04, I set it up once and it works from that point on.  If it wasn't for the huge downloads, I have considered Debian as well.

I am fairly new to Ubuntu having started with Feisty Dawn.  I had a "break" from Linux shortly after getting my laptop as I had too many issues and support was not that good at that time for laptop users.  Now, that is no longer an issue and I am glad to finally have Linux working on my laptop - even though it is still a dual boot scenario.

I will give 7.10 another go by doing a fresh reinstall and a clean slate to remove my mods.  I have a feeling I typoed when installing the ndiswrapper drivers and that is what is causing part of my headache.  :lolflag:

---

### Post by CyberBob on 2007-11-28
I was actually starting to prepare for a move to Debian Etch, having installed that distro to a spare HD, when I discovered in another thread about this little command:

```
$ sudo aa-complain cupsd 
```

... and after doing that, my little Brother QL-500 thermal label printer started humming again!  I have no idea why cupsd "broke" during the distro upgrade from Feisty to Gutsy, but the command above fixed my problem.

Now that I look at that command in the light of day, it is a fitting command, complaining to cupsd.  "Hey there cupsd!  Wake up!  Do your jobs!!"

Now my system rocks once again ...   :guitar:


p.s.  If anyone is interested in reviewing my year-long battle to get this printer working - and stay in working condition - you can read all the horrid details here:
[http://forums.linux-foundation.org/read.php?24,49]("http://forums.linux-foundation.org/read.php?24,49")

---

