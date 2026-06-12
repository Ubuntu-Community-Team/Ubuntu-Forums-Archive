---
title: "Trouble with Ubuntu after upgrades"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2016-11-11
Hi,

A week or so ago I did an upgrade, and then suddenly couldn't login to Ubuntu. I'm using Ubuntu 16.04.1 LTS.

**First problem:**
I get semi-randomly timed lockups, followed by a reboot with no dialog asking for permission. It happened when all these problems started, seems to be related.
[LIST=1]
[*]It tends to be during high cpu usage. 
[*]It has happened with a completely idle box, no user apps running at all. 
[*]I don't see anything in any logs 
[*]I don't see any signs of kernel panic. 
[/LIST]

I don't see any kernel panic in the logs, 


I wound up using ssh to login from remote, install xfce and then reboot, and I could finally login that way. I worked a few days, did some updates, etc. I don't particularly like xfce anymore, so I switched to i3. Don't particularly like that anymore, so on a lark I tried mainstream Ubuntu again.

The reboots have persisted through all my desktop changes, generally when I'm using the machine actively.


**Second problem:**
When I alt-tab now, it hides the app I was in, then switches to the next app.  Alt-tab again, same thing.  Once I cycle through all the open apps, I have only one visible app.  This is very frustrating.


I'm currently running smartctl tests on the disks, but IMO I should get errors in the logs if something is broken I think.

Can anyone give me an idea what might be doing this?

Thanks.

---

### Post by 1clue on 2016-11-12
bump

---

### Post by oldos2er on 2016-11-13
Thread moved to *Installation & Upgrades*

---

