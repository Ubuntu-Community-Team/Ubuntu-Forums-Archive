---
title: "Can't update and install applications on Ubuntu 9.10 desktop"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by emreesen on 2010-03-28
Hi I am Emre and proud to be an Ubuntu user.
My problem is I can't update my Ubuntu 9.10 Desktop OS.
On software sources screen I can choose any mirror but after that reloading repositories will fail all the time.
A few days ago constantly there is a red error screen at system tray but after installing "ubuntu tweak" it's gone.
The red error sign says it cant update the system there is a broken link on repository list try to filter "broken" on update manager.
Sorry about cant give you the exact error text because now it doesn't show up.
But still I can't update my system and can't install application.
Thanks in advance.
Any help will be gratefully appreciated.

---

### Post by pastalavista on 2010-03-28
Look in /etc/apt and see if you have a back-up of 'sources.list'. If you do, rename it to 'sources.list.old' or whatever and change the backup file to 'sources.list' and then run apt-get update again.

You need to be root to do this so the easiest way is with a root file manager so run with Alt-F2 'gksu nautilus'

---

### Post by emreesen on 2010-03-30
> **pastalavista said:**
> Look in /etc/apt and see if you have a back-up of 'sources.list'. If you do, rename it to 'sources.list.old' or whatever and change the backup file to 'sources.list' and then run apt-get update again.

You need to be root to do this so the easiest way is with a root file manager so run with Alt-F2 'gksu nautilus'



Thank you for your response but that didn't solve my problem.
I reinstalled my system with a clean install after backup.
But out of the box ubuntu can't update itself and can't install software.
The error text is:
"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

How can I fix this ?
Thanks in advance.

---

