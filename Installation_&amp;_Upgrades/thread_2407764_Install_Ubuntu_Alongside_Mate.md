---
title: "Install Ubuntu Alongside Mate"
date: 2018-12-09
forum: Installation &amp; Upgrades
---

### Post by RedChili on 2018-12-09
Hi!

I'm running Ubuntu Mate 18.04 on my laptop. I would like to switch to the regular Ubuntu instead. So my question is:

Is there a way that I can install the regular Ubuntu alongside Mate, or preferably, to replace Mate while I keep my documents, pictures, and Thunderbird and Mozilla profile folders?

Thanks in advance!

---

### Post by TheFu on 2018-12-09
First, backup anything you can't afford to lose. Documents, personal settings, system settings and the operating system. Sometimes bad choices are made accidentally. Having a backup mitigates that risk. Be certain you can restore the backup.  **aptik** is an easy backup tool for this, but I don't know how well it works on 18.04.

**sudo apt install ubuntu-desktop**   [https://packages.ubuntu.com/xenial/ubuntu-desktop](https://packages.ubuntu.com/xenial/ubuntu-desktop)
but beware that some of the configuration files may be used by both systems and that might be incompatible.  It would be best to create a fresh, new, userid for the new DE.

On the login screen, there is a "gear" which allows selecting the environment to be used at login. Mate, Gnome, Ubuntu, openbox, etc. 

If you like, you can remove the mate-desktop meta-package, but I wouldn't bother. 

I've never added the Ubuntu Desktop package, but I have installed many different GUIs. I always use a newly created userid until I'm positive that the GUI/DE is what I want.

You can copy the documents and both thunderbird and firefox config/data from 1 account to another. Provided the files are placed into the expected locations and permissions are similar, just with the new userid as owner, they will work as before.

---

### Post by RedChili on 2018-12-09
Thanks! That's what I suspected.

I've already made a backup of all important files to an external HDD, so it should be a simple task.

---

### Post by TheFu on 2018-12-09
> **RedChili said:**
> Thanks! That's what I suspected.

I've already made a backup of all important files to an external HDD, so it should be a simple task.

If the external HDD isn't using a Linux file system, it is likely that the correct permissions will be lost.  Unix cares not just about the data inside the files, but the 32-bit permissions + the owner + the group.  These all need to be retained in a proper backup. 

Permissions aren't so important for "documents", but there are many settings where it is absolutely critical.  For example, ~/.ssh/ the directory and everything inside it has exact permissions mandates.

---

### Post by RedChili on 2018-12-09
Thanks, TheFu! It works like a dream. I'm using the same login for both flavors.

---

### Post by TheFu on 2018-12-09
> **RedChili said:**
> Thanks, TheFu! It works like a dream. I'm using the same login for both flavors.

You were lucky.  I've seen settings conflict and break both DE options.

---

