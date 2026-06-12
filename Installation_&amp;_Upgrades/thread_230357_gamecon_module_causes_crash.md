---
title: "gamecon module causes crash?"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by oblib on 2006-08-05
This topic has been mentioned by not resolved on the forums here. I just upgraded from Breezy to Dapper, and now my SNES controllers hoooked to the parallel port doesn't work. If I run jstest, it seg faults. If I run zsnes with the gamecon module loaded, the system freezes, requiring a hard boot. If I try zsnes without gamecon loaded, it works fine. How can I fix the gamecon module? Do I need to do a kernel recompile or go back to Breezy?

---

### Post by RaymondQE on 2006-08-08
Recompiling the kernel with the latest sources does work, but the process screwed up my usplash and also required compiling the nvidia kernel source.  So now I am viewing a blank screen during bootup, but once I get into the X environment all is well.  Zsnes no longer locks up :D

---

### Post by oblib on 2006-08-19
I submitted a [bug]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55355")  and got a response that the fix was committed. I don't know what that means though. When will gamecon work?

---

### Post by RaymondQE on 2006-08-20
I believe that the next time a new security release for the kernel comes out, it will contain the fix for the gamecon module.

---

### Post by RaymondQE on 2006-09-15
New kernel update (2.6.15-26.47) out now and it fixes the gamecon crash issue.

---

### Post by maci0 on 2006-09-16
had this issue long ago

[http://www.ubuntuforums.org/showthread.php?t=197942&highlight=snes+pad](http://www.ubuntuforums.org/showthread.php?t=197942&highlight=snes+pad)

---

