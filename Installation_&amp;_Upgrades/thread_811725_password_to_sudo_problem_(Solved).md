---
title: "password to sudo problem (Solved)"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by atl_CCk on 2008-05-29
I have posted a problem to the list as the password question was not asked to install software.  I then decided to do the upgrade from the (terminal)CLI interface.  A few answered me for the right or proper command to execute the installs and upgrades from the CLI.  When I did the system failed with a "error in line 20".  After VIing and repairing as stated here;

  Problem turned out to be error in /etc/sudoers file line 20 had a carriage      return(CR). Removed the CR as in root ALL=(
ALL) ALL
to
root ALL=(ALL) ALL
And it worked!

Cleaned up a lot of problems?

I would like to thank the community for helping me isolate the problem and repairing this computer which I have spent a lot of time building into a DB server.

---

