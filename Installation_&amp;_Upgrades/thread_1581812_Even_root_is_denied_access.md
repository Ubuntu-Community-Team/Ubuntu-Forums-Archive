---
title: "Even root is denied access"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by miserly-martyred on 2010-09-25
I have been trying to run the following commands several times in the last couple weeks, to no avail.

"su" to get to root...then while root "apt-get update" for updates

also

"sudo apt-get update"

BOTH are denied even with root or user-admin pwd.

States that either permission is denied and/or frequently states that the command "apt-get" does not exist.

...very confusing to me

---

### Post by aysiu on 2010-09-25
If the command *apt-get* doesn't exist, then you must have uninstalled (accidentally) something really important. I'm not sure how to get that back.

---

### Post by miserly-martyred on 2010-09-25
oh d*mn, that's kinda what I was thinking 

I also just noticed that it said this:

sh: dpkg  Permission Denied.


As you pointed out though, I don't really know what I would have installed/uninstalled that would do that.

I havent even touched system installation/program-related items.

Just random networking/media items, ughhh

---

### Post by miserly-martyred on 2010-09-25
another important note is that I WAS able to install updates just fine for a while.  However, as an ongoing issue, my pc HAS been having issues being totally denied function because of "inability to fork child process" this sometimes comes into play with the update manager.  I dunno, I get the feeling google chrome is frying everything b/c fewer issues happen when it is never run, but it's still sporadic

---

### Post by aysiu on 2010-09-25
Update Manager, *dpkg*, and *apt-get* are all linked processes.

---

