---
title: "Software Updater exits without updating"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by conor9 on 2016-02-05
Hi

Usually, the software updater prompts me every few days or so with updates and runs without problem.

The last time it ran, I selected the "remind me later option" 

It didn't remind me, but I didn't think any further on it.

Today, I ran the updater from the (unity?) taskbar.
it checked for updates and listed the updates available for installation.

I press "install now". It displays the "installing software" dialog but then exits without prompting for the password and without performing the installations  (in this case updates to JDK and Ubuntu Base)

I have removed the package lists at /var/lib/apt/lists  (and /partial)
I have run   sudo apt-get update
I have even purgedm removed and re-installed the update-manager but still to no avail.

apt-get must be working - it let me uninstall and reinstall the software updater

Any help would be appreciated

Thanks!

---

### Post by grahammechanical on 2016-02-05
> I selected the "remind me later option"

That will depend upon how often Update Manager is set to check for updates. If Updater Manager is set to check for updates daily, then "remind me later" will mean when next it checks for updates. Which would be the next day. In a sense the option = cancel.

Regards

---

### Post by conor9 on 2016-02-05
that makes some sense, i guess, but if I manually start the update then shouldn't it run the update and not decide if it should complete it or not.

---

### Post by conor9 on 2016-02-06
bump

---

### Post by howefield on 2016-02-06
Try updating from the command line, as you might get some clue as to what is wrong, if anything at all.

> sudo apt-get update
> sudo apt-get upgrade

Post back the results.

---

