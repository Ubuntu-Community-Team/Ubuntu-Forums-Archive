---
title: "Upgraded 12.04 to 14.04, Shell commands freezing, can CTRL+C/Z and Command OK"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by eli.d on 2017-04-15
Howdy.

I just upgraded a Ubuntu work server used mostly for a NAS.  Prior to the upgrade I could run all of my commands in the shell without a problem.  After the upgrade, my commands will freeze up after enter... I can hit control + z or control + c and then restart them again and most of the time they work fine.  Sometimes they'll freeze once or twice in a row, but then I just cancel it and restart it and it works like there was never a problem.

I use SSH for all this and changed a lot of SSH settings thinking maybe that was the problem... but it can't be SSH because the CTRL+Z or CTRL+C works fine.

A lot of the commands I've been testing today were opening up sftp connections, etc.  I'm not sure if it's only network related commands or not.  If I'm not mistaken some other commands, like just opening a file in VIM, etc will also freeze up (not verified).

I would upgrade to 16.04, but we're using this to automate some processes now and really can't afford a crash or any downtime.  The upgrade process went smooth with no failures, but I know something is not right.  I used to use this via SSH in 12.04 all the time with no problems.  Now it's this sporadic command/process hanging after execute. Until re-executed... then it's like no problem was ever there.

I tried googling and searching the forums but don't really know how to find the solution to this one.  Can't find the right words or something to describe it.  It's annoying though.  :-)

Thanks for any ideas.

---

