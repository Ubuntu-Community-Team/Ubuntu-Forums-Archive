---
title: "Server install stops during Select and Install"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by sandau on 2006-06-01
I've run this thing twice and the first time it stopped at 25%, this time it stopped at 18% "preparing lvm2".

is this thing downloading packages and servers are hammered or what?  I know my inet connection is good.

Note: I'm installing in a virtual machine, Parallels on OS X.  I've installed many versions of Breezy on it with zero problems.

Thanks.

---

### Post by sandau on 2006-06-01
ok, i guess i'll wait until this thing is fixed, maybe in a couple of days?

---

### Post by llamakc on 2006-06-01
Yeah I believe traffic is really heavy. I just tried to install tetex and it took forever.

---

### Post by sandau on 2006-06-02
tried another install this morning...stopped at 5% this time...definitely going backwards...

---

### Post by sandau on 2006-06-03
can i expect this thing to ever work?  anyone home?

---

### Post by sandau on 2006-06-03
well, 5th time, i'm gonna consider Dapper Drake a Flappin Fake because it doesn't install for me at all and no one here seems to want to help.  I was hoping for a little more LTS but not seeing any TLC....

Tried it again, still stops randomly on "Select and Install software", this time at Retrieving file 37 of 64 at 5%.  I guess my first attempt was best at 25%.

---

### Post by llamakc on 2006-06-03
Is it fetching these packages from the net? You can move over to one of the tty's (ctrl-alt-F2, -F3 I forget which one) and watch the output of what's going on.

If its trying to get the packages from your install cd, maybe your iso is bad or the cd has errors from the burn?

---

### Post by cjking on 2006-06-03
Try another partitioning scheme other than LVM

---

