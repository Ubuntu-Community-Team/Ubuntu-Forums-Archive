---
title: "Updating one PC from another"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2007-02-01
Here's the situation.  No broadband at home.  Have access to broadband at work.  Thinking about buying a lap top.  If I have Ubuntu installed on the lappy, and Ubuntu installed on the home PC, can I transfer updates and packages from the lappy to the home PC?

I remember seeing posts along this line but can't find 'em this morning, and Google Linux isn't getting me anywhere either.  

Any help much appreciated!

---

### Post by bustanil on 2007-02-01
Copy all your updates/packages from your laptop which is located at **/var/cache/apt/archives** and save them to a directory in your Home PC, then run **dpkg -i *** in that directory. Wow, this is really a "quick and dirty" work. :D

---

