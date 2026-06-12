---
title: "upgrade problems"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by koulanji on 2007-10-18
I'm trying to upgrade and I get this lovely error

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport. 

Any idea why?

---

### Post by por100pre1 on 2007-10-18
Download the Gutsy CD and try a fresh install, backup your whole user folder before proceeding. Please help the community [filing a bug]("https://bugs.launchpad.net/bugs/+filebug/") against update -manager, be sure to provide the results of these commands:

```
cat /var/log/dist-upgrade/apt.log
```

```
cat /var/log/dist-upgrade/main.log
```

```
cat /var/log/dist-upgrade/main_pre_req.log
```

```
cat /var/log/dist-upgrade/term.log
```

If you decide to do so, please do it before the fresh install.

---

### Post by koulanji on 2007-10-18
sorry, that does not help at all. NTFS is shady on this system too. My usb keys work on and off I can't back up anything. Is there any other way that I can upgrade?

---

### Post by Sef on 2007-10-18
> NTFS is shady on this system too.

What do you use as your file system for Ubuntu?

> My usb keys work on and off I can't back up anything. Is there any other way that I can upgrade?

Try using a Live CD to access your files and back them up to the usb keys.

---

### Post by Ghostlove on 2007-10-18
> **koulanji said:**
> I'm trying to upgrade and I get this lovely error

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport. 

Any idea why?

I am having exactly the same problem. I am currently downloading Gutsy to make a fresh install and see if that helps.

Don't forget to backup! :)

---

### Post by koulanji on 2007-10-18
Ok, I cannot back up anything for a fresh install. Why does everybody keep recommending that. Not to mention I've tried the new Gusty on my laptop and it is just broke *** as hell. I can't upgrade on my desktop and I can't install programs on my laptop. How broken *** can one get. Now is there any other way I can upgrade?

---

### Post by blueeyesmike on 2007-10-18
I had a similar problem, I just changed my server in administration>>software sources and I'm downloading now

---

### Post by koulanji on 2007-10-18
What server did you choose? Because right now all the servers in the repo are dead. This is just really incredibly dandy. I'm done.... I'll wait till next week to upgrade this piece of ****

---

