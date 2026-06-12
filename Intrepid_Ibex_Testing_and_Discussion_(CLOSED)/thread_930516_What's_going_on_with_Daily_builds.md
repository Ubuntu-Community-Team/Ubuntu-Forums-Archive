---
title: "What's going on with Daily builds?"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kosimo on 2008-09-26
Last daily build is from 3 days ago. 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Any particular reason why the building team has stop building iso's?

Thank you

---

### Post by OrangeCrate on 2008-09-26
Beta freeze?

[https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule)

> 
For the preparation of the beta release (see BetaProcess), uploads for packages in main and restricted are held in the queue and are subject to manual approval of the release team. The purpose is to stabilize the archive, allow the archive administrators to consolidate it and fix package inconsistencies, and be able to fix critical bugs quickly and in an isolated manner.


---

### Post by alienexplorers on 2008-09-26
I don't know why,  I have been wondering about this myself.  I like using the daily builds.  Forgot all about the beta freeze.

---

### Post by Kosimo on 2008-09-26
I don't think that a beta freeze is the reason. I'm experiencing a booting error (so I can't try intrepid) and I was trying to get the latest daily build to see if it has been fixed... But looks like I have to wait

---

### Post by Perpetual on 2008-09-26
> **Kosimo said:**
> I don't think that a beta freeze is the reason. I'm experiencing a booting error (so I can't try intrepid) and I was trying to get the latest daily build to see if it has been fixed... But looks like I have to wait

Kosimo, still no luck getting the live cd to boot?  I am in the same boat as you.  Have you tried any other distros that are using the 2.6.27 kernel?  I have tried Fedora and Mandriva and neither will boot...just like Ubuntu.  I am wondering if it's a kernel issue and/or nvidia issue.  I'm not knowledgeable enough to figure this out on my own though.

---

### Post by plun on 2008-09-26
> **Kosimo said:**
> I don't think that a beta freeze is the reason. I'm experiencing a booting error (so I can't try intrepid) and I was trying to get the latest daily build to see if it has been fixed... But looks like I have to wait

Where is your bug report about your problem with your PC  ?

If everyone just hope that a daily build fixes things "automagic" its
impossible...

---

### Post by Perpetual on 2008-09-26
> **plun said:**
> Where is your bug report about your problem with your PC  ?

If everyone just hope that a daily build fixes things "automagic" its
impossible...

[https://bugs.launchpad.net/ubuntu/+bug/272155](https://bugs.launchpad.net/ubuntu/+bug/272155)

---

### Post by plun on 2008-09-26
> **Perpetual said:**
> [https://bugs.launchpad.net/ubuntu/+bug/272155](https://bugs.launchpad.net/ubuntu/+bug/272155)

Good !

If possible,  is 8.04 OK  ?

> "For anything hardware related, give precise details about your hardware. Attaching the output of "**lspci -vvnn**" and "**dmesg**", after a fresh boot, will help a lot."

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

It is also filed against "Ubuntu" and this is probably a kernel issue
because of Busybox.

---

### Post by Perpetual on 2008-09-26
> **plun said:**
> Good !

If possible,  is 8.04 OK  ?



It is also filed against "Ubuntu" and this is probably a kernel issue
because of Busybox.

Yes, for me, 8.04 boots fine.  I can also boot Fedora 9, Mandriva 2008 and openSuse 11.  For me, it seems anything with the 2.6.27 kernel is a fail.

---

### Post by Kosimo on 2008-09-26
> **plun said:**
> Where is your bug report about your problem with your PC  ?

If everyone just hope that a daily build fixes things "automagic" its
impossible...

Oh really? I though that there is some magic about Ubuntu that fixes everything only thinking about it...  	:roll:

Talks about this bug:  	[http://ubuntuforums.org/showthread.php?t=924202](http://ubuntuforums.org/showthread.php?t=924202)

Bug submitted in launchpad:   [https://bugs.launchpad.net/ubuntu/+bug/272155](https://bugs.launchpad.net/ubuntu/+bug/272155)

---

### Post by Kosimo on 2008-09-26
> **Perpetual said:**
> Kosimo, still no luck getting the live cd to boot?  I am in the same boat as you.  Have you tried any other distros that are using the 2.6.27 kernel?  I have tried Fedora and Mandriva and neither will boot...just like Ubuntu.  I am wondering if it's a kernel issue and/or nvidia issue.  I'm not knowledgeable enough to figure this out on my own though.

Let's talk about it on the previous topic ([http://ubuntuforums.org/showthread.php?p=5860140#post5860140](http://ubuntuforums.org/showthread.php?p=5860140#post5860140)) . And the answer is no still not working :(

---

