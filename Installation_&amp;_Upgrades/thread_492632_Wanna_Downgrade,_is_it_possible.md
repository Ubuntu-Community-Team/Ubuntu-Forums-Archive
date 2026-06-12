---
title: "Wanna Downgrade, is it possible?"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by scragar on 2007-07-04
I upgraded to 6.10 because it was pointed out that I was running an old version(I was planning to upgrade again to 7.04, but considering the extra proccessing power I'm using for 6.10 I decided against it).

The problem is that various things have stopped working completely(bit-torrent, wine and Audacity) while others(mostly firefox) keep crashing(it appears to be ever time I close a tab while playing a youtube video on another tab)

What I need to know is would it be possible to downgrade to 6.06 again? I miss bit-torrent and without wine I can no-longer prove that Ubuntu is better than Vista to my friends(the only argument they have so far is compatibility, and wine solves that issue).

oh, and if it's not possible to downgrade will 7.01 use less or more processing power than 6.10 is using now, every time I open a new application my Processor hit's 100% for about 10 seconds.

---

### Post by tgalati4 on 2007-07-05
Post some specifics about your hardware.  There is not an automated procedure for downgrading (that I know of).  

Your best bet is to back up your /home directory, your /etc directory (for good measure) and start with a clean Dapper install.  

There is nothing wrong with Dapper if it runs the stuff that you need when you need it.

I had a machine run for 165 days straight.  That was enough to convince me.

---

### Post by scragar on 2007-07-05
I've got a 40 gig hard drive, 384 RAM, I can't remember anything else of the top of my head.

I will properly just wind up tarring my home directory and backing it up for a clean re-install though, it only takes 20 mins to re-install, I've already done it twice(once because skype messed up because of a bad instilation, and the other cos I accidentaly changed the entire /opt directory to chmod 777 testing how long the command would take to adjust every file in it, it was strieght after the skype re-install, so I wasn't afraid of messing things up at all, and apparantly I did...)

---

### Post by tgalati4 on 2007-07-05
You have enough RAM to run Dapper.  I have 512 in one machine and 1 GB in another.  You have plenty of disk space.  What is your processor?

You have enough space on your disk to run 2 or 3 distos and dual-boot them.  That way when you do a fresh install of Gutsy, you still have Dapper when Gutsy takes a dump.

Make sure you have a swap disk (1 to 2 GB would be sufficient) that way Live distros can take advantage of it.

So you will have a reliable, working Dapper installation on one partition, a Gutsy Alpha installation on a second partition, and a swap disk to help out any other Live Distro that you want to try.

Just a serving suggestion.

Good luck.

---

### Post by scragar on 2007-07-05
I actually only want one OS, me and a friend are almost constantly swapping files we got of bit-torrent(I download any small files, 1GB or less, he downloads the big files and un-rars things), my 40GB hard-drive has to be cleaned out weekly or I'd run out of space.

having another OS on the comp doesn't really sound like a great idea.


edit: actually, since installing Ubuntu I've noticed a HUGE amount of extra space(where was XP hiding it?), so I'm gonna try installing Dapper again by re-sizing my current partion, that might be the best option since I get to keep 6.10(to upgrade to 7.04) and 6.06 again.

---

