---
title: "No TTY consoles after upgrade"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by Shdwdrgn on 2007-05-03
I have a system that was passed to me with Dapper on it, and I decided to take it up to Feisty this week.  Since update-manager would not show a possible dist-upgrade, I took the other path of changing occurances in sources.list from dapper to edgy, performed an apt-get update/dist-upgrade, then rebooted the system.  

All seemed well at this point, so I checked update-manager again for the availability of a dist-upgrade, but still did not get the notice.  So I followed the same path, editing sources.list and changing edgy to feisty.  After the upgrade, I again rebooted the system.  This is where I first noticed trouble...

Currently, when I boot up the system, everything appears normal (I get the ubuntu splash screen and the system comes up in the GUI login), however if I switch back to tty1 I see an error about no devices listed in the mdadm conf file (which is fine, I'm not using RAID on this system), and the cursor is flashing on the next line.  There is no login prompt on any console (1-6), and hitting keys doesn't do anything.  I CAN get to a terminal in X once I log in.  Tried 'init q' to see if it would reinitialize the consoles, but nothing happened.  Have also just performed a "dpkg-reinstall --all" which reconfigured a lot of items, including setting up inittab for consoles 1-6, but again after a reboot, there is no login prompt.

At this point, the easy thing would be to just reinstall a clean Feisty and be done with it, but what would I learn from that?  What I really want to know is, how do I figure out what is getting hung up in the init scripts, how do I try to force inittab to launch the consoles, and how do I resolve this issue.  I want to more fully understand what's going on, in case some day I find a similar problem on a critical machine.  Any help or hints towards troubleshooting are greatly appreciated!

---

### Post by Shdwdrgn on 2007-05-03
Solution to this issue has been found.  Appears there is a bug on it already, I just didn't use the right search terms.

Related bug is at [https://launchpad.net/ubuntu/+bug/95210](https://launchpad.net/ubuntu/+bug/95210)
Solution is to edit the /etc/event.d/tty[1-6] files and remove to extra repeated code on the last line.

---

