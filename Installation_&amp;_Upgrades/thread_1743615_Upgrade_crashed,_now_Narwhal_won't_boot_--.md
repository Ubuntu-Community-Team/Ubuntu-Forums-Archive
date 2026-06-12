---
title: "Upgrade crashed, now Narwhal won't boot --"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by NotCluelessExceptNow on 2011-04-29
Here's the situation. I helped my Brother upgrade to Ubuntu from Win XP about a year ago. He was very happy with the result and has taken a few upgrades since.  Yesterday, however, he kicked off the 11.04 upgrade and left the house for a while (he has a slower DSL connection). When he got back, the upgrade hadn't completed and when he tries to boot the PC, he gets the following. It just goes to the dual-boot selection screen and when he selects Ubuntu he sees..


 [FONT=Arial][SIZE=2][FONT=Arial]init: udevtrigger main process (349)  terminated with status 1[/FONT][/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2][FONT=Arial]init udevtrigger post-stup process  (354) terminated with status 1[/FONT][/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2][FONT=Arial]Init: udevmontor process (348)  killed by TERM signal[/FONT][/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2][FONT=Arial]The disk drive for / is not ready  yet or not present[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]
[/FONT][/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2][FONT=Arial]Continue to wait; or press S to skip  mounting or M for manual recovery[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]
[/FONT][/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2][FONT=Arial](IF SELECT M, THIS SCREEN  APPEARS)[/FONT][/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2][FONT=Arial]Root filesystem check  failed[/FONT][/SIZE][/FONT]
 [FONT=Arial][SIZE=2][FONT=Arial]A maintenance shell will now be  started[/FONT][/SIZE][/FONT]
 [FONT=Arial][SIZE=2][FONT=Arial]CONTROL-D will terminate this shell  and reboot the system[/FONT][/SIZE][/FONT]
 [FONT=Arial][SIZE=2][FONT=Arial]root@james-desktop:  #_[/FONT][/SIZE][/FONT]

So, obviously the upgrade failed for who-knows-what reason (power drop, DSL cloggage, etc). He can still boot into XP (which he hasn't done in months  "-) but needs his Ubuntu back -- what course of action would you recommend for him to either a) get his previous 10 version back or b) successfully complete his 11.04 upgrade?  He has an older PC with 1 2.4 GHz CPU and 1 GB of RAM.  He lives 600 miles away from me and I'm trying to help him figure out how to proceed.  All help greatly appreciated...Rick.

---

### Post by KegHead on 2011-04-29
Hi!

He'll need to reinstall.

KegHead

---

### Post by brownthumb on 2011-04-29
Hi, I don't have the answer for you. I have the same problem. My upgrade to Narwhal froze, so I had to restart. I have the exact same error.

I have seen some threads about "disk drive not ready" and am looking into it. It seems I cannot alter the fstab because it is a read only filesystem.

I am investigating and I'll post again if I find out anything new.

---

### Post by brownthumb on 2011-04-29
Hey NotClueless, there is another thread about this here: [http://ubuntuforums.org/showthread.php?t=1743615&highlight=disk+drive+ready](http://ubuntuforums.org/showthread.php?t=1743615&highlight=disk+drive+ready)  More people are posting there, so I'm going to post further updates to that thread.

KegHead, I don't believe you *need* to reinstall. It's just a few borked config files. It should be recoverable without reinstalling.

---

### Post by NotCluelessExceptNow on 2011-04-29
> **brownthumb said:**
> Hey NotClueless, there is another thread about this here: [http://ubuntuforums.org/showthread.php?t=1743615&highlight=disk+drive+ready](http://ubuntuforums.org/showthread.php?t=1743615&highlight=disk+drive+ready)  More people are posting there, so I'm going to post further updates to that thread.

KegHead, I don't believe you *need* to reinstall. It's just a few borked config files. It should be recoverable without reinstalling.


Thanks, brownThumb, but the link you have here is just back to this thread...

---

