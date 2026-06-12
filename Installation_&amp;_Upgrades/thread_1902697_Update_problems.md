---
title: "Update problems"
date: 2011-12-31
forum: Installation &amp; Upgrades
---

### Post by Davis Bre on 2011-12-31
The problems started when I've had installed Java, what you can see in this post: [http://ubuntuforums.org/showthread.php?t=1900837&page=2](http://ubuntuforums.org/showthread.php?t=1900837&page=2)  . This problem has been solved, but after solving this problem, I got an update problem:
davis@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I would be grateful, if someone would tell how can I solve it or reinstall Ubuntu 11.10, which is in dual boot with Windows 7. 

Davis

---

### Post by BC59 on 2011-12-31
First check if you have open another application like Synaptic or a Terminal.

---

### Post by spacecheck on 2011-12-31
> **Davis Bre said:**
> The problems started when I've had installed Java, what you can see in this post: [http://ubuntuforums.org/showthread.php?t=1900837&page=2](http://ubuntuforums.org/showthread.php?t=1900837&page=2)  . This problem has been solved, but after solving this problem, I got an update problem:
davis@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I would be grateful, if someone would tell how can I solve it or reinstall Ubuntu 11.10, which is in dual boot with Windows 7. 

Davis
You could try adding "sudo" before the command, and then entering your password...

---

