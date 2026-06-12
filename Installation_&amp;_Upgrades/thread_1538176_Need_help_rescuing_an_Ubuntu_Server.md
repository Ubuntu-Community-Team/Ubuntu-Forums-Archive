---
title: "Need help rescuing an Ubuntu Server"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by hotpuppy on 2010-07-24
Problem: Ethernet card not being recognized
 
Issue: I don't know enough about linux to successfully fix this.
 
Solutions Tried: Rescue Install - can get the card working, but it won't stay working when I reboot.
 
Background:
- Running 10.04 with updates current as of a week ago.
- New system, 2GB ram, 1TB HDD, running Intel desktop board.
- Decided to change to a new case for footprint reasons.
- Discovered that motherboard is a mATX and case is MiniITX.
- Changed motherboard to mini-itx. 
- Installed, assembled, and rebooted (same processor)
- Boots fine, but network card not loaded.
- Network card (chipset on board) is seen by lspci
 
chipset is a Realtek rtl8111/8168B (rev3)
 
system appears to be loading the r8169 driver
 
 
Any suggestions?
 
My background is windows and I've been running Debian and Ubuntu for about 6 years, but I'm not a guru (working on it). I'm slowly but surely converting all of our systems to Linux. :)

---

### Post by hotpuppy on 2010-07-24
I resolved this.  
 
I did ifconfig -a (to show all interfaces)
and found that the new card was listed as eth1
 
so I went into /etc/network/interfaces and changed the stanzas (headings) from eth0 to eth1
 
I then rebooted (shutdown -h now -r) because I don't know how to reload the networking cleanly in ubuntu.
 
That resolved the issue.

---

### Post by Iowan on 2010-07-25
[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is how to mark the thread [SOLVED]. ;)

---

