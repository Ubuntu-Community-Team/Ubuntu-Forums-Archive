---
title: "reinstall firefox / remove personalisations"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by aixroot on 2010-08-18
I have personalized Firefox to much. 

I would like a new clean version.

I tried to remove 
sudo apt-get remove
and with auto-remove
and with purge

I tried it with synaptic, I tried it with the Ubuntu software centre.

Every time I got my same personal settings back. Same plug-ins, same tabs, same same same. 

How do I do get a new clean Firefox to re-personalize later?

---

### Post by sydbat on 2010-08-18
> **aixroot said:**
> I have personalized Firefox to much. 

I would like a new clean version.

I tried to remove 
sudo apt-get remove
and with auto-remove
and with purge

I tried it with synaptic, I tried it with the Ubuntu software centre.

Every time I got my same personal settings back. Same plug-ins, same tabs, same same same. 

How do I do get a new clean Firefox to re-personalize later?You should close Firefox first. 

In your 'Home' folder there are hidden folders (starting with a '.'). To see them, go to 'View' and select 'Show Hidden Files'. 

Then find the '.mozilla' folder, go into it, open the 'Firefox' folder and you will see the default profile (it will be named something like 'jashdgxxx.default'). Do not delete yet (just in case). Rename the profile to something like 'jashdgxxx.default.old'.

Then restart FF and it will create a new 'default' profile folder that will have no profile info or add-ons or anything.

---

### Post by aixroot on 2010-08-18
thanks 4 your quick reply.

Weird though, that after a reinstall and purge Firefox uses previous config files

---

### Post by lovinglinux on 2010-08-19
> **aixroot said:**
> thanks 4 your quick reply.

Weird though, that after a reinstall and purge Firefox uses previous config files

That's normal behavior. You can install, uinstall or update Firefox and your personal data will be kept. The purge command does remove user config files (ie at /home) of any programs, it removes system config files.

BTW, I would recommend that you learn how to use the profile manager, instead of deleting or renaming profile folders. See these:

[http://firefox-tutorials.blogspot.com/2010/05/profiles.html](http://firefox-tutorials.blogspot.com/2010/05/profiles.html)
[http://firefox-tutorials.blogspot.com/2010/05/backups.html](http://firefox-tutorials.blogspot.com/2010/05/backups.html)
[http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

