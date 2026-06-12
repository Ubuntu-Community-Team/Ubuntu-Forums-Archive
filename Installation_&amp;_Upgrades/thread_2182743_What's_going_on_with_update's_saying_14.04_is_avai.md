---
title: "What's going on with update's saying 14.04 is available"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by david98 on 2013-10-22
I just opened the terminal typed sudo update-manager -d started downloading updates then this popped up in the software updater what's going on this cannot be right.
a would appreciate any advice [ATTACH=CONFIG]247151[/ATTACH]

---

### Post by michaelcranie on 2013-10-22
Why did you type this it tells update manager to upgrade to the latest version even if it is a development release.

---

### Post by coffeecat on 2013-10-22
> **david98 said:**
> 
a would appreciate any advice 

You might find a read of man update-manager useful. :wink:

michaelcranie is right - With the -d option you were telling update-manager to check if it's possible to upgrade to a development version. The 14.04 repositories are now open for developers and testers to use and that is why you are getting that message.

From man update-manager:

>  -d, --devel-release
              Check if upgrading to the latest devel release is possible


---

