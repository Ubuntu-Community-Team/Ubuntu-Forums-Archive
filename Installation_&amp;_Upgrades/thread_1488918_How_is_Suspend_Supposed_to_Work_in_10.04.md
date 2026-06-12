---
title: "How is Suspend Supposed to Work in 10.04?"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by karat on 2010-05-20
Suspend was working fine on my machine in Karmic.  However, now that I've upgraded to 10.04, suspend doesn't seem to do anything other than lock the screen.  The network is still active, and the cpu still has activity, which causes heat to build up.

The problem is that I can't tell if this is a bug or a feature -- or if it just reset some option that I haven't found yet.  There don't seem to be any errors that I've found yet.

How is it supposed to act?

---

### Post by efflandt on 2010-05-20
I had a similar issue, along with sluggish video for some tasks.  Suspend and hibernate worked fine in 9.10.

In my case it was related to the new 10.04 default kernel mode setting (KMS) video driver (vs. previous user space video modules).  The **nomodeset** kernel boot parameter fixed my video and suspend/hibernate in 10.04, so it worked just as good as 9.10.  My desktop has legacy ATI X1300 using default video modules.

That kernel parameter similarly fixed occasional scrambled boot graphics on a laptop with Radeon Mobility X1300.

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by karat on 2010-06-01
Unfortunately, that doesn't seem to have changed anything.

Are there any diagnostic tools that will tell me if these features are working correctly?

---

### Post by David Stodolsky on 2010-06-04
Both suspend and hibernate end up at a locked screen/screen saver, without case fans spinning down. I get fan spin down with XP, but not Win7.

---

