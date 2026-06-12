---
title: "Upgraded to Eft--stalls during reboot"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by kwilliams0 on 2007-04-01
Hello,

I just finished the "official" upgrade process on my ubuntu desktop from drapper drake to eft.  I can no longer boot my machine (final step to reboot failed).  As background, when it starts up, the Ubuntu flash screen does not load correctly (the bar underneath is a few lines and ubuntu is white).  I hit Alt-F1 to get to the command line and the last line I see is:  

fb0: VGA16 VGA frame buffer device

I do not think that is the problem though (although I don't really know).  I want to dig in and do a lsmod to see what the last loaded module is, but I don't have a command line.  I was told I could do that in inittab, but i am not sure how exactly, and haven't had luck with ait.  I tried this:

0:2345:respawn:/sbin/getty 300 ttyS0
1:2345:respawn:/sbin/getty 300 tty1
2:23:respawn:sbin/getty 300 tty3

at the beginning of inittab, but with no luck.


Additional information--I can reproduce this error if I try to boot from the edgy eft boot CD (I disabled framebuffer via fb=false, and still have th esame error).  I can successfully boot using the dapper drake CD.

Any pointers on how to troubleshoot this problem or determine what's going on would be extremely appreciated.

I did not the line: drivers/rtc/hctosys.c: unable to open rtc device (rtc0) about 5 lines before the fb0:... one.  Could that be the problem?

---

### Post by zvacet on 2007-04-02
You can not upgrade directly from Breezy to Edgy.That produced errors.If you have Edgy CD reinstall.

---

### Post by kwilliams0 on 2007-04-02
I proofread that too...I'm upgrading from Dapper Drake (6.0.6 LTS) to Edgy Eft (6.1).  I'm editing the original post.

---

