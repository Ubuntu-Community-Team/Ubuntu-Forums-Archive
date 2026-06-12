---
title: "Hard drive space planning for ubuntu 10.04 LTS"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by Shibbir on 2010-10-16
When I install and update software on Ubuntu, what is the location of those installation files. I'm going to install Ubuntu 10.04 LTS with 30 GB and wanna update huge collection of software. Is it enough or I need more space?

My plan is :
boot = 130MB
swap = 4096 MB
/ = 26000MB

Should I need separation of root(/). Like: /user, /tmp etc. If, then which media needs more space?? OR what should be the best choice?

---

### Post by lemming465 on 2010-10-17
If you are upgrading an existing install, the packages will be staged in /var/cache/apt, so /var needs about as much free space as your total amount of installed software on /usr.  If /usr has 8 GB of stuff on it, /var probably needs about 10 GB of free space for an upgrade.

You can do lots of different disk layouts, depending on your goals.  Your proposed layout looks fine.  I've done everything from a single root partition at home to 13 partitions on some work machines.

---

