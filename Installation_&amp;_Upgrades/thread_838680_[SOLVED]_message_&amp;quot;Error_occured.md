---
title: "[SOLVED] message &amp;quot;Error occured"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by chicoharv on 2008-06-23
Tried to install new packages on Hardy running in windows.Downloaded 86 new packages and when it tried to install the packages about 2/3 installed, laptop locked up and I get an error message as follows
E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct problem.
E: _cache->open() failed, please report.

went to terminal and tried to do above but I get authentication of password failure
'su authentication failure'
 How do I clear this I am using my root password.

---

### Post by Rocket2DMn on 2008-06-23
run
```
sudo dpkg --configure -a
```
You can't use su because the root account is disabled by default in Ubuntu.

---

### Post by chicoharv on 2008-06-23
:)Thank you that solved that problem and now last 50 installs are starting. How do I thanks and close this thread?

---

### Post by Rocket2DMn on 2008-06-23
There is a link in my signature on how to mark threads as solved.  If you find posts useful, you can thank people by clicking on the blue ribbon in the bottom right corner of a post.

---

