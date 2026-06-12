---
title: "Mulitple bash sessions logged!"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by Morons on 2007-07-25
HI,
I have a need to log all my concurrent bash sessions for user x, root, etc. to .bash_history.  Currently only one session log to .bash_history and a lot of info seem to be lost.  Is there an setup/config that can do this?
Please advise

Thank you very much :confused:

---

### Post by eentonig on 2007-07-25
what do you want to accomplish with this?

couldn't you just merge the info from the seperate user .bash_historie files?

---

### Post by Morons on 2007-07-25
No, I sometime make 2 or more ssh sessions and log onto linux boxes for hours at end, one sometime monitoring and tunning tail on logfiles / debugguing, the other i type commands, all of these sessions seem to use one single flatfile .bash_history and does not create seperate logs, an pain in the backside If you ask me.  If only it was logging via syslog it would have worked in concurrent session.  I have no clear way of sying witch bash session actually gets written to disc and witch not, maybe (my suspicion) the 1st one actually lock the file and the rest does not log at all!

---

