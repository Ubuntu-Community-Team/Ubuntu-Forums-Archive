---
title: "Why does mdadm want postfix?"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2013-07-17
I'm running Xubuntu 13.04, it's been running for awhile.

I just installed a couple disks I want to set up as RAID, which by itself is no big deal to me, I've done it before.

I tried with apt-get and synaptic both, mdadm wants postfix.  I installed both, and then was able to completely remove postfix with evidently no issues.

Is this in the repository or is it yet another sign that my package manager is messed up?  I've been having issues.

---

### Post by newbie-user on 2013-07-17
You need postfix to send you email alerts if your array gets degraded. Having postfix installed is not necessary for mdadm to function correctly; however, depending on your needs and/or the physical location of the computer, you might want to receive email alerts.

---

### Post by slickymaster on 2013-07-17
If you are using mdadm and smartd to monitor your hdd and raid, you probably want to be informed if they find any errors or so. So there is postfix which can send mails via sendmail to your e-mail address.

---

### Post by 1clue on 2013-07-17
It's my workstation.  I'll know.

Besides, why would it be a prerequisite to load the app?  Wouldn't that be something you would design into your overall plan?

---

### Post by newbie-user on 2013-07-17
I suppose it's included by default because RAID is more often found on servers which are left to run on their own with little user interaction.

---

### Post by Cheesehead on 2013-07-17
> **1clue said:**
> It's my workstation.  I'll know.

Besides, why would it be a prerequisite to load the app?  Wouldn't that be something you would design into your overall plan?

mail-transport-agent, which could be any of several possible packages including postfix, is a recommended (*not required*) dependency of the mdadm package for the reasons already described.

You can easily see the dependencies of packages several ways, including apt-cache or synaptic.

You seem to be using package managers that assume you want the recommended packages. That's a setting in your package manager. You can change it.

---

### Post by 1clue on 2013-07-17
Usually I either don't mind or maybe don't notice.  This one struck me as strange.

I understand the reasons now.

Thanks.

---

