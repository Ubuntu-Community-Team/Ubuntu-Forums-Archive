---
title: "Freezing after updates"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by U_buntu on 2010-09-28
Just installed 10.04 after booting up, I installed the available updates. Now every time i try to do something The screen freezes till I pull the power. Any ideas? I even did another clean install and just installed the security updates and the same thing happend.

---

### Post by coffee412 on 2010-09-28
> **U_buntu said:**
> Just installed 10.04 after booting up, I installed the available updates. Now every time i try to do something The screen freezes till I pull the power. Any ideas? I even did another clean install and just installed the security updates and the same thing happend.

What do your logs say?

> sudo cat /var/log/messages


What video card are you using? If nvidia are you using the proprietary drivers?

Boot into the safemode and do you still have the same problem?

---

### Post by U_buntu on 2010-09-28
I believe i do have the nvidia card, it locked up both standard and safe mode. I don't know what you want from the log messages. it popped up a bunch of info.

---

### Post by coffee412 on 2010-09-28
> **U_buntu said:**
> I believe i do have the nvidia card, it locked up both standard and safe mode. I don't know what you want from the log messages. it popped up a bunch of info.

Ok, Run this and see if you get any output:

> sudo cat /var/log/messages |grep Clocksource


Im more than willing to help you if you want to send me your log file. I dont think there is anything in there that would be a security risk. If your willing to do that then Ill take a good look at it for you as Im not doing anything tonite.

If you want, Send your /var/log/messages file to coffee412 AT comcast.net

---

### Post by U_buntu on 2010-09-28
Ahh clock source isn't working. but everything seems to be running fine at the moment. It appears that the system (for whatever reason) does not run fast enough to get all the updates in place from the time it does a reboot. i turned the system off for the time being while I awaited a reply here, once I booted back up, every things running just smooth. Been up for about 45 minutes browsed the net, ran terminal commands, check list for further updates and everything is going good.

---

### Post by coffee412 on 2010-09-28
> **U_buntu said:**
> Ahh clock source isn't working. but everything seems to be running fine at the moment. It appears that the system (for whatever reason) does not run fast enough to get all the updates in place from the time it does a reboot. i turned the system off for the time being while I awaited a reply here, once I booted back up, every things running just smooth. Been up for about 45 minutes browsed the net, ran terminal commands, check list for further updates and everything is going good.

Glad to hear that things are now working fine for you. I had a system that did all kinds of weird things until it just locked up. I found it to be the clocksource was totally bad (hardware issue on MB). I changed my clocksource and no more problems. I think this is a major issue but not a ubuntu issue. Its more of a manufactuer issue with their hardware (bios?). 

Anyways, Have fun with Ubuntu!

:popcorn:

---

### Post by U_buntu on 2010-09-28
Thanks for your time and help. Like I said, that command with clocksource did not work. i dunno. tried about 5 different ways to type it in (spacing). But if its just a lag on updates then hopefully all will be fine from here on out.

---

### Post by U_buntu on 2010-09-29
Alright, apparently I was wrong. I dunno, so what i'm gonna do is wipe and re-install the system. Get a list of the updates I see, and get the computer specs in details. And see were we can go from there. Cause after the update, most of the time, the screen goes black about half way up the monitor, makes me think maybe theres some issue with the graphics card, but All is well before the updates. I'm looking at 71 updates, some i could knock off myself, others i dont know what they are exactly. i'd rather not have to check 60 updates or some thing like that to try to pin-point the problem if I don't need to.

---

