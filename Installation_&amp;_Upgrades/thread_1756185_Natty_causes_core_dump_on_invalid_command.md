---
title: "Natty causes core dump on invalid command"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by nrundle on 2011-05-12
I just upgraded my server from Maverick to Natty and I noticed that now if I type a command that doesn't exist, instead of the usual package search for the command I get a core dump.  I thought I would see if I could get information on the core so I ran /usr/bin/gdb and that core dumps as well.

I have tried removing the package command-not-found but same thing still happens.  Any ideas what could cause a core dump simply when you type a name that doesn't resolve to a file in the path?

-----------------
Update: Found out that after removing command-not-found it still existed in /usr/share  Once I removed the directory entirely non-existent commands no longer cause a core dump.  However, invoking gdb still causes a core dump.  Also, I reinstalled command-not-found and it causes a core dump again on invalid commands.  Perhaps the real culprit is still to be found.

---

