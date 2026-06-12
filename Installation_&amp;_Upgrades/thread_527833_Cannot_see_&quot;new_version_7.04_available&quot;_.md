---
title: "Cannot see &quot;new version 7.04 available&quot; when I start update-manager"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by onetrackmind on 2007-08-17
I'm running 6.10 and I want to upgrade to 7.04. When I open update-manager and click check, I do not see the message "A new version is available" as the webpage says.

Here is the output from the dpkg:

>>dpkg -l update-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  update-manager 0.45.4         GNOME application that manages apt updates

I tried this to see what version I am using:

>>lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy

One additional thing is that when I start update-manager, I get a message saying that it could not connect to all the repositories. But I am able to update some packages when it says I have some updates available, so I am able to connect to some repositeries.

Could anyone help me with this problem?

Thanks,

---

### Post by K.Mandla on 2007-08-17
What repositories are you using -- I mean, geographically speaking? If it's possible, you could change to repositories in another location, and maybe connect for the upgrades you want.

---

