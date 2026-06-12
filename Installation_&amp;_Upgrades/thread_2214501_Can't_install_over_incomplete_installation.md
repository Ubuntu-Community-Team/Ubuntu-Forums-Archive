---
title: "Can't install over incomplete installation?"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by frish2 on 2014-04-01
Hello, I am having some problems with installing Ubuntu onto my Windows 7 computer. I downloaded the Ubuntu installation package from the site and commenced my first installation. While downloading some files, the internet cut out and interrupted the process. Now whenever I try to install, Ubuntu detects a previous installation. Whenever it tries to uninstall completely, I get an error message as follows: "Permission denied... For more information, please see the log file: c:/users....<logfile>" 

As it turns out, the cut & paste.txt file size exceeds forum limits. I'm not sure whether or not to post the log files, let me know if they would help.

I can only hope there is somebody who can shine some light on the situation for me.

---

### Post by ajgreeny on 2014-04-01
As you are still at this installation stage I suggest you boot to the live DVD/USB system, start gparted from that and format the partition with the faulty install allready on it to ext4.  Now when you try to install again choose "Something Else" at the partitioning stage and you will see this empty ext4 partition and can point the installer to it.

Personally, I never use the "Install updates" and "Install proprietary codecs" at installation time; I prefer to get the system installed much quicker and then update and add the appropriate "*ubuntu-restrcted-extras" package afterwards.

---

### Post by grahammechanical on 2014-04-01
This is what my eyes notice:

> [COLOR=#000000]please see the log file: c:/users....<logfile>" [/COLOR]

In Linux we do not have drive letters assigned, such as c:/. Is this an install of Ubuntu using Wubi.exe? How are you trying to uninstall?

Regards.

---

### Post by frish2 on 2014-04-01
I haven't managed to install Linux yet, due to this problem I'm having. I tried uninstalling with the uninstall application, but it wasn't able to remove. Then I tried hunting down the bits and pieces in program files and temp and recycling them, but no luck there either. I'm using the wubi.exe to install Linux on my hard drive which currently has Windows 7 installed.

---

### Post by frish2 on 2014-04-01
Unfortunately I am not able to get so far as to choose anything aside from "Uninstall" (the previous, incomplete installation) or "Cancel".
If there were some way of removing all traces of the previous version, would that perhaps help?

---

### Post by ajgreeny on 2014-04-01
I had no idea this was a wubi install, so ignore my comments at post #2.

I do not recommend wubi, and few people on the forum know much about it, unfortunately.

---

