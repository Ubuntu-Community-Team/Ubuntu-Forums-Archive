---
title: "How to backup certain settings"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by nch0930 on 2010-03-14
I reinstall my system very frecuently, and I was wondering if there is a file where some gnome settings are stored, so I can just backup it, and have all my settings like they were before reinstalling.

-Icons on the top panel.
-Keyboard Shortcuts
-Power Management
-Sound 
-Keyboard Layout settings.

I know I could have /home on another partition, but I'd rather backup only the settings I mentioned above, and have the rest of my /home cleaned.

Also, Is there a way to setup SCIM as the default IME using a command?

Thanks, I'm using Karmic Koala.

---

### Post by YannBuntu on 2010-03-17
If you reinstall frequently for tests, you should do it in VirtualBox.

look into the hidden files your /home, you should see folders of known applications (.mozilla for Firefox , etc.) 

Try to save&restore just the following:
.config
.fonts
.gconf
.gnome
.gnome2
.gnome2_private
.nautilus
.scim

etc..

---

