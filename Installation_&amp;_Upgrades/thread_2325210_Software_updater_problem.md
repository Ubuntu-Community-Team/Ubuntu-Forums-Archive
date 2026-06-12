---
title: "Software updater problem"
date: 2016-05-20
forum: Installation &amp; Upgrades
---

### Post by castromic on 2016-05-20
I recently upgraded to Ubuntu 16.04 from 15.10 using the Software Updater. The upgrade worked well and the software was impressively quick.  Since then after 2 or 3 software updates the Software updater has stopped working and the window just hangs.
I have tried 
sudo apt update

in a terminal window, but the message
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

is returned.

Any suggestions would be appreciated

---

### Post by howefield on 2016-05-20
Generally that means another instance of apt is already running, eg ubuntu software, synaptic package manager.

Close all software updaters and try the terminal again ?

---

### Post by wanderer3 on 2016-05-20
Got this problem tonight on my second laptop (the other one updated a few hours ago). It hangs on software updater when run. I also got the error mentioned when trying to run Synaptic. A reboot and the same thing occurred with the Terminal command sudo apt-get update - it hangs. Bug or server error?

---

### Post by howefield on 2016-05-20
Run top in a terminal and check to see if appstreamcli is running and taking a lot of cpu ?

Ctrl + c to come out of the top program.

---

### Post by wanderer3 on 2016-05-20
> **howefield said:**
> Run top in a terminal and check to see if appstreamcli is running and taking a lot of cpu ?

Ctrl + c to come out of the top program.


No it's not running.

---

### Post by howefield on 2016-05-20
Could be related to this bug which is affecting a few people.

[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845)

Fix is in the works apparently.

---

