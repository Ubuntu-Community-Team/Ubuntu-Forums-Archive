---
title: "Server 11.04: RAIDing a LVM help?"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by Iker Höek on 2011-09-14
Hello guys.

I installed Ubuntu server 11.04 to be used as a nagios server.
It was installed with LVM in a 80GB HDD.

Since it took me weeks to configure nagios i decided to RAID it in 2 new 1TB drives instead of reinstalling from scratch.

I've gotten so far as to clone the 80 GB disk into one 1TB drive and resize it without issue (altough it was hard because i'm fairy unfamiliar with LVM)

I don't want to trash the installation in the new drive but i just can't find a LVM-specific RAID 1-installation how-to that's not 4 years old or includes setting up LVM or does not include LVM at all.

So, question and tl;dr: Is it safe to use a not LVM aware method to install RAID 1 in LVM?

Any help would be appreciated.

[SIZE="1"]Also: got a beautiful "*You do not have permission to create tags. You may only use existing tags.*" is there anything we can still do?[/SIZE]

---

### Post by YesWeCan on 2011-09-14
Hi and welcome to the forums. :)

This may give you some ideas and it's right up to date. I can vouch for the author: [http://ubuntuforums.org/showthread.php?t=1832812](http://ubuntuforums.org/showthread.php?t=1832812)

I don't know how familiar you are with linux. You really want to make a RAID partition on the 1TB first, then an LVM, then copy your files across, then make it bootable, then add the other 1TB and assimilate it into the RAID.

---

### Post by Iker Höek on 2011-09-14
> **YesWeCan said:**
> Hi and welcome to the forums. :)
Thanks. Funny enough this is my second welcome here =)
The last one was when i joined back in 06.
Somebody pruned my posts >.>

> **YesWeCan said:**
> This may give you some ideas and it's right up to date. I can vouch for the author: [http://ubuntuforums.org/showthread.php?t=1832812](http://ubuntuforums.org/showthread.php?t=1832812)

I don't know how familiar you are with linux. You really want to make a RAID partition on the 1TB first, then an LVM, then copy your files across, then make it bootable, then add the other 1TB and assimilate it into the RAID.

"*Migrate your Ubuntu OS drive to a RAID-1 array*" I couldn't think about any more convoluted search terms to look for when I first checked the forums for info on this one, thanks!

I'll be checking the link you gave me and report later, cheers! =)

---

### Post by YesWeCan on 2011-09-14
> **Iker Höek said:**
> Somebody pruned my posts >.>
The nerve!
LOL I didn't even notice your 2006 join date; I only noticed your bean count. Otherwise I might have quipped: "I can't wait for your next post".

---

