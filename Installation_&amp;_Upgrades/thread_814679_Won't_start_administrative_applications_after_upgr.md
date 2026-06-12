---
title: "Won't start administrative applications after upgrade"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by kev717 on 2008-05-31
For some reason, I decided to upgrade to hardy heron today.  I installed (took about 4 hours) and then started using it.  I noticed that for some reason I couldn't open up any administrative applications.  They would appear in the bottom task-bar and say "starting administrative application" but then both would close and the program would never start.  I can't even open up my package manager (synaptic).

I am using an HP computer with a 2.5GHz celeron processor, 384MB of ram, and a 40GB hard drive.

Thank-you in advance for your help
-kev

---

### Post by Rallg on 2008-05-31
Boot to recovery mode, log in, then:

sudo apt-get update && sudo apt-get upgrade

that might pull in something you need.

Then, boot normally. Attempt to launch the administrative system information, which has a tab that shows running processes. If it launches, Then try launching some other administrative program.

If the other admin program fails to launch, have a look at which processes are running. This requires some knowledge of processes. I may be that there is a spurious gnome process running (one that should not be running). If you can identify a spurious process, terminate it, then try launching the admin task again.

During beta testing, as I recall, there was an issue like this.

---

### Post by kev717 on 2008-05-31
Sorry... I just found the answer from one of my tech assistants...
sorry to bother you, the URL is: 
[http://ubuntuforums.org/showthread.php?t=247507](http://ubuntuforums.org/showthread.php?t=247507)

Thank-you for you suggestion though.

---

### Post by Rallg on 2008-06-01
Learned something new, myself. Note that the original problem (from your link) was back in late 2006. Perhaps something in recent updates has caused it to re-appear for some users.

---

