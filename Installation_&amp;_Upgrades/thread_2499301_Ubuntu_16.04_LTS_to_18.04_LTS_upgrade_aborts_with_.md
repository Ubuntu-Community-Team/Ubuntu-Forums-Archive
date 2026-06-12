---
title: "Ubuntu 16.04 LTS to 18.04 LTS upgrade aborts with error"
date: 2024-07-22
forum: Installation &amp; Upgrades
---

### Post by jackson0 on 2024-07-22
[COLOR=#000000]Hi,[/COLOR]


[COLOR=#000000]I would like to (long overdue) upgrade my 16.04 to 18.04 LTS (and then further to 22 or 24), unfortunately the upgrade aborts because there is a problem with mdadm.[/COLOR]


[COLOR=#000000]I use a software raid1 (mirroring with two HDD) on the system.[/COLOR]


[COLOR=#000000]Attached is the crash.log, can someone help me to fix this, “sudo apt update && sudo apt upgrade” has also reported a problem with mdadm...

[/COLOR][COLOR=#000000]Regards,[/COLOR]
[COLOR=#000000]Jackson[/COLOR]

---

### Post by yancek on 2024-07-22
Both 16.04 and 18.04 have been unsupported for over a year (18.04) and 3 years (16.04) so the standard update and upgrade commands will all fail since the repository locations online have changed.  You need to keep current on when a release reaches EOL.  The simplest solution would be to use a more recent release and install it and then restore data from your backups.  You could try a search for respositories for EOL Ubuntu releases if you want to try that.

---

### Post by jackson0 on 2024-07-22
That's not the problem, the system tries to upgrade, but it aborts because there is a problem with mdadm. See Crash.log

---

### Post by TheFu on 2024-07-22
Back in 2018, I upgraded my 16.04 systems to 18.04 without problems.  It might seem like mdadm is the issue, but being out of support means all the repos you need are gone.

Cut your loses.
Backup any data you don't want to lose.
Do a fresh install of 22.04 or 24.04 (if you like more risk), restore your data and get everything working as you like again.  Then set a calendar reminder to upgrade the OS in 2-3 yrs.

Of course, you could pay for ESM support, if you like.  I think a few systems are free for everyone, then try to upgrades, but doing more than 1-2 LTS-to-LTS upgrades brings and leaves a bunch of cruft.  Many subsystems have been completely replaced since 16.04.  That leave a system in a strange state where there are files left over that aren't used anymore .... or worse ... are still being used even though a new subsystem replaced it in a release since 2016.

[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm) - I think they call it "PRO" now.

---

