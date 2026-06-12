---
title: "administration tools don't work on gutsy"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by gswoods on 2008-02-25
I've had a bunch of trouble with Fedora 8 on this DELL Latitude D520 laptop (can't get wireless to work, suspend doesn't work, VMware runs very slowly, etc.) so I figured I'd give Ubuntu a try (7.10 Feisty).

I've run into some problems that look similar to some reported in previous threads, but the fixes for those did not work for me. The problem is that I can't run many of the administration tools. It just pops up a window that says "The configuration could not be loaded. You are not allowed to access the system configuration".

I have checked that my login is in the admin group. sudo works. dbus is running, and it is already set to start before HAL (S12dbus). Restarting dbus does not help. I have reinstalled all the *dbus* packages , gnome-system-tools, and system-tools-backends. I have rebooted after doing this.

None of this helped, I still have the problem. 

If I run from a terminal, this is what I see:

(network-admin:6375): Liboobs-WARNING **: There was an unknown error communicating with the backends: Process /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl exited with status 127

That's it, nothing else.

I get this same error if I try to run "sudo network-admin" or "gksudo network-admin", or run "sudo su" first and run network-admin from a root shell.

Anybody got any other ideas?

---

### Post by gswoods on 2008-02-25
Sorry I'm brain dead: of course I meant 7.10 Gutsy, not Feisty.

---

### Post by gswoods on 2008-02-26
I tried a complete reinstall, but no luck. I cannot get past this, so I guess I have to give up on Ubuntu for this laptop.

---

### Post by gswoods on 2008-03-12
The problem turned out to be that *perl* was broken. Apparently there is no libperl.so file, so no perl scripts can run. Adding a symlink from libperl.so -> libperl.so.5.8.8 got everything working!

Still it makes me wonder how something so basic could be broken...

---

