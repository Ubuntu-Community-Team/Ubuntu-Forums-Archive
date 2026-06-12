---
title: "Toolchain Ready"
date: 2009-04-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2009-04-28
from: Martin Pitt
reply-to: [email]ubuntu-devel-discuss@lists.ubuntu.com[/email]
to: Ubuntu Development Announcements <ubuntu-devel-announce@lists.ubuntu.com>
date: Tue, Apr 28, 2009 at 2:33 AM
subject:Karmic open for development
mailing list: ubuntu-devel-announce.lists.ubuntu.com 

Hello world,

Following a brief period while we got the toolchain into shape, the Karmic Koala is now open for general development. Please remember to wear your seat-belt, and remember that bugs in the rear-view mirror may be closer than they appear. Automatic syncs from Debian will begin shortly.

The release schedule for Karmic is available at [https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule) . To summarise the next few months, we expect to be able to produce the first milestone in mid-May, to cease automatic syncs from Debian towards the end of June, and to enter feature freeze at the end of August.

We do not recommend that users upgrade to Karmic at this time; it is likely to be in very considerable flux until the initial round of merges is complete. As ever, any developers wishing to take the plunge at this early stage should ensure that they are comfortable with recovering from anything up to complete system failure.

Good luck!

--
Martin Pitt                        | [http://www.piware.de](http://www.piware.de)
Ubuntu Developer ([www.ubuntu.com](www.ubuntu.com))  | Debian Developer  ([www.debian.org](www.debian.org))

---

### Post by go7Ul1ai on 2009-04-28
And the journey begins :)

---

### Post by autocrosser on 2009-04-28
Is your Rocket-belt on??? Thrusters ready--Rogue3 to Rogue leader--the word is GO!!

---

### Post by VMC on 2009-04-28
I'm assuming it works this way. With an installed Jaunty, change the sources.list to point to Koala. Then sudo apt-get update & sudo apt-get upgrade. Is this right?

If so, then I'm basically running Jaunty until several updates from the toolchain are in place. I also realize that this should be done from a test partition.

My "real" Jaunty is on another partition. Someone mentioned that there is a "sticky" on this subject.

Thanks, and I'm in for the ride. Sounds like fun(?). I've never done this before. Not to worried, it's just a partition that can be reinitialized.

Most important for even attempting this, is to help report bugs.

---

### Post by autocrosser on 2009-04-28
That works---And if you have changed your sources---as soon as you update--You are "Karmic"---see: [http://ubuntuforums.org/showthread.php?t=1140437](http://ubuntuforums.org/showthread.php?t=1140437)

---

### Post by Kareeser on 2009-04-29
[quote=Technoviking]As ever, any developers wishing to take the plunge at this early stage should ensure that they are comfortable with recovering from anything up to complete system failure.[/quote]

Hehehe... I know it was said completely seriously, but I like this :)

VirtualBox FTW.

---

### Post by Luffield on 2009-04-30
> **VMC said:**
> I'm assuming it works this way. With an installed Jaunty, change the sources.list to point to Koala. Then sudo apt-get update & sudo apt-get upgrade. Is this right?

I think you need another step: sudo apt-get dist-upgrade. I'm not sure.

> **Kareeser said:**
> VirtualBox FTW.

Basically I agree wholeheartedly, but using Karmic in VirtualBox on a Jaunty host I got my *host* PC rebooted without warning twice in two days. Really strange.

---

### Post by Reiger on 2009-04-30
That's what happens with kernel panics and similar. A memory leak, perhaps?

---

