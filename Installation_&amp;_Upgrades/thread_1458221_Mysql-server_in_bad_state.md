---
title: "Mysql-server in bad state"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by yoblin on 2010-04-19
I'm running Lucid, and after one apt-get upgrade I get hangs with the mysql package:

Preparing to replace mysql-server-5.1 5.1.41-3ubuntu11 (using .../mysql-server-5.1_5.1.41-3ubuntu12_i386.deb) ...


no matter what I do I can't get it to remove or install the mysql package. I've tried doing:

sudo dpkg --remove --force-remove-reinstreq mysql-server-5.1

but even that just hangs forever.

I just want to remove the package so I can install the other updates :(

any help?

---

### Post by yoblin on 2010-04-20
This post:

[https://answers.launchpad.net/ubuntu/+question/14619](https://answers.launchpad.net/ubuntu/+question/14619)

combined with killing the "start mysql" command when the package manager freezes helped

--- 

I removed the package with sudo dpkg --force-all -r mysql-server-5.1

and killing the 'stop mysql' command on lockup

---

