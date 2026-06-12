---
title: "Upgrade to 8.04 failure; now Ubuntu hangs after login screen"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by MNA_Novice on 2008-04-30
While installing upgrade to new release connexion with remote server was interrupted - event logs show continued timeouts and "will retry after 60 seconds"; at some point in this hang of the Upgrade Installer (Ubuntu was running w/ no issues at this time) someone else restarted the machine... 

Now, Grub launches, Ubuntu launches, the login screen shows up, I login and password, then we hang at a beige blank screen, no actions, no nothing.

Is this repairable w/out reinstalling and reconfiguring? I had set this up as a LAMP Server to run our Wiki, and don't really want to redo all that... I've tried the xfix command from Grub - after running it, same issue upon restart.

any Linux gurus out there with good advice?

Thanks...

---

### Post by Keith5698 on 2008-05-01
I'm experiencing the same issue.  I did not encounter any errors during install, but the computer just hangs at a beige screen after I log in.  I tried various sessions, but they all respond the same.  I'm brand new to Linux, and I'm not sure how I can troubleshoot this issue.  Any assistance would be greatly appreciated.

---

### Post by Peter09 on 2008-05-01
what is your graphics card? Try booting in recovery mode and typing 

```
startx
```

what happens?

PC

---

### Post by mk122 on 2008-06-05
Hi, I am also having this problem with a Toshiba Satellite A70. I tried typing in "startx", and the same hangup happens, with low-grade graphics.

---

