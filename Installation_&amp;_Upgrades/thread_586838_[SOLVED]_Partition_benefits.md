---
title: "[SOLVED] Partition benefits?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by anotherdisciple on 2007-10-22
I plan to Reinstall Gutsy soon because I'm a newbie and I've probably messed stuff up... also I've heard about a different way to partition your hard drive that I think has some benefits.

I have Vista taking up the first 23 gigs of my 160 gig HD, then I have a 2.5 gig swap, and the rest is the root "/". I have heard a lot of people say that you should have a swap, root (system), and /home partition. They said it can make clean installs of new version easier because you don't have to backup all of your data... it just stays on your HD while you put the new version on. Also, if you really mess something up, you can reinstall instead of trying to fix it without losing your music, pictures, etc. ??? 

So here's the real meat of the questions... How much room should I have for the system partition? Do programs and other software store on the /home partition, or do you need to leave room on the system partition for programs? When I clean install Ubuntu 8.04 (whenever it comes out) will I need to do anything to make sure I don't have two "/home" folders since I'll already have a "/home" partition? What else do I need to know about good partitioning rules?

Thanks,
         Nick

---

### Post by forestpixie on 2007-10-22
when you reinstall with a /home folder you tell the installer where you're home is but DON'T format it and it should be there for you afterwards - you need to use the same username and password when you reinstall I've read.

Configs get put in home but generally programs go into /

---

### Post by Herman on 2007-10-22
Hello anotherdisciple,
To my way of thinking it's not so much how big should your /home be, but how much room do you need to allow for / (your root partition) for adding software.
Your / (root) partition is probably less than 1.8 GB when Ubuntu is newly installed but will probably need more room as you add more software to it.
Most people don't know how much software they might want to add. We just add it when we see an idea and want to try it out. There is a lot of great free software available to be installed in Ubuntu. You can even add other desktops, for example you can install KDE in Ubuntu so you can choose either Gnome or KDE at login and use Ubuntu or try Kubuntu in the same installation. That kind of thing takes up room, so you want to leave yourself a big enough / (root) partition to  leave yourself room in case you ever get a notion like that. 
Say around 5.0 GB, I would guess, should be a large enough / (root).
You can still resize it larger someday if you ever need to with GParted.

Then you could make your /home partition take up the rest of the disc, because for most people, added files take up far more disc space than software, especially if you save music and video like most people these days.


I don't use separate /home partitions myself though, I have tried it, but I don't like it. I prefer to have a whole 'nother Ubuntu operating system instead, with both of them installed as one single /.
I guess I just like to be different, I have a whole different set of strategies about how to do all kinds of things than most other people. 

Whatever you do just have fun, 
Regards, Herman :)

EDIT: But don't forget, just because you have all your data in a separate /home partition doesn't mean you don't need to make regular backups, of at least your most important data.

---

