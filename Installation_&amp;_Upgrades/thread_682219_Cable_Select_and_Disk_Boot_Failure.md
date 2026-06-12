---
title: "Cable Select and Disk Boot Failure"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by steve42 on 2008-01-29
OK, I've been lurking about for a while now, and I finally ran into something on an install that has me perplexed, so I thought it time to sign up and post.

Just freed up an Athlon 64 3000+ system with 1GB RAM, so I decided to try an Ubuntu 7.10 Live CD install.

The system has two IDE hard drives in it.  The first (IDE Channel 1 Master) is a Western Digital 5.2GB and the second (IDE Channel 1 Slave) is a Maxtor 3.6GB.  Both are jumpered for Cable Select with an 80-conductor ribbon cable, and both are recognized on boot with no problem.

When I booted to the CD and began the install, I chose the WD 5.2GB as the target drive.  The install went well, and I ejected the CD at the end for the reboot.  Upon restart, the system presented me with a "Disk Boot Failure" message.  Tried several times and nothing changed.  Finally shut down and disconnected the Maxtor 3.6GB drive, which had been attached in the middle of the ribbon cable, and restarted.  Ubuntu booted normally.

I shut down and reversed the connections, placing the Maxtor 3.6 at the end of the cable and the WD 5.2 in the middle.  On startup, I got the "Disk Boot Failure" message again.  I shutdown and disconnected the Maxtor 3.6 again, leaving the WD 5.2 on the middle connector.  Once again, the system started normally.

Now, I am not 110% certain the 3.6 drive is good, but it was working when I pulled it.  Is there anything else I am missing?  I'm willing to chunk the drive, but it's the second largest spare I have, so I wanted to put it to good use.

Thanks for any advice you can give.

Steve

---

### Post by yazuki101 on 2008-01-29
Hey, I dont know if this will help you, but I was having the same kind of problem with a computer I was building yesterday. It turned out to be a hardware issue with the IDE terminal on the MOBO. it would only read from one drive. (i was hooking up a CD-ROM inline with my HDD) I had to switch out the board for another one and it worked fine.

---

### Post by stevescripts on 2008-01-29
Are you sure you have the cable connected properly?

Blue to motherboard, grey to slave, and black to master?

Also, might be worth a new cable (cheap), before you give up on the drive.

Hope this helps

Steve
(who has had 80pin cables give up on me before...)

---

