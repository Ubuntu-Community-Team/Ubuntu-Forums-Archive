---
title: "installer still hangs when more than 15 partitions (now even in 11.10/oneiric)"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-11-06
The past few versions of Ubuntu have an installer bug which results in a hang when there are more than 15 GPT partitions are on the hard drive (I have not tested more than 15 MBR partitions to see if MBR would be different).  This is still the case in 11.10/oneiric.

Yes, I can install by masking the partition table and hiding the partitions it won't be targeting.  Once installed this way, and all the original partitions restored, it boots and runs fine.  That's why I believe it is an installer issue.  The issue is definitely not in Ubuntu when running, nor the kernel, nor udev, nor Slackware's installer, even with all 58 of my partitions visible.

---

### Post by oldfred on 2011-11-06
Have you filed a bug report?

[SIZE=1]**Improving Ubuntu: A Beginners Guide to Filing Bug Reports  **[/SIZE]
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

[https://bugs.launchpad.net/~ubuntu-installer?field.searchtext=&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/~ubuntu-installer?field.searchtext=&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by Skaperen on 2011-11-06
[QUOTE=oldfred;11431918]Have you filed a bug report?

[SIZE=1]**Improving Ubuntu: A Beginners Guide to Filing Bug Reports  **[/SIZE]
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

apport: command not found

How about directions on filing a web site based bug report?  Launchpad doesn't seem to want to do that.

---

### Post by Skaperen on 2011-11-06
> **oldfred said:**
> Have you filed a bug report?

[SIZE=1]**Improving Ubuntu: A Beginners Guide to Filing Bug Reports  **[/SIZE]
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

How about a link to the web page to actually file a report there?  In the past, Launchpad has refused to accept direct bug reports.  You can't file a bug report with apport if apport isn't there.

---

### Post by Skaperen on 2011-11-06
Weird, the web site refused my first reply saying my message was too short, and that I needed to make it at least 1 character.  But it actually posted it anyway.  Now another bug to report.

---

