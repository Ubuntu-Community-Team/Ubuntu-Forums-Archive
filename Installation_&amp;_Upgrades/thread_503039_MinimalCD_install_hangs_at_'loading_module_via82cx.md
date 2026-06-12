---
title: "MinimalCD install hangs at 'loading module via82cxxx'"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by element42 on 2007-07-17
I'm using the minimalCD to install a command-line only system (from which I'll install fluxbox) but the install process is hanging at the 'Detecting hardware' stage; it does nothing for about five minutes, then gets to the message "loading module 'via82cxxx' for 'IDE chipsets support'", after which it does nothing at all. I left it going to at least half an hour several times.
I know that the CD is okay because I've used it to do exactly the same thing on my laptop, where it worked. Can anyone tell me what the problem is? I would love to offer more information, but as a complete n00b, I have no idea what would be pertinent, nor how I might get it...
Thanks!

---

### Post by RedSquirrel on 2007-07-17
It's a bug.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86578](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86578)
and
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)

The first link claims it is a duplicate of the second link. I skimmed through those links but I didn't see anything useful or related to a hang during installation.

This thread suggests that dapper might be an option:

[http://ubuntuforums.org/showthread.php?t=392674](http://ubuntuforums.org/showthread.php?t=392674)

I wonder if the alternate CD could be used in place of the minimal CD. I believe there's an option on there to install a command line system. I don't know if it would be any different than the Minimal CD though. Probably not, but it might be worth a try.

---

### Post by element42 on 2007-07-18
Thanks!

I did try the alternate install CD last night, but it just hung in a different place...
I think I'l wait a few days and just install gutsy tribe 3 using the alternate install image. That'll use a newer kernel so there shouldn't be a problem...?

---

### Post by RedSquirrel on 2007-07-18
Yeah, one would like to think the newer kernel would address this issue. If it doesn't, there's always dapper. Good luck. :)

---

