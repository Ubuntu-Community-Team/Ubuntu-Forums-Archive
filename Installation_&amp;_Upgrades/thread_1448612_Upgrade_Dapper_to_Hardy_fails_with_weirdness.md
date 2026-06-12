---
title: "Upgrade Dapper to Hardy fails with weirdness"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by baustiech on 2010-04-06
This has now happened to me on three different Dapper (6.06 LTS) machines that I've upgraded to Hardy (8.04.4 LTS), so I'd say there's a problem and I've mucked up a "solution".

Everything's set up smartly, nothing stupid was happened or was done.  Each machine had one IDE, broken into 3 partitions: boot, swap, root.  All machines were over 5 years, maybe 10 years old.  All had important data sitting in a kind of limbo, sometimes off for months, sometimes running for weeks at a time.  

Needing a place to practice the 606 > 804 upgrade (failure on critical machine that now necessitates same upgrade that basically musn't miss of fail), I'm glad I upgraded these three boxes for practice.

Skipping all the blah blah, from a terminal I did an apt-get update; apt-get upgrade, then changed the /etc/apt/sources.list to replace every "dapper" to "hardy", then did an apt-get dist-upgrade.

This dist-upgrade thingy worked great the first time I tried it, goofing around, years ago (it's what got all the three machines onto Dapper 6.06 LTS in the first place, as they had been running the first or second Ubuntu).  Happily, dist-upgrade worked again this time.  Serious kudos to whoever invented this thing and to everyone who's made it work over the years.  From personal experience I can reveal that apt-get dist-upgrade is the single and by far the very most important reason that tens of thousands of important servers have been set to running Ubuntu.  Well, that and the fact that Shuttleworth (to whom we all owe a debt of gratitude) is doing what the greedy grubs at RedHat should have always done.

There was one goofy problem this time, 606 to 804, however.  I'll sum it up: IBM abandoned evms, which 606 installed by default, but now it's broken and causes the upgrade to fail.  Something about an error line beginning with "cpio:" at the initamfs-tools part of the process.  Not sure the exact error, doesn't really matter at this point (though it might tomorrow, and if so I'll be back to post more), because what seems to have worked was apt-get remove evms, then apt-get remove lvm-common, then redo the apt-get dist-upgrade command.  Coupla other little things needed tweaking, too, and have slipped my mind, but basically the 6.06LTS to 8.04.4 LTS apt-get dist-upgrade worked, and I wanted to share how to fix the comparatively tiny sand-particle problems and also say "thank you" to everyone who's done what we all know is total drudge work to make it the diamond it is.

---

