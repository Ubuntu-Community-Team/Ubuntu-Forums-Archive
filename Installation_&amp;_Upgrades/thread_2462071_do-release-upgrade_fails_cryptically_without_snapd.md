---
title: "do-release-upgrade fails cryptically without snapd"
date: 2021-05-12
forum: Installation &amp; Upgrades
---

### Post by jjacobsohn on 2021-05-12
I updated my 20.10 server to 21.04 and had to solve a problem along the way.

I minimize the attack surface on this VM server machine by running only what I know I need. I run snaps only within VMs so I disabled snapd on the base machine.

Turns out that the do-release-upgrade installer assumes snapd is available. Failure signature is:
> -- 0:hirsute -- time-stamp -- May/11/21 21:34:25 --


Restoring original system state


Aborting



Googling revealed a bug report from a prior release upgrade that found snapd absence caused a silent abort. The bug was rejected.

Enabling and starting snapd cleared the problem.

Posting in case someone else encounters a similar issue.

---

### Post by TheFu on 2021-05-13
Thanks for the post.  Time to make a decision about the OS our servers use, I suppose.

---

