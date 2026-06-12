---
title: "Lucid Lynx Black Screen of Death with Intel Video Chipsets"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by lelamal on 2010-06-07
If like me and many other owners of Intel Video Chipsets, you are extremely pissed off because you couldn't upgrade to Lucid due to the infamous black screen of death, read on for the workaround that worked on my laptop may work for you as well. But don't expect a final fix, for it's just works around the issue.

I have a Thinkpad R50e, and used Ubuntu on it up to Karmic with satisfaction. Unfortunately, I was unable to upgrade to Lucid due to the persistent black screen that appears after GRUB, during Plymouth. I tried some workarounds ([https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)), but none worked. In the end, I had to switch to my desktop where I installed Kubuntu, while left the laptop unused with Karmic on it. :(

Up to today. :P

I followed the discussion around this issue at [http://www.ubuntugeek.com/ubuntu-10-04-lucid-lynx-and-intel-video-chipsets.html](http://www.ubuntugeek.com/ubuntu-10-04-lucid-lynx-and-intel-video-chipsets.html). I already wrote about this workaround there, but wanted to share it here as well, for people might bump into it more often, on these forums.

OK guys, here goes: I decided to get back to the only official documentation on this bug that I knew about: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes). Last month I had already tried *Workaround A* like many of you, with exactly the same disappointing results. Today, at first, I tried *Workaround C* (Upgrading), but it didn&#8217;t help. Then I tried **Workaround D**: downgrading, this time. And I must say with relief that 2.6.31 kernel really resolved the issue completely. I had it because I dist-upgraded my system, but I&#8217;m sure you can easily get it, if you only have 2.6.32 because you fresh-installed ubuntu - just don&#8217;t ask me how, for I never did it :). I just wanted to share it, because I know how frustrating this issue was, and this workaround may give you a completely working environment as long as you keep booting from the 2.6.31 kernel (choose it from GRUB at startup). And yes, video works flawlessly, too! Yay! :P Enjoy!

---

