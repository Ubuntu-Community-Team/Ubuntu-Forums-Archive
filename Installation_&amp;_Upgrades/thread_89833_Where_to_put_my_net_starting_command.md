---
title: "Where to put my net starting command?"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by loki99 on 2005-11-13
Hi all!

I'm setting up ubuntu for a friend of mine and we need to run a command as root to get net connectivity.  Where would be a good place to put this command so it gets executed before ntp and all that stuff?

any well informend suggestion would be more than appreciated! :p

---

### Post by GTvulse on 2005-11-13
In an init.d script that executes at S level with a priority between 40 and 60. The default networking script is S40. S41 to S44 are good values because S45 is used to set up NFS mounts and by that time the network interface should be up already. (Copy the script to /etc/init.d, make a symbolic link in /etc/rcS.d). You can read a lot more about how init.d scripts are configured in the rcS.d directory in the [Debian Policy Manual]("http://www.debian.org/doc/debian-policy/"), document that you can install with Synaptic from the Ubuntu repositories or read it online.

---

### Post by loki99 on 2005-11-21
Thanx for the info! :smile:

---

