---
title: "APT database corrupted! PLEASE HELP!"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by syntek on 2007-04-11
I'm not sure what went wrong, when, or how, but somehow i messed up my edgy's apt database.

I can run apt-get update successfully, but if I try to run upgrade, install, or remove, apt-get, aptitude, and synaptic all "freeze up"..

For example: If I run # apt-get remove somepackage

I'll get a message like this:

[B][INDENT]0 upgraded, 0 newly installed, 1 to remove and 47 not upgraded.
Need to get 0B of archives.
After unpacking 41.0kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... [/INDENT][/B]

But it will just sit there forever. I've tried running apt-get clean, autoclean, and even moved the .bin files in /var/cache/apt into /root and retried - to no avail..

Basically, aside from updating from the repositories, apt-get freezes, at the last line **"(Reading database ..."**

Any tips on how to fix this or anything else I could try to fix my system so I can do updates and add/remove software from my machine..

I am looking forward to doing a dist-upgrade to Feisty once it's available, but I'll need Apt functioning before even thinking about that!

Any pointers would be greatly appreciated.. Thanx!

---

### Post by heimo on 2007-04-11
You could try to run it prefixed with "strace" and see where it gets stuck. May or may not be helpful. Then you could check if you have a backup of status file.
```
ls -l /var/lib/dpkg/status*
```

See too similar files like this?
```
-rw-r--r-- 1 root root 2205766 2007-04-10 22:19 /var/lib/dpkg/status
-rw-r--r-- 1 root root 2205765 2007-04-10 22:19 /var/lib/dpkg/status-old
```

Try backing up the current status file and then replacing it with status-old. Does it work?

---

### Post by syntek on 2007-04-11
Thanks for the info..

I renamed the status file to status.bad and renamed status-old to status, then ran apt-get update, which looked normal, but gave the following warning/error at the end:

**E: dpkg was interrupted, you must manually run '*dpkg --configure -a*' to correct the problem.** I ran that cmd (which gave no output, just brought me back to the shell) and then did another update, this time it did not show that warning.

so, i decided to see if that all worked and ran an apt-get upgrade..

since i cleared out the cache, it's redownloading a whole bunch of updates, i won't know i i get the problem until after everything is downloaded and it attempts to install an update, or rather, read the database.. so, ill post in the morning if it was a success or not..

thanks again, ill sleep with my fingers crossed.. ;)

---

### Post by heimo on 2007-04-11
I hope it goes well. I just love how debian package management can do miracles and recover even though it can get a bit messed up sometimes. Fingers crossed.   :)

---

