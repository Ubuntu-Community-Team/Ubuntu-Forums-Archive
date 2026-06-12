---
title: "Ubuntu Upgrade Mirror selection"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by kai4785 on 2010-08-17
I've been working on doing local mirroring of linux distributions I own, mostly because I've got more storage than I need, and it's a fun challenge.

So, I've got a local 9.04, 9.10, 10.04, and 10.10 mirror that is working great. I can point my sources.list file at my mirror and do updates, and I can run network installs from my mirror as well.

I've had it running long enough to have a laptop that I want to update from 9.04 to 10.04 (for my mommy so she can see all the cool HTML5 stuff I put on our family website.) Update Manager sees an upgrade path to 9.10, but I can't get it to use my local mirror to download the data. So instead of getting LAN speeds at 10Mb/s, I'm using my internet speeds at ~800Kb/s. 

How can I pick an "upgrade mirror" so to speak? /etc/apt/sources.list gets basically commented out during the process :(

---

### Post by uRock on 2010-08-17
It probably has something to do with the system going only to ubuntu's secure mirrors to prevent you from going to a hacked server. There may still be a way around this.

---

