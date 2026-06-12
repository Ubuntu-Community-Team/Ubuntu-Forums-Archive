---
title: "hardy (remix) KDE Login and new users"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by petersk on 2008-05-31
I have had a heck of a time setting up a new user in KDE4 (Hardy Heron remix) 8.04. 
1) I cannot see any "adminstrator button" when I use the "system settings" program in "favorites". 
2) Since "System Settings" is in favorites, I cannot figure out what program it actually is, so I can run it using sudo.
3) I ended up using kuser (after installing it with synaptic) to actually create a new user, but had to jump through hoops to be able to log into that user (that is, I copied the /home directory of the primary user into the new users home directory and then changed the permissions)
4) The new user STILL doesn't show up in the KDE login manager.  I tried changing kmdrc in kde4/kdm, but couldn't find the right option in there.

Can ANYONE help?  I'd LOVE to get the new user to show in the KDE login manager, and I'd like to get the "administrator button" to show up in system settings.

Kurt

---

### Post by petersk on 2008-07-05
kdesudo /usr/lib/kde4/bin/systemsettings

is apparently the "work-around".
Kurt

---

### Post by spooner on 2008-09-19
Cheers Kurt, worked brilliantly.

---

