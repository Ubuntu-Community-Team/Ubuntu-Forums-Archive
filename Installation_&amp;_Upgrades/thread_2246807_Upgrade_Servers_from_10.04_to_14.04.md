---
title: "Upgrade Servers from 10.04 to 14.04"
date: 2014-10-03
forum: Installation &amp; Upgrades
---

### Post by matthew54 on 2014-10-03
Hi, I'm new at the systems admin thing and need to upgrade my university's servers from 10.04 to 14.04. My boss wants me to start researching on how to go about this but I can't find a ton of info on it. I would love to know that steps I should take to upgrade these 19 servers without losing data, having very little downtime, and keeping all of our software working correctly. Should I upgrade to 12.04 first? We have begun using Ansible for automation so it would be nice to have some guidance through this process or where else to research.

---

### Post by ian-weisser on 2014-10-03
Well, I would recommend using a test system. Migrations like this can have quite unexpected problems.
VMs are great for this kind of testing. I would replicate a sample 10.04 install (with data) in a VM.

You have two migration paths to test:
Update 10.04 --> 12.04 --> 14.04
Fresh install of 14.04. The installer will try to maintain the existing data in /home.

Opinions around here vary. Some people swear by fresh installs. Others swear by updates. It won't take you long to test both options and discover which one _you_ prefer...since you'll be the one troubleshooting and maintaining it.

A big variable is which applications you want to keep, and how they have changed in four years.

---

