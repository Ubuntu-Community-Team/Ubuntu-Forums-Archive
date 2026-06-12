---
title: "Mythbuntu system hangs after regualr system update: &quot;out of memory&quot; errors"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by mcc1975 on 2010-08-04
Dear forum members

I have Mythbuntu 10.04 installed on an exclusive HTPC and working great... until tonight. After letting the system update some packages (161 packages if I remember right), I suddenly have an issue where the graphical system won't start. After researching I found three error messages that might be causing that.

1. At the start of splash screen I see "UUID=xxxxxxxCD7 not ready yet or not present" I checked in /etc/fstab and found that this is the swap partition. I don't remember seeing this before so this could be the culprit.

2. I'm not at the computer in question right now but I saw a Plymouth error about "mountall" and then the message "plymouth command failed". Not sure if this could be the main error.

3. after a while (usually ca. 1-2 min) I receive thousands of errors of the kind "out of memory"... "kill process XXXX" (process vary wildly e.g. dbus-daemon, mysql, etc)... "process killed"..."respawning"

After error 3, I'm not able to switch to graphical console (ctrl-alt-F7). If I was in the graphical console at this moment, I simply can't switch to the CLI console.

I'm always afraid of updating my system since I've seen lots of things breaking afterwards (usually the proprietary graphic drivers) but this is really strange. I spent huge amounts of time setting up this system so any help is greatly appreciated.

Thanks.

Best regards
Marcio

---

### Post by mcc1975 on 2010-08-05
Dear forum members

I did some investigation and solved the swap partition not being mounted. This gave me a few more minutes to play before the system becomes unresponsive. Playing with top and free -m, I found that some application must be suffering from a memory leak. After trying different things, I now found out it is an application called "Default". It only lives for a second before crashing an opening a new instance. What I get is something like:

PID          User   PR    Virt           RES   SHR                
31XXX   root        20       1920  720       476         0:00.0 Default

There are literally hundred of those being created at any given time.

After killing all this "Default" applications, I can finally see my desktop. Does anyone know what causes this and how to address the issue?

Thanks in advance for any help.

Cheers

---

