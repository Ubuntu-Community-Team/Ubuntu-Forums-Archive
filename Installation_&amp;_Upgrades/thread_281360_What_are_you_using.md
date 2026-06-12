---
title: "What are you using?"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by ivoencarnacao on 2006-10-20
I am finally switching to Ubuntu only, ( no more Windows XP for me [-( ) and therefore i would like to try something different from the previous installs of Ubuntu i had.

On my laptop i used to had 1024MB for /swap, 20GB for /root & /home both on reiserfs.


But now i am looking for something different like the XFS filesystem, it seems that i cant have /boot on XFS so, what should i choose to go with XFS?

In my laptop i have a 1,5Ghz Centrino, 512Mb Ram, and 60Gb Rpm Hdd.
How should i make my partitioning for the best performance?

Giev some opinions pls! 8) 



By the way, what are you guys using as your filesystem? :mrgreen: 


Thanks!
Ivo.

---

### Post by wieman01 on 2006-10-21
Stick with EXT3... Easiest & most obvious choice. Never had a problem with it.

---

### Post by Cynical on 2006-10-21
I use JFS instead of XFS.

---

### Post by Kateikyoushi on 2006-10-21
XFS uses more cache and cpu, it is faster with bigger files, because of the cache power loss can easily result in data loss.

In ubuntu I use ext3, on my gentoo install jfs sys and home, xfs for my videos, ext2 for portage.

---

### Post by ivoencarnacao on 2006-10-21
That laptop is going to do a little bit of everything.

From university programming, to a media playback (was planning to try MythTv) and a lan server.

I was also planning to try one of the encrypted filesystems! :P

Like i said, a bit of everything!


At the moment i dont have any UPS, so maybe after all that XFS isnt that of a good idea, on the other hand JFS doesnt have support and it seems ReiserFs is on that way too... ext3 seems to me to be outdated! :D

I really dont know what to do ( hope i dont get beaten here! ), except that my box will be using Ubuntu Edgy!


Any sugestion about how i should partition a 60gb hard drive?
I used to have 1gb for swap, 20 for root, 20 for home (both on reiser) and 20 for the other OS, but no more for the other OS!


Please help!

---

### Post by skymt on 2006-10-21
I use Reiser at the moment, but I'll probably switch to ext3 (or 4, or 5) next time I reformat.

---

### Post by etienne.navarro on 2006-10-22
> **ivoencarnacao said:**
> At the moment i dont have any UPS, so maybe after all that XFS isnt that of a good idea
But it's a laptop, no?

> Any sugestion about how i should partition a 60gb hard drive?
I used to have 1gb for swap, 20 for root, 20 for home (both on reiser) and 20 for the other OS, but no more for the other OS!
How come 20GB for root? 10GB is usually more than enough.

---

### Post by Sef on 2006-10-22
I'm using reiferfs now, though I have tried xfs and jfs a bit.  I may switch back to ext3 after it gets more updated (ext4.)

---

