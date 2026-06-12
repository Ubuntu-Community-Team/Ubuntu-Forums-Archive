---
title: "Error when installing build essentials"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by arun-3 on 2014-09-25
I have tried to install build essentials. Got this error message in terminal command can you please suggest an solution .Since i want to install open CV

 sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
developer@developer-System-Product-Name:~$ sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Best Regards,

---

### Post by ian-weisser on 2014-09-25
It means another application that uses the package manager is already running.
You can only use one at a time.
The system enforces one-at-a-time using a lockfile.
apt-get cannot access the lockfile because another application is still using it.

There is the very slight possibility of a system problem - a crashed application that failed to release the lockfile.
However, it's very, very rare. Much more likely you have another application running.
Rule out the most common reason first.

---

