---
title: "High processor usage while in idle."
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by Gerard Barberi on 2006-11-13
Has anyone else experienced this problem?

I upgraded to Edgy a few weeks ago.  When my system goes idle, the processor usage skyrockets up and I see more load on my system than when I am actually using it.  I searched around the web for answers.  I killed the update manger from running in the background, but it didn't work.  Then, I killed python and perl processes.  That worked for about a week, but for some strange reason it no longer does.  I came home to hear my PC's fan roaring and more load than I've ever seen on the system.

Is it something with the 2.6.17 kernel?:confused: 

I'd like to know because I leave my system on all the time, so that I can access it from school and work (and anywhere in between).

Thanks

---

### Post by chriscando on 2006-11-13
Do you know which process it is that is driving up your system load?
Use the command 'top' in a terminal to find out ('q' to exit top) which process is hogging all the cpu.

---

### Post by Gerard Barberi on 2006-11-13
Thanks chriscando.

I restarted my system and left everything running normally.  I ran top in a terminal.  About 3 minutes into it, I found the culprit.  It was the Beagle daemon.  It took 70% of the CPU and let it go as soon as I moved the mouse.

Is this a bug?  I know Beagle needs to index files in the background, but I never had it take up that much CPU on Dapper.

---

### Post by Eversmann on 2006-11-20
BTW, i have the same problem, but the process that takes 100% CPU (and not when the computer is idle, i mean all the time) is beagle-helper.

---

### Post by wh0rd on 2007-01-25
Is there a fix for this?

---

