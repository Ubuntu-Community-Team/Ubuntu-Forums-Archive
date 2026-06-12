---
title: "upgrade kernel?"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by deanhiller on 2009-11-22
I have one machine on 2.6.28-16-server and another that I would like to upgrade to the same but right now is 2.6.24-23-server.  I tried copying over the sources.list file so it would use the new repositories but "apt-cache search linux-image" has different results on both machines...not sure why it is not using the new jaunty repositories once I copy over the sources.list file.  I think copy over the whole apt directory and it still doesn't work.  I still don't see those images(the new 2.6.28-16), in fact, I don't see a list of any images except the installed image.  How do I fix this?

thanks,
Dean

---

### Post by zvacet on 2009-11-23
Do you have any specific reason not to upgrade from Intrepid to Jaunty on that machine?If not just upgrade to Jaunty and you will get linux-image you are looking for.

---

### Post by snowpine on 2009-11-23
Hi Dean, editing "sources.list" is not sufficient to upgrade from one Ubuntu release (Intrepid) to another (Jaunty). Further action is necessary to complete the upgrade.

Here are detailed instructions: [https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

---

