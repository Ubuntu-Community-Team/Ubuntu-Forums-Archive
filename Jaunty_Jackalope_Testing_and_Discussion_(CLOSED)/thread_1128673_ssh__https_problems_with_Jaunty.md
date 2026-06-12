---
title: "ssh / https problems with Jaunty"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MediaBlitz on 2009-04-17
I upgraded from 8.10 earlier today and after the reboot Firefox would not load any https sites and none of my ssh connections worked (ssh, sshfs, git and subversion all fail).

Everything was working perfectly on Intrepid. I've been though and checked everything I can think of but I'm not exactly a Linux expert so any suggestions would be much appreciated.

Cheers.

---

### Post by Cybie257 on 2009-04-17
Reinstall SSH for starters. With a server at work, when I upgraded a 7.10 machine to 8.10, I had to re-install SSH and that fixed it. 

As for the firefox HTTPS problem... Small maybe that that might help? Or try re-installing SSL???

Upgrading distros always breaks something. Thats why installing a new release as a fresh install is recommended by most. So, if you choose to upgrade, gotta be ready to fix all the broken things. :)  

I notice that VMWare workstation breaks every time I do an Upgrade. :(

Hope this helps,
   -Cybie

---

### Post by MediaBlitz on 2009-04-19
Thanks for you help Cybie.

None of those things worked so I rebooted the router and that fixed it. Very odd problem!

---

