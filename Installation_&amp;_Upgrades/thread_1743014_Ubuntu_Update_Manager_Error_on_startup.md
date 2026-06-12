---
title: "Ubuntu Update Manager Error on startup"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Jaymus on 2011-04-29
I have been trying to use the ubuntu update managerto install java on my computer, but every time i try to start the update manager, i get these errors all in a row:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

My internet connection is obviously stable or I wouldn't have been able to post this.  I can only tell from the error message is that is failing to retrieve the package list.  Do i need to launch with superuser permissions somehow?

---

### Post by kukker32 on 2011-04-29
you use** update manager** to **install java **? you  sure you don't mean synaptics packets managger ? or ubuntu software center ??

you could maybe download java from java.com and install it manually??

also what is the user permissions of

/etc/apt/sources.list ?

---

### Post by dino99 on 2011-04-29
as numerous ubuntu afficionados are installing/upgrading thier system(s), the servers are too busy right now, so better to wait a few days

---

### Post by Jaymus on 2011-04-29
Also getting this after reboot:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' message and include the following error message:
malformed line 61 in source list /etc/apt/sources.list (dist parse)

---

### Post by dino99 on 2011-04-29
> **Jaymus said:**
> Also getting this after reboot:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' message and include the following error message:
malformed line 61 in source list /etc/apt/sources.list (dist parse)

output of:
sudo gedit /etc/apt/sources.list

---

### Post by Jaymus on 2011-04-29
Have tried manual installation from java.com.... it doesn't work, and have tried running installation through command prompt, but at the end it attempts to openthe update manager to complete installation, which fails.

---

### Post by Jaymus on 2011-04-29
I have discovered  the problem.  It seems that one source added in there had a typo when i added it, and was at the specified line 61.  Ill delete the source and try again...

---

### Post by Jaymus on 2011-04-29
I have it running now.  I didnt know where to look thank you for the help.

---

### Post by dino99 on 2011-04-29
then set this thread as "SOLVED" using the thread tools on top thread

---

