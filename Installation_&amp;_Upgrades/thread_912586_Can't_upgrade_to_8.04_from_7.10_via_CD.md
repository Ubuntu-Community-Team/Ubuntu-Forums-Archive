---
title: "Can't upgrade to 8.04 from 7.10 via CD"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by windyweather on 2008-09-06
I tried to upgrade from 7.10 to 8.04 using the Alternate CD.

The CD update process failed silently - no error box. Maybe there's a log, but I don't know where to look. Further attempts allowed me to upgrade some files - about 375 files were updated over the network.

But now I get a loop whenever I run the upgrade manager. No further updates are possible.  See the dialog attachments.

How do I upgrade the system?

Thanks,
windy

---

### Post by Partyboi2 on 2008-09-06
You should find the logs in /var/log/dist-upgrade, maybe they will give you a clue to what has happened. Strange how it is saying that a upgrade  from hardy to gusty is not supported considering you are trying to upgrade to hardy.

---

### Post by windyweather on 2008-09-07
Here are the logs.

---

### Post by Partyboi2 on 2008-09-08
I am not sure what has gone wrong, I have found a bug report [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/222048") that you could re-open if you can provide them with more info.

---

