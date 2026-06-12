---
title: "The &quot;Fancy Dragon&quot; Evades Me!"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by Mookawaka on 2006-09-12
I am considering the upgrade to distribution 6.06 of Ubuntu.
Upon attempting to open the update manager I get this error message in the terminal:

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in ?
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 60, in ?
    from DistUpgradeFetcher import DistUpgradeFetcher
  File "/usr/lib/python2.4/site-packages/UpdateManager/DistUpgradeFetcher.py", line 31, in ?
    import GnuPGInterface
EOFError: EOF read where object expected

This could possibly be an arguement for upgrading step by step from the command line, but I am nervous about corrupting my own system which has worked quite well for me this Spring and Summer as 5.10 after some initial stumbling around and banging my face against the keyboard upon first starting out with this operating system.

---

### Post by Mookawaka on 2006-09-16
Does anyone have a translation of these error messages?
Possibly some lines from the terminal that could resolve the issue that could be copied and pasted?
Thank you in advance.

BUMP!

---

### Post by nalmeth on 2006-09-16
What command are you using and getting this output?

What happens when you just like the update-notifier button instead (in the system tray)?

You can update thru the command line with:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Mookawaka on 2006-09-21
When I arrived at this error I was attempting to follow the wiki guide to upgrading to Ubuntu 6.06 -- [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

Thus arriving at the end and using the command:
gksudo "update-manager"

When I use the UPDATE MANAGER button in the system tray, my computer makes some noise like it is processing heavily and then promptly does nothing.  I assume this means that it is cycling through the same error.

I am not sure if these processes are directly related but when the update notifier shows up by the clock to inform me of new software updates I have no difficulties in proceeding in that manner.

---

### Post by Mookawaka on 2006-09-22
Does anyone have insight into why the UPDATE MANAGER is not working for me and spitting out the error from the first post?  I would as much like to learn how to resolve such issues as understand how to work around it.

BUMP!

---

