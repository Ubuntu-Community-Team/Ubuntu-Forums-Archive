---
title: "Why are Snaps not downloaded in background when they become available?"
date: 2024-03-06
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2024-03-06
My Ubuntu system just requested that I restart to apply changes.  When I signed back in I opened a terminal and types "sudo snap refresh".  


[LIST=1]
[*]Why does an Ubuntu system restart not perform "snap refresh" along with all the other updates to ensure that the system really is up to date, since Canonical intends to move as much of the software management to Snaps for its own convenience.
[*]Why are the updated Snaps not downloaded in the background, rather than waiting until "snap refresh" is run.  Some of these Snaps are hundreds of megabytes in size and even on today's multi-megabit/second connections they take up the time of the user for no obvious benefit.
[/LIST]

---

### Post by TheFu on 2024-03-06
Snap updates are checked 4x a day by default. If you aren't seeing that, something is wrong with your system - or the snaps are being rolled out slowly and you aren't in the group to get it this time. There are downsides to getting new code before everyone else. Count yourself lucky if you haven't been burned by that yet. It will happen.

Corporations want the version of software they have installed, not something new.  This is important for business continuity.

Just because YOU aren't happy with the default 4-checks daily that snapd does for updates, that doesn't mean everyone else wants their work disrupted in the middle of a day or even during a work week.

I want patches to only happen when I specifically request them.  That's usually on Saturday mornings, so I have 2 full days to fix anything that failed.  Usually, everything is fine, but once every other year, something gets really fouled up and I need to fix it manually.  About once a decade, I need about an hour to fix it.  If it takes a hour and it isn't fixed, I'll wipe the system and load from backups.

Canonical is trying to manage resources for millions of users, not just 1.  Look at it from that perspective.

BTW, I hope you aren't running 19.10 anymore. Support for that ended in July 2020.

---

### Post by ian-weisser on 2024-03-07
> **7-webmaster said:**
> Why does an Ubuntu system restart not perform "snap refresh" along with all the other updates to ensure that the system really is up to date[?]
 
It does exactly that in many circumstances.

Neither debs nor snaps check for updates at system restart unless a certain amount of time has passed since the last check. And they check at different frequencies. Since both check (and install) mostly in the background, it's unclear why the system restart criteria is important.

> **7-webmaster said:**
> ...since Canonical intends to move as much  of the software management to Snaps for its own convenience.

Invalid assumptions. Irrelevant. 

> **7-webmaster said:**
> Why are the updated Snaps not downloaded in the background,  rather than waiting until "snap refresh" is run.

Background downloading was introduced in Ubuntu 23.04.
Are you perhaps using an older LTS? 19.04 is long dead.
LTS is not the path to up-to-date software.

---

