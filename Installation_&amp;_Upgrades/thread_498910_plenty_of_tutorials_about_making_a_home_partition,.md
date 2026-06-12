---
title: "plenty of tutorials about making a /home partition, but..."
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by fflarex on 2007-07-11
I can't find any that explain how to do a reinstall with an existing /home partition. I've been considering making a separate partition for my user data and files, but I can't imagine it would be worth it if I can't find instructions for how to preserve that data across new reinstalls. Can someone point me in the right direction?

---

### Post by scrooge_74 on 2007-07-11
This should point you on your merry way 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you have a /home partition then is easy to tell the install CD to mount that partition as your /home  Is definetly a good idea to keep /home away from the rest of the system

---

### Post by Vajra Vrtti on 2007-07-12
> how to preserve that data across new reinstalls
In the reinstall you will have to use the manual partitioning option.
Then, just specify the mount point */home* in the appropriate partition.
That's useful to preserve application settings from one installation to other (is that what you want?).
I also prefer to keep my personal data in another isolated partition.

---

### Post by merlinus on 2007-07-12
Also, be sure to NOT format that partition!  There will be a checkbox -- do not tick it.

-merlin

---

