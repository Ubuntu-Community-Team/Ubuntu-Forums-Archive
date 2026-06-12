---
title: "Partial Upgrade Help, yes I did read the sticky"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Drood on 2009-10-20
Hi, while updating 9.10 beta my computer crashed and now when I try to upgrade via the Update Manager I get the aforementioned message. When the computer crashed and booted back up my gnome was messed up and once I booted into Ubuntu and ran the update again It prompted me to enter a command in the terminal, I did. (I do not remember the actual command, but the explanation the message gave me was I needed to upgrade via that way because the original update was interrupted). Anyways, now I am being offered a partial upgrade, I do not know if it is related to that upgrade that did not go so well. 

The sticky says usually the partial upgrades goes away within hours but I have been offered it for about 3 days now, should I just wait or go ahead with it. I do not have enough knowledge about Ubuntu or the packages to determine whether or not to install them.

Edit : Gnome is working now, it is not the issue. I am just unsure whether or not to partial upgrade.

---

### Post by paul_in_london on 2009-10-20
Try running these commands:

```
sudo cp /var/lib/dpkg/status.old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available.old /var/lib/dpkg/available
sudo rm -vf /var/lib/apt/lists/*
sudo rm -vf /var/cache/apt/*.bin
sudo aptitude update
sudo aptitude safe-upgrade
```

The 3rd command will refer to a directory called partial. You can ignore that because the directory doesn't need to be removed.

The last command (safe-upgrade) may complain about dependencies that can't be resolved. If it does, try running:

```
sudo aptitude update
sudo aptitude full-upgrade
```

If the full-upgrade wants to remove anything and you're unsure, don't run it and post your output here first.

---

### Post by VMC on 2009-10-20
> **Drood said:**
> ...
The sticky says usually the partial upgrades goes away within hours but I have been offered it for about 3 days now, should I just wait or go ahead with it. I do not have enough knowledge about Ubuntu or the packages to determine whether or not to install them.

What's the name of the package it's offering to upgrade?

---

### Post by Drood on 2009-10-20
Hmm, not really sure. It doesn't specify whether its a new package or upgrade or removal for that matter, if it appears on the list but is not checked, does that mean removal ? There's a lot of them 141MB.

---

### Post by Drood on 2009-10-20
When I click on them and read the descriptions they do say specifically if they are removing packages.

---

### Post by slakkie on 2009-10-21
Could you do this:
```

sudo aptitude update 
sudo aptitude -s safe-upgrade

```

This will simulate the safe-upgrade, without affecting your system. Could you post the output of the safe-upgrade command? 

See this thread as well, [http://ubuntuforums.org/showthread.php?t=1287523](http://ubuntuforums.org/showthread.php?t=1287523)

---

### Post by 2blue on 2009-10-21
I also have done all the updates and partial upgrade. I was told that this close to the release of the final Karmic Koala release it was safe, now I am beginning to wonder. 

Will this be a disaster or will things sort out its self with further upgrades?

---

### Post by slakkie on 2009-10-21
Not sure, don't know which packages got removed..

---

### Post by neontrailer on 2009-10-21
Ive got 9.10-64bit on a separate drive just in case, I start it up every 2-3 days to see whats new. Today it hit me for a partial upgrade everything went fine until it rebooted and froze with no icons in the top panel for date and shut down. So I was forced into a hard reboot and it came back up normal and everything was fine!   Strange?

---

### Post by 2blue on 2009-10-21
Yes a bit unusual neontrailer. 

After a rather large update or upgrade, I cannot remember, the Ubuntu vignette (the startup taadaa-sound) got very jerky, and strange, now it has been like that for the last few start-ups. Any ideas what it might be? 

I might have to do a full install of the final release if strange things don't work out by them selves.

---

### Post by psyke83 on 2009-10-21
> **2blue said:**
> Yes a bit unusual neontrailer. 

After a rather large update or upgrade, I cannot remember, the Ubuntu vignette (the startup taadaa-sound) got very jerky, and strange, now it has been like that for the last few start-ups. Any ideas what it might be? 

I might have to do a full install of the final release if strange things don't work out by them selves.

I'm pretty sure that's a PulseAudio problem, most people are experiencing it, and re-installing won't solve it.

I'm not aware if a bug is filed yet.

---

