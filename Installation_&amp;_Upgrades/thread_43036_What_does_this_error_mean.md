---
title: "What does this error mean?"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by TristanMike on 2005-06-20
Could anyone tell me if this error is important or just what means.  Please try to take it easy on me, I'm a BIG noob to Linux/code

Failed to run /usr/bin/update-manager:
 Child terminated with 231 status

I got it when did 4 udates today, two were Gaim and the other two, not sure of....

Thank You
TristanMike

---

### Post by Xian on 2005-06-20
It's a permissions error message. It is telling you that you do not have the system privileges to perform that operation. There could be several reasons for this, but the most likely is that either you are not set up with the proper system rights, or those rights were not recognized due to a program error.

The best way to determine this is to try and run the commands below and see if it will let you complete the request or feed back to you an error message. Open a terminal and input the following:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

---

