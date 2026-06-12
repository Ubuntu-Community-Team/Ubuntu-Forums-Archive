---
title: "system incredibly slow/laggy, process without name running"
date: 2008-08-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Benjamin_Lebsanft on 2008-08-09
After the latest upgrades tracker and empathy start even without being in "autostart", I disabled tracker because it slows down my system by a large amount but still I got a process without a name running and slowing down my system. from clicking on the x to the applications closing there are around 5 seconds "time out". What can I do?

---

### Post by RIchard James13 on 2008-08-09
Open a command line console/terminal and run the command top. It should show you everything with a process id (pid) running on the system. It sorts by those using the most CPU first. If there is one using more than 80% or so then that is the likely culprit. Post a screenshot of top running so that other people might be able to determine what is hogging your system. If you maximise the terminal window then you get more info from top.

At the moment top says that Xorg is using 37% to 40% of my CPU. But that is because I have a game running in a window behind the web browser. Top shows that as well. So sometimes it is not always the top command.

---

### Post by TheMono on 2008-08-09
Also, some system processes won't show up properly unless you run top as root - sudo top.

---

### Post by Benjamin_Lebsanft on 2008-08-11
Thanks I'm going to try that. Strange thing is, it's not always there, sometimes I reboot and get a completely usable system.

---

### Post by Benjamin_Lebsanft on 2008-08-16
Ok when using sudo top when I encouter this it seems like the X server is using ~30% and making the system almost unusable.

---

### Post by inportb on 2008-08-16
For me, Xorg usually uses minimal resources until I start manipulating windows, at which point the special effects kick in and boot CPU usage up to 50%. So if your Xorg is stuck at 30%, it might be a problem. Have you tried disabling desktop effects?

(And if you kill Xorg, does it shorten the lag between clicking the X and the window closing? LOL)

---

