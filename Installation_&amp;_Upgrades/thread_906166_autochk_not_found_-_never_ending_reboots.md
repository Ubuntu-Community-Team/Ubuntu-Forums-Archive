---
title: "autochk not found - never ending reboots"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by simonuk on 2008-08-31
Ok,

This is now the second time this has happened while installing Ubuntu so it seems like it is something that must happen to a lot of people. 

Problem: After installing Ubuntu and then trying to access the windows partition it says it can't find autochck.exe, gives you a quick blue screen of death and then reboots. This is never ending. You can't access safe mode and "Best last known config" doesn't work either.

Cause: From what I gather the windows partition suddenly goes hidden.

Solution:
I have seen a lot of solutions and to be honest they all scare me. They involve setting up boot disks (I don't have a floppy drive) or they mess with hex numbers and so on. The windows partition is very important to me so I wanted to go about this a different way. If you can still access the Linux OS then try this:

Open terminal and type in:

```
sudo gparted
```

enter the password

This  will load the gparted programme. 

Now look for the windows partition which will probably be the ntfs filesystem. Most importantly the flag will say "boot hidden". Right click on this partition and choose "Manage Flags". Untick hidden and close down Gparted and restart.

You should now be able to get back into windows.

Simon.

---

