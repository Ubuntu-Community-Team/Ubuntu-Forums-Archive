---
title: "Deep DEEP TROUBLE :-S"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by 555bananas on 2010-04-17
Normally, I wouldnt be stupid enough to mess with the foundation the partition on my hard drive, but I did. You see, I already installed Ubuntu on an 4 year old XP latop (60 gb I think?), and found that nothing was deleted in the Windows XP side of the hard drive. So I thought, "Why not install on my Vista Machine". So I did, and right now, it's been stalled on resizing partition at 0%, for about 20 minutes. And, due to my stupidity, I didnt back up my data (which I CANNOT LOSE BECAUSE MY CURRENT HOMEWORK IS STILL ON IT). Is it normal for it to take this long? On my XP machine resizing only took about 6 minutes. Is it alright to reboot my Vista machine? Will I lose Data? Pleeeease help!!!:confused: 
P.s. My Vista machine is x32-bit, about 585 g.b. (in total), 3 gb of ram, and Nvidia Graph Card.

---

### Post by mbuell on 2010-04-17
OOOps. 

I'm answering 'coz what you are doing and the answer u need is immediate. Right - so

Try ctrl-c. Try the gui "quit" or "abort" button. Now. 20 min is not normal, and you will probably not lose anything, yet. I'll say more in a 2nd reply. Sending this one now.

---

### Post by 555bananas on 2010-04-17
No worries, I just got to step 5 like right now, maybe my hard drive was slighty too big or something. But thanks for the help anyways :):P

---

### Post by lisati on 2010-04-17
How big is the Vista partition? I've had resizing of partitions take several HOURS.

---

### Post by mbuell on 2010-04-17
Ok - now taking a few more min to answer.

What are you using to do the partitioning? I'm assuming a gui partition editor - like the live cd, yes? If yes, where does it say it is - 0% complete, 12% complete, 50% complete? Does it have a "details" button to click? Has it finished any tasks at all in details?

Based on my usual experience, I've guessed that your answer to all these will be 0%, and no tasks complete. Gparted, or whatever you are using, choked at the get-go. If that is the case, you should be able to cancel the partitioning and get your data back. Actually, if you have indeed "hung" at the start of the partitioning, you should be able to kill it - clean or dirty - and reboot without any ill effects. 

Of course, after you've done that, you will certainly do a backup before you get started again.

---

### Post by mbuell on 2010-04-17
But - if your process is farther along - you are probably borked. There are things you can do to recover partially edited partitions and data - but I've never been unfortunate enough to have used them. 

However, I will say this - if you intend to recover ANYTHING from the partition that is going bye-bye, you need to stop the process asap. Any data writing on that area of the disk that was that partition will endanger recovery of the data on that partition. 

Having said that, if your partition is borked, the COST $$$ for recovery is probably expensive. You may rethink the value of redoing your homework.

---

### Post by mbuell on 2010-04-17
> **555bananas said:**
> No worries, I just got to step 5 like right now, maybe my hard drive was slighty too big or something. But thanks for the help anyways :):P

Ah - ok - good. Altho obviously others have had different experiences, I've never had a partition resize take hours. I could see 10 to fifteen minutes on a big resize with no progress, but if it took longer than that, I'd kill it and restart, assuming that it hung. 

You still might want to abort the install, and make a backup, but at least you seem to feel that things are going in the right direction, and that is what counts.

Best of luck;

---

