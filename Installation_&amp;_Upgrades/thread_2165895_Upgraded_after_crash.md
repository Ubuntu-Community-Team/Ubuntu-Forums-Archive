---
title: "Upgraded after crash"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by Boosh007 on 2013-08-06
About a week or so ago, my system crashed (10.04.4 LTS Lucid Lynx). The hard drive was so fragged that I couldn't use it anymore. So I purchased another. It was then that I decided to upgrade to a newer system, so I got 12.04.2 LTS Precise Pangolin. As of today it's brand new, I just started to enter back all the sites and files I could find from the old system that weren't ruined. It wasn't until I shut it off completely that I started to have problems. For some unknown reason, when I boot it up, it goes black, like a huge terminal page. In tiny three-point text it asks me for my username and password. If I out it in, it waits for more commands like a terminal, but I literarlly have to use ctrl-alt-delete to restart it. I have to do this three times and sit through three restarts before the magic number four, boots it in normal mode. It's annoying to say the least. Any ideas?

---

### Post by VMC on 2013-08-06
If you mean by "fragged" , that it was fragmented, then why not just reformat the hard drive instead of buying a new one?

If you know how to manually edit a live grub2, then at the end of the linux line add *nomodeset* and see if you can continue. If you can, that should indicate you need to look at you video driver.

---

### Post by Boosh007 on 2013-08-07
It was fragged so badly (had so little information on it), that it wouldn't accept even the simplest of commands, claiming there was no such command listed. It gave me lists, but even those came back with the same replies. I figured a new hard drive was cheaper (about $26) and less of a headache than finding a command it would accept. It would seem that I may have jumped the gun also. It has been booting up normally since last night when I tried to get the netflix-desktop to work right. I was told on another forum, that I may have inenvertantly downloaded a small segment of the server i836 download with the desktop copy which could steer my system into the wrong direction. The program command they had me use to fix the netflix-desktop, must have fixed the problem, since it's been booting up fine now.

---

