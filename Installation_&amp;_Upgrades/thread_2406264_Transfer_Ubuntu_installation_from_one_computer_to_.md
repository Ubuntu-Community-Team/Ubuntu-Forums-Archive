---
title: "Transfer Ubuntu installation from one computer to another ..."
date: 2018-11-18
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2018-11-18
I read other threads on transferring Ubuntu from one computer to another ...
but in my case, I can't transfer the disk drive holding my current Ubuntu installation.

I have an old Acer 3700 w/ internal drive holding both Windows 10 and Ubuntu 18. I want to move just the Ubuntu over to my new desktop which already has windows 10 loaded.
Ideally I would start up the new computer in windows and then copy over the Ubuntu installation from the Acer and then 'reconfigure'?

---

### Post by oldfred on 2018-11-18
Is old computer BIOS/MBR and new computer UEFI/gpt?
If so you cannot really copy it.

But I normally suggest that it often is easier just to do a new install and restore from your normal backups.

Your /home will have all your use settings. You probably do not want much or anything from /etc as new system may be different.
You also should have a list of installed apps, to make it easy to reinstall them in new system.
Good way to confirm your backups have everything you want or need as you still have old system to go back to, if something is missing.

If both systems are on your network, once Ubuntu is installed you can easily use rsync to copy data from one to the other also.

---

### Post by michael351 on 2018-11-18
Thanks oldfred!

Your suggestion then is to have both systems (old and new) on the same network and install a fresh copy of Ubuntu on the new one.
Once loaded, I can copy over /home from the old system to the new one - correct?

As my old system will be running - what other directories should I copy over to the new one?
The new system is primarily for Kodi and my movie collection (which is stored in my personal cloud).

---

### Post by oldfred on 2018-11-18
What else is on old system?

I do not now Kodi, but is it on old system. Its files may be in / somewhere?
And upgrade of Kodi may be a separate issue?

---

