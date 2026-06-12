---
title: "Gutsy updgrade instructions don't work"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by youboontoo on 2007-08-19
Of course, maybe I should not even do it (upgrade to alpha/beta). 

Here are the instructions for "upgrading" to gutsy tribe4:
(from [http://www.ubuntu.com/testing/tribe4](http://www.ubuntu.com/testing/tribe4))

"Upgrading from Feisty

If you upgrade from feisty, please make sure that you have update-manager 0.59.23 
from feisty-proposed installed. Then run "update-manager -d". "

I installed the update-manager version suggested, but when I run "update-manager -d"
I get this response:

"current dist not found in meta-release file"

Any suggestions?

---

### Post by Megaqwerty on 2007-08-19
Have you tried **ALT+F2** and then entering into the box:
```
gksudo "update-manager -c -d"
```
and clicking **Run**?
FYI: The **-c** means "Check if a new distribution release is available" and the **-d** means "Check if upgrading to the latest devel release is possible."

-Megaqwerty

---

### Post by youboontoo on 2007-08-20
Yes. 

It does not matter whether I run "update-manager -c -d" or
"update-manager -d".

The error message is the same.

---

### Post by Megaqwerty on 2007-08-21
This is a bug in the update manager. Ironically it seems to be fixed in gutsy. If you need further help, I will attempt to assist.
[https://bugs.launchpad.net/update-manager/+bug/127263](https://bugs.launchpad.net/update-manager/+bug/127263)

---

### Post by uwflatlander on 2007-09-24
> **youboontoo said:**
> Of course, maybe I should not even do it (upgrade to alpha/beta). 

Here are the instructions for "upgrading" to gutsy tribe4:
(from [http://www.ubuntu.com/testing/tribe4](http://www.ubuntu.com/testing/tribe4))

"Upgrading from Feisty

If you upgrade from feisty, please make sure that you have update-manager 0.59.23 
from feisty-proposed installed. Then run "update-manager -d". "

I installed the update-manager version suggested, but when I run "update-manager -d"
I get this response:

"current dist not found in meta-release file"

Any suggestions?

These steps should fix the meta-release problem. Give them a whirl.

[http://ubuntuforums.org/showthread.php?t=559039](http://ubuntuforums.org/showthread.php?t=559039)

---

