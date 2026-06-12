---
title: "Post-upgrade (Edgy -&gt; Feisty) performance issue"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by clembie on 2007-04-23
I can't seem to find anyone having a similar problem, so I think that this is specific to my installation, however, I recently upgraded from Edgy to Feisty (the official way) and I'm now getting processes going uninterruptible on me for up to 20 seconds and then coming back to life.  It looks as though my hard disk is doing absolutely nothing for those 20 seconds and then has a quick jolt of activity just as the process comes back to life.  

I thought that this was just happening with firefox, which seems to go uninterruptible more than other processes, but it's happening with any number of processes--if I start another process while one is uninterruptible, most of the time that one will be uninterruptible too.  Nothing stays uninterruptible, though, and there are no zombies (save a netstat zombie that went away when I restarted firefox).  I'm having problems isolating the issue.  Anyone have any ideas?

[EDIT - UPDATE]

Solved (sort of).  Apparently this is a hardware-specific issue affecting certain System76 laptops.  System76 users, see this notice:

[http://knowledge76.com/index.php/FeistyUpgrade](http://knowledge76.com/index.php/FeistyUpgrade)

Putting a CD in the drive stops the disk lockups.

---

### Post by palmerthegeek on 2007-04-28
clembie,

Are you connected to a network?  Wirelessly or wired?  I have noticed if my machine has trouble finding its network it seems to act up.  

Hope this helps...
Let me know...

---

