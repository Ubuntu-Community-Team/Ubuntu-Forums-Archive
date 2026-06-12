---
title: "[SOLVED] Synaptic Pkg manager will not load"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by MacDuff on 2008-05-07
More grief with upgrade from 7.10 to 8.04.  When I try to start the Synaptic Package manager, the load icon spins for 10 to 15 seconds then nothing happens.

Similarly, if I try to open the Software Sources the load icon spins but nothing happens.

In addition if I try to use "Add Remove Applicatons" to install Adept Manager, when I click on "Apply Changes, the load icon just spins forever.

Can anyone tell me how I can get Synaptic et al to run?

Is there a way to roll back Ubuntu 8.04 to 7.10 or must I clear the Operating system and do a clean install of 7.10?

Thanks

---

### Post by stankopp on 2008-05-08
It sounds like the problem that I was having.  It was actually an "unable to resolve host" issue.  If you search the fora for that issue, you can find the solution and just cut and paste the commands into a terminal window.  Good luck!

---

### Post by MacDuff on 2008-05-08
Thanks for that

I will give it a try

Mac

---

### Post by MacDuff on 2008-05-08
Strange! It worked!

Changed the localhost to my computer name and I could load Synaptic and Software Sources with no problem.

On both my other Ubuntu machines, the default host is localhost on IP address 127.0.0.1 and they work fine.  Of course they are running ver 7.10 whereas this is 8.04. 

Just one of the frustrations of using Ubuntu but don't get me wrong, I still love the OS in spite of many inconsistencies.

---

