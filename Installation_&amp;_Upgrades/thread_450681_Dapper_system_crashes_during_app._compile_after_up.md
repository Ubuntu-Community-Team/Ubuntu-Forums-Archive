---
title: "Dapper system crashes during app. compile after update"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by Fremont_Cunningham on 2007-05-21
I have a Dapper system that has been working well for 3 months, The system is on auto-update. uname -a :
Linux grubby 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux
This system is used to compile a huge application - takes around 3 hours (SL client) - and had been working well until yesterday, when an update arrived. I allowed the update install.

Since then any compile is crashing at about 1 hour into the compile. First the screen goes blank and the kb unresponsive, though the disk runs like the compile is proceeding. After 5 to 10 minutes the machine shuts down.

On normal reboot it dies at 'Mounting Root File system' - the screen goes corrupted and then blank.

Booting in recovery mode produces a ton of messages, A possible interesting one is something like 'INFO recovery required on root file system.' Recovery runs,,, I exit at the prompt and get a good login screen. I can then shut down and reboot normally.

I have been through this compile-crash-recovery loop several times now, it is 100% reproducible. I am suspecting that yesterday's update changed something critical. That update was probably distributed on May 19th 2007, but *may* have been released in the previous week. On the evening of the 18th the machine did compiles well, and no update had been presented.

What I lack is the knowledge of where in Ubuntu to trace the cause of the crash, or recovery, or what that update was and possibly how to roll it back.

Is there a log of updates some place and a method to roll back such updates? Searching Admin options shows nothing useful.

Fremont Cunningham.

---

