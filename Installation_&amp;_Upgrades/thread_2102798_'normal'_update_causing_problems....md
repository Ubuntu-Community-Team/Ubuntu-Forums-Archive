---
title: "'normal' update causing problems..."
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by AraiBob on 2013-01-08
I did a 'normal' update, and after rebooting several applications have lost data and can't find working directories. I can see the list of recent updates, but cannot 'undo' them. I can't even capture a list of them for posting here. I will list a few.

How can I 'fix' these updates?

Nautilus (3.5.90.really.3.4.2-0ubuntu4, 3.5.90.really.3.4.2-0ubuntu4.1)
python3-distupgrade (0.190.4, 0.190.5)
and a bunch more for Python

sabnzbdplus (0,7,7-0ubuntu1^jcfp1-quantal, 0.7.9-0ubuntu1^jcfp1-quantal)
and several more for sabnzbdplus
ubuntu-release-upgrader-gtk (0.190.4, 0.190.5)

Also updates for handbrake

software-center (5.4.1.2, 5.4.1.3)

The two that are really broken are SabNZBdplus and TransmissionBT. Their working directories can't be found after the reboot of the pc.

---

### Post by ibjsb4 on 2013-01-08
You sure that normal update wasn't a partial update.

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by AraiBob on 2013-01-08
The link you pointed me to is for 'partial UPGRADES'.

I am having issues with a 'normal' set of updates. I check for updates every few days, in addition to the automatic notifications.

I have been adding PPA's to help deal with some issues with RhythmBox, so I was getting more than the usual updates.

This time, a few more updates showed up, so I accepted and installed them...

---

### Post by ibjsb4 on 2013-01-08
Do you get any error reports?  Without error reports it is hard to troubleshoot.  What about when you update, do you get error reports?

```
sudo apt-get update
```

If this is a problem with the PPA's you have added you can remove or just uncheck them.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

PPA Purge can also be used.  Its in the software center.

[http://packages.ubuntu.com/lucid-backports/ppa-purge](http://packages.ubuntu.com/lucid-backports/ppa-purge)

---

### Post by AraiBob on 2013-01-08
No error messages, no aborts, etc.

I just did another check for updates, and Mozilla Firefox has another 28MB update. Tedious, and might break.

As both SabNZBdplus and TransmissionBT are both Python based, I suspect the latest updates for Python.

How can I undo the latest updates? I know what they are, as I can see the list of them.

I did un-check the PPA for RhythmBox. and did a check for updates, yesterday. In that case, the 'report' was that the pc was up to date, and there were no more updates.

How can I undo the last updates? Windows (even though I hated it eventually) did allow that feature.

How can I undo the latest updates?

Regards, AraiBob

---

