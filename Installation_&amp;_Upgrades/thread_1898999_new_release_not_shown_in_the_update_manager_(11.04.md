---
title: "new release not shown in the update manager (11.04)"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by 3pckz on 2011-12-22
Hi guys

I'm sort of a newbie to Ubuntu, been using the natty narval. I've wanted to upgrade when the notification came up, but during the download the internet connection just died. 

Now, the update manager doesn't show the new release... 

I've already tried the Alt+F2 and typing update-manage -d

Please help...

---

### Post by zvacet on 2011-12-27
What is output of 

```
lsb_release -a
```

---

### Post by sammcneill on 2012-01-07
I am having the same problem. Here is the output from my version check:



> sam@Ubuntu:~$ date
Sun Jan  8 11:22:22 NZDT 2012
sam@Ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

When I run the update manager it says I'm fully uptodate.

Any assistance appreciated

---

