---
title: "Partition Question"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by usarmykr on 2007-10-07
Ok, I know I can only partition one drive 5(maybe its 4, will only let me creat 4, then the remaining 23gb says"unusable") times, but forgot when I decided to reformat totally(did the DoD 3 passes of 0s deal on the driver) because of an issue where 1440x900 would not show up on my list of resolutions, even after driver/windows patching.  So on the my issue, do I NEED a "/" "/home" and swap? or can I do without a "/home" and have my things stored on the root folder?  The reason why I ask is I use vista as my primary OS, as many do I am sure (I am a gamer) and have gotten into the habit of partitioning my HDD into an OS and data part, which seems to have bitten me n the ***.  What do you guys recommend doing?

---

### Post by usarmykr on 2007-10-07
Also, what is logical and primary mean exactly?

---

### Post by ryanVickers on 2007-10-07
You can only have 4 primary, but then if you want more, make and "extended" and then put "logical" ones in side it (extended it like a container, logical are primary inside an extended)

For simplicity, just make a 1GB swap and everything else as "/".  you can't have everything on the root folder, but on the root folder, there will be a folder called /home with your stuff in it (under another folder called your user name).  "/" is like C:\, and "/home" is like "C:\Documents and Settings" :).  I would just keep vista (or not ;)), shrink it, and make a 1GB swap and everything else (that's not Vista or swap) as "/"
[B]
So short version: 
*-*[I]make a vista partition (primary)
-make a 1GB swap (primary)
-make everything else "/" (primary)[/I][/B]
[B][I]
Extended is like a container - you then have an (unlimited number) of logical partitions inside it[/I][/B] (they are basically primary, but inside the extended)

---

