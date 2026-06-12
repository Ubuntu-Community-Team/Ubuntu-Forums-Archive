---
title: "Upgrading Feisy 7.04 --&gt; Gutsy 7.10 using upgrade manager or cdrom"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by ashgeo on 2007-10-23
I am trying to upgrade feisty to 7.04 to Gutsy 7.10 using both the cdrom and the upgrade manager without success.  The upgrade manager downloads loads of stuff, thinks about it for a while and then comes up with the following failure message:

"Getting upgrade prerequisites failed"

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

I've no idea where to report this bug, or what to do about it! :confused:

I've downloaded the cdrom which when I put in the cdrom drive feisty very kindly mounts it and then opens a window containing the contents of the disc!

I've looked on the forums and tried the ALT-F2 and entered the command in the 'run' box and nothing happens.  I know the cdrom boots ok into gutsy as have tried it 'live'.

For info I have a home-built PC, 1Gb RAM 1.2Ghz Duron processor, Asus A7V133 m/b, dual boot with windoze xp pro.  It is not new but does what I want (will upgrade sometime soon!) for the moment.

I am quite new to all this and learning rapidly(ish).  Not afraid of the 'terminal' but don't know the commands or arguments yet.....

---

### Post by ashgeo on 2007-10-28
Managed to sort it out by opening the terminal and typing:

gksudo gedit /etc/apt/sources.list

then placed a "#" in front of the repos that it could not connect to (meaning that the system did not look for files there).  Saved the modified text file.

Then ran the update manager and am now updated and on Gutsy 7.10!

---

