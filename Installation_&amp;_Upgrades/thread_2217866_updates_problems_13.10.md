---
title: "updates problems 13.10"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by aliasrafael on 2014-04-18
I have the next message the comand get clean doesn't work
The upgrade needs a total of 58.7 M of free space on disk '/ boot'. Free at least 3,751 k additional disk space on '/ boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by ian-weisser on 2014-04-21
Well, the command is 'apt-get clean', not 'get clean.' Big difference.
Don't forget to use sudo.
And if it "doesn't work" please show us any error messages.

The error message seems pretty clear to me. Your /boot partition is too full.
Are you asking for help with how to clean it out?

---

