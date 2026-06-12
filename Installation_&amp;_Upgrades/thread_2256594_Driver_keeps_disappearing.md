---
title: "Driver keeps disappearing"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by Yippee38 on 2014-12-13
I'm running Mythbuntu 14.04.  I've got a Ceton InfiniTV card in it, and I'm using it for MythTV.  Generally, it works fine.  However, once in a while, when I get updates to Mythbuntu and have to restart the system, the driver for the card will, apparently, disappear.  I can tell because I try to watch TV through MythTV and I get an error about the tuner card.  I then run "ifconfig -a" and I see the loopback and the NIC, but not the Ceton InfiniTV card.  It normally should show up as a network interface.  At that point, I try "sudo modprobe ctn91xx", but it tells me the ctn91xx does not exist.  At that point, I have to re-install the drivers to get it working again.

You probably guessed by reading this, that I'm not a linux expert.  I don't know much about reading log files and interpreting what I see in them.  I'm sure there is a reasonable explanation for what is going on with this driver, but I have no idea how to troubleshoot it.

Can anybody offer any advice and how to go about figuring out what is going on?

---

### Post by Yippee38 on 2015-02-11
This is driving me crazy.  Can anybody offer any suggestions on what I can look into to fix this problem?

---

