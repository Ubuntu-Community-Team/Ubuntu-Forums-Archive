---
title: "Persistent Hard disk activity 8.04"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by ksadil on 2008-04-26
Hello,

since upgrading to 8.04 last night,  I have hard disk activity about every 4 or 5 seconds. This cannot be good. /var/log/messages does not show anything strange. Can anyone suggest how to trace the problem?

Thanks,
Kim

---

### Post by ksadil on 2008-04-28
My printer serving/sharing also seems to be broken. I cannot connect clients to my server. I previously had xp and ubuntu clients able to access my laser print. 

Please help

---

### Post by ksadil on 2008-05-04
Printer problems are solved, it appears that sharing options in the printer server settings tab were set tonot share by the upgrade. A fresh install with the AMD64 desktop has solved the persistent disk activity.

---

### Post by telemetry on 2008-05-09
I have had persistant hard disc activity in 8.04 after upgrading.  I had a sense that the problem was connected to the rather strange and new: Search and indexing option.  I was right: going in and changing and altering the settings for this badly tuned thingymabob - stopped the disk activity.

I suspect most people will be having problems because of the default settings of this new part of 8.04, which seems to be a shame as a lot of people might just give up on 8.04 if they can't find the cause of the constant noise from their hard discs.

If you go into preferences you will find the options to change the timing and constancy of this weirdness.

---

### Post by ksadil on 2008-05-09
I went looking for such a quirk, but did not find it at the time. A fresh install does not cause the problem. My new system is very good now (AMD64). In moving to the AMD64 platform I found my mail server migration was a significant chore, but fortunately that is over.

---

