---
title: "Near impossible to boot, multipul errors"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by darkcard on 2008-09-12
Last night has been pretty interesting for me. I downloaded the Ubuntu 8.04 image and burned it to a disk. When I booted off of it, I checked to see if it was valid first and it was. Then I tried to start with it, and it wouldnt get past the third little bar after ubuntu's little bar bouncing screen. I downloaded and burned the alternate CD and it installed off the bat. After a restart, I got this error after the Ubuntu load screens went away.

init: rc-default main process (4904) killed by SEGV signal

I looked around the internet, I could not find this problem. I ended up reinstalling to find the same problem. Not satisfied, I tried to fix the problem.

I went into recovery mode and ran a shell in the two enviorments it had. Then I restarted and it booted, to my surprise. I started to install updates, only to find that in the middle of installing them it had frozen. After a restart, it loaded into a black screen that I couldn't do anything with.

More surprised and not satisfied, I ran recovery mode again. It gave me some weird error:

Call Trace:

-==== BUNCH OF STUFF====
Bash: The: Command not found

Then it had me in a terminal like-enviorment. So I typed in exit and it restarted itself. After the ubnutu load screen, it gave me the exact same error but with a different process:

init: rc-default main process (4477) killed by SEGV signal

Next time:

init: rc-default main process (4612) killed by SEGV signal

The next start, it booted, somehow. I tried to get on firefox to see what the problem could be, to find that firefox, or any application, would not load. I tried to update, but it said I had to do it maunally. I thought the default root password was root or admin, neither worked so I couldn't do it manually. Because nothing would work, I restarted my computer again.

I got:

init: rc-default main process (4650) with status 139

After a restart, the load bar stopped halfway and i restarted.

Then I loaded in recovery mode and it ended up in this:

Edevd-event(4324): run program: '/lib/udev/auth_}id' abnormal exit

Thats where i gave up. Any ideas?

Note:

A gig of ram, so memory shouldnt be a prolem. 160 gig hd too.

---

### Post by Detailedghost on 2008-11-26
I'm actually having the same problem too, but instead it says for me "init: rc-default main process (5131) killed by SEGV signal". I did all the things you did too and still have the same problems. So we're stuck on the same boat.

---

### Post by Detailedghost on 2008-12-19
ok I think I got it to work. What I did was I reinstall ubuntu and booted it up fine with my onboard video. Then I installed the drivers to my video card and rebooted. I set my BIOS to my NVIDIA card and i worked fine. Now I'm not sure if it'll fix your problem but it did fix mine.

---

