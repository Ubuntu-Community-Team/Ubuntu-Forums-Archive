---
title: "ntp on Fiesty"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by dld on 2007-08-10
After upgrading to 7.04 it took me a while to discover that my digital clock was
drifting off.   I did a ps -A and found that two or three ntpd's were running, and
ntpq indicated that ntp was not working.  Restarting ntpd clears the problem, 
but I hate to do that every day.

Tried a number of things.  At the moment I have removed openntpd from /et/init.d
and set the clock to synchronize.   I get one ntpd running that way, but ntpq 
indicates delays, jitter, etc are all ZERO, and refid's are all   .INIT.
So I don't believe that ntp is working for me, but it would take days for the 
clock to drift to the point that I could tell that.

What is going on, and how do I make ntp run whenever the machine is running
without manual intervention???
    Don

---

### Post by Odrodzona-Sarmacja on 2007-08-10
During boot up there is a service run, which synchronizes computer's time with a time server on internet. Try disabling that service and see if it helps.

---

