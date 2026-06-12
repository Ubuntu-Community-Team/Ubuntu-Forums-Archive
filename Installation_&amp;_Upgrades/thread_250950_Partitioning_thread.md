---
title: "Partitioning thread"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by Anonii on 2006-09-04
Greetings,

today I decided to change to Edgy Eft. This means: Backup everything, download edgy iso, boot iso, *parition the freaking hard drive* and then install edgy.
While I was thinking this idea, something flashed in my head: "Why the hell do I always use the autopartitioning?"
-Since I'm dic*head and I'm not thinking of using automated tools, I would like to learn more about partitions and partitioning.
First of all, I'd like to try a not-that-simple partitioning scheme (not that advanced too :P), that includes seperate partitions for: / , /tmp, /var, /usr and /home. The automated tool only creates two partitions, / and /home, afaik.

So, after trying to learn more things on this partitioning scheme, I didnt find any really good source of information, and decided to give up the edgy upgrade and learn more about partitioning.

My hard drive is 80GB. And it will be a Desktop PC with just one user. I know that, this partioning scheme is not needed for a desktop PC, but firsly I want to learn some things, and I dont really care about the minimal performance boost I'll get.

So, can you recommend me some sizes for the different partitions, and as well, why did you chose this size? Also, if you recommend me to add more partitions for other directories like /etc/ or others, tell me so.

Thank you!
>:3

---

### Post by facefur on 2006-09-05
I'm a long way from expert on this, but here's my experience.  I've been trying various Linux flavors, but Ubuntu is now my confirmed choice.  I'm not sure how many partitions are really needed (my work laptop has only one = / + swap space).

I have the following partitions on my drive, which is only a 30G:

WinXP:  /media/windows,  15G - that's what it needed
Linux:  /home             4G - seemed to be a good size
        /usr              4G - same reason
        swap              2G - 2x my 1G memory
        /root             500K - someone said this would be fine
        /                 remainder

This scheme allowed me to go from Breezy to Dapper without touching my personal files on /home.

YMMV

---

