---
title: "copying /home from dapper to feisty causes broken system. registry/gconf?"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by zoubidoo on 2007-07-06
I have just upgraded from Dapper to Feisty by fresh install.  I tested the new install, everything works fine.  Then I restored my /home subtree  and the problems begin.  Can't launch terminal window or firefox or any application through gnome.  The machine is only usable from the console.  uids and file permissions look fine.  Is it a gnome registry thing?  How can I check?

Help!

---

### Post by zoubidoo on 2007-07-06
Rebooting just gives me a black screen, X/gnome fails to make it to the login screen.

I replaced /home/ with a fresh install /home and it works fine again.

I think the .gnome/.gconf dirs are to blame - the config is not portable and so that screws things up.  It used to be easy to keep data separate from software with /home in a separate partition.  But if gnome can't handle old config files it all becomes a bit of a mess. :(

---

### Post by dabl on 2007-07-06
Yep.  Your /home directory is where a lot of application-specific configuration information is stored, much of it in hidden files.  I think you have totally confused your new Feisty system :( .

Sorry.

Next time, in your /home directory, make folders for your data like this:

/Docs
/Music
/Images
/Downloads
/Porno

or whatever :D

Then, when you install a new OS, you can let it change /home as it needs to, and it won't touch your data.

:D

---

