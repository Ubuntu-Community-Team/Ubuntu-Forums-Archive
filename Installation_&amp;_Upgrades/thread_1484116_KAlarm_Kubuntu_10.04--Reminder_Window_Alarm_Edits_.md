---
title: "KAlarm Kubuntu 10.04--Reminder Window Alarm Edits Aren't Saved"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by yateendra on 2010-05-15
Dear Forum:

I had formerly been using the KAlarm application with Kubuntu 9.10 [64-bit], and did a clean install of Kubuntu 10.04 [64-bit].

It appears that a major upgrade of KAlarm has occurred between the two Kubuntu releases, such that, upon starting KAlarm on the new install, I was asked about converting the format of my existing alarm data file to a new format (which wouldn't be readable by the old version). I answered "yes" to all prompts, and the conversion appeared to complete successfully (no warning windows). The KAlarm version installed is 2.4.4.

The behavior I'm observing is that, when a reminder window pops up and I edit the content (either the text message, the time the message is to be displayed next, or both) the updated information is *not saved* (although no warning message or other error is triggered). However, it *is* possible to successfully edit and save pop-up reminders from the main window.

There seems a high probability that this is not the correct forum for this topic, so I wondered if someone might suggest where I publish this information. I checked launchpad, and it appears there are no recent posts regarding KAlarm.

Thanks!

---

### Post by yateendra on 2010-05-17
As I experimented more widely with this problem, it appeared likely that this was due to a software glitch. I registered at launchpad.net, from which I was referred to "bugzilla." I filed a report ([https://bugs.kde.org/show_bug.cgi?id=237822](https://bugs.kde.org/show_bug.cgi?id=237822)), and the software author has reproduced the problem and indicated that a fix will be forthcoming.

Thanks, all,
Cam

---

