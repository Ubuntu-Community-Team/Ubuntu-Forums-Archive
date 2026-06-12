---
title: "Improper shutdown: &quot;A program is running&quot;"
date: 2009-01-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-01-25
Had alpha 3 installed. Do updates once or twice a day. Yesterday I updated, and now this error appears whenever I try to shutdown (from top right corner). If I click logout it does shutdown or restart whatever I originally chose.

Just wondering if anyone else has the same problem.

---

### Post by lonniehenry on 2009-01-25
I get it occasionally but it is usualy ff3.2 that is being unresponsive- sometimes even after I shutdown ff and do other things.  I chalked it up to a ff problem, but maybe not.  It doesn't do it all the time.

---

### Post by andrewabc on 2009-01-25
Thanks I'll test out the firefox theory. You mean firefox 3.1 ?

---

### Post by lonniehenry on 2009-01-25
I have been using ff 3.2a1pre beta and so I thought that because it wasn't fully part of Ubuntu it was missing something in its shutdown.  I sometimes have ff showing up in top after I have closed it.  After a few seconds it disappears.  FF3.2 works well especially now that 64 bit flash works.
 Don't know if this helps or if the problem is caused by some other process.  

JJ 64 bit updated from fresh alpha 1 install.

---

### Post by andrewabc on 2009-01-27
After some updates today/yesterday, I havn't noticed this problem again.

---

### Post by zekopeko on 2009-01-27
> **andrewabc said:**
> Had alpha 3 installed. Do updates once or twice a day. Yesterday I updated, and now this error appears whenever I try to shutdown (from top right corner). If I click logout it does shutdown or restart whatever I originally chose.

Just wondering if anyone else has the same problem.

this isn't an error. it's a nice way to tell you that there are some apps running and that you are about to kill them with your logout/shutdown

---

### Post by chrisccoulson on 2009-01-27
Well, it is an error if it occurs for an application like update-notifier, which shouldn't inhibit the session and should just shut down with no interaction, or application name is "Unknown".

I'm not sure if there is a bug in gnome-session here. I've seen the "Unknown" application a few times on Intrepid

---

### Post by RaZoR1394 on 2009-01-27
I get this both on Intrepid and Jaunty. It's nothing that really annoys me and it only happens during some power downs.

---

### Post by zekopeko on 2009-01-27
this could happen for 2 reasons. either a program is going crazy and the gnome-session-daemon can't kill it cleanly or the app doesn't have an interface to talk to g-s-d which is asking all running apps to stop their jobs and cleanly shutdown.
The nice thing about it is that if you were working in an app (doc writer) that talks to g-s-d it won't eat your master thesis but will tell you that you still have the writer app open.

---

### Post by andrewabc on 2009-01-28
Happened again. Unknown program.
Only firefox is used, so it probably has something to do with that.

---

### Post by richardh9936 on 2009-03-17
Me too.  In other circumstances, I've noticed FF taking a few more seconds to shut down.

More importantly, it's spooking some of our newer customers.  We worry that we've been infected, like a Windows user.

Could someone try to mop up the other incident records, please?

---

### Post by andrewabc on 2009-03-17
> **richardh9936 said:**
> Me too.  In other circumstances, I've noticed FF taking a few more seconds to shut down.

More importantly, it's spooking some of our newer customers.  We worry that we've been infected, like a Windows user.

Could someone try to mop up the other incident records, please?

Hmm, I havn't noticed this occuring for a while. It happens once in a while, but I think it might be because I close firefox then shutdwon computer too fast before firefox closes.

Shouldn't your customers be using a stable release 8.10? Or is it a problem on that as well?

---

