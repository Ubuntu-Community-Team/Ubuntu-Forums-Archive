---
title: "Hardy - problems with evolution-exchange"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by papikondalu on 2008-04-28
The upgrade to Hardy was a breeze. I used the alternate ISO and there were no issues during the upgrade process.

The problem started when I started using the evolution mail client. I observe that within 15 minutes evolution-exchange process takes up more than 650MB of RAM. Evolution, evolution-exchange, and gconf-d take 22% of CPU each. My laptop has 1GB RAM. It becomes sluggish after 15 minutes. Shutting down evolution (evolution --force-shutdown) will bring back my system in normal mode.

Looks like some serious memory issues with evolution that is shipped with Hardy :(

Please let me know if any of you had seen this problem.

-PK

---

### Post by PmDematagoda on 2008-04-28
Did you try reinstalling Evolution?

---

### Post by lfjewett on 2008-05-01
I'm also have problems with evolution and exchange.  Seems to go off an eat 99% of one CPU ( dual cpu's ) and a bunch of memory.. At the same time it won't send or recieve any exchange email. I have a script that kills and restarts it, but it's happening every 30 minutes or so.  I have tried to uninstall / reisntall exchange and rebuild the account settings.. All to no avail.  Has anyone found a patch or work around?

---

### Post by SJI on 2008-05-06
I think i'm having the same trouble as you chaps.

Evolution seems fine whilst simply poling exchange for mail. Opening and reading mail doesn't seem to cause it too much trouble, and when the email being read is closed the CPU usage drops back to normal and powernowd behaves accordingly.

Once you've clicked on "Reply" to an email evolution-exchange-storage and gconfd-2 go a little crazy with cpu usage, and powernowd no longer steps down.

Exit evolution and then restart it, but don't send any emails and it behaves reasonably well.

I have a fresh install of Hardy.


Stephen

---

### Post by tidiemme on 2008-07-07
Same here,

Evolution + Exchange eat memory after sending one mail.

If I start everything is fine after sending a mail it becomes hungry and eats a lot  of memory...

I need to restart it every time I send an email......... :-(

Thanx
TD

---

### Post by criesca on 2009-11-19
I confirm the same problem in 9.04 and 9.10 up to the latest updates, I have a 4GB system and I can see evolution consistently trying to consume all memory and skycrapping at 100% both of my cores. I usually set it to nice 20... so it will not prevent my computer from reacting, but it never ceases and keeps eating memory untill I get tired of it not responding and kill it.

After that the system recovers really well.

I have noticed that even opening and closing Evolution will leave 1 or 2 threads behind that will eat up all the memory in the system when no client is open. If needed I will upload contents and information for those threads.

Edit:
I did try reinstalling, in fact, I can confirm this behaviour on a fresh install of 9.04 and 9.10.
So I do not think this is new. and I do not think it is miss configured.
Even the Global Address Directory is working. (I took quite a bit to configure everything)

---

