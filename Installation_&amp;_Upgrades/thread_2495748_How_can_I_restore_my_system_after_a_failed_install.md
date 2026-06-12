---
title: "How can I restore my system after a failed install of held-back packages?"
date: 2024-02-29
forum: Installation &amp; Upgrades
---

### Post by nim2 on 2024-02-29
Hey,

I just installed a few held back packages (all were mesa:386  dependent). However, afterwards, tons of system and application packages  have been removed.

 There is no x-server anymore, and no WM, no dolphin, QT etc. OS is Ubuntu 22.04 jammy with kernel x86_64 Linux 6.5.0-21-generic.


 I haven't rebooted yet (and I don't think it will boot anyway). Is  there a way to rescue my system? Or do I need to backup /home and stuff  and start over?


 According to the apt log, when installing the mesa packages, another  package (policykit-1-gnome:amd64 (0.105-7ubuntu3, automatic)) have been  installed as well, I guess that was what broke my system.


 Would it be somehow possible to re-install all removed packages? Any help is appreciated!

---

### Post by TheFu on 2024-02-29
All things are possible, but based on the description, you'll need to be better than me to fix everything.
My backups allow nearly complete recovery in about 45 minutes. You've probably already wasted at least that much time already.

I'd ensure my backups were good, then start over.

Also, don't try to force 32-bit code onto Ubuntu Linux that isn't pulled in automatically by dependencies.  If you want a 32-bit OS, Debian probably still has one for a few more years. I know they are discussing ending 32-bit library and program support inside the Debian project.

If you have a list of the removed packages and there aren't other packages which conflict, you could feed that list into apt-get to be installed.

But you have to ask, is this really worth your time if it only takes 45 minutes to have a clean system?  My answer would be NO, not worth it for a maybe solution when I have a guaranteed method to be productive again in less than an hour.

It's your call.

---

### Post by ajgreeny on 2024-02-29
I'm tempted to ask why you "forced" the installation of those held back packages; they are usually held back for a very good reason, ie, something nasty has already been discovered to go wrong when installed by another user somewhere. That is why we have these phased updates and quite often see held back packages when using terminal to update and upgrade.

However, having got to this state I agree totally with TheFu and recommend a clean install over your existing system. Backup all your personal files currently in your home and then start again and restore your personal files.

And in future please don't force those held back packages!

---

