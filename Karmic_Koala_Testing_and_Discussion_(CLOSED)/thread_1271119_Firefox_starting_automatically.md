---
title: "Firefox starting automatically?"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by camper365 on 2009-09-20
It's bizzare, whenever I log in, Firefox starts. I have checked my startup programs and .bashrc for firefox, but I can't find it anywhere. Anyone else having this problem?

---

### Post by kansasnoob on 2009-09-20
The only thing I can think of is something being corrupt in your Firefox profile. I had a problem some time ago where I'd copied my .mozilla folder to a new installation and I'd had Firefox "running" at the time I did it so it would automatically start up.

**NOTE: Firefox must be shut down when playing with the .mozilla folder! AND: if you're at all unsure of what I'm explaining, STOP and request more help!**

What I did to fix it was create a backup of .mozilla (find in Home > View > Show hidden files). *I just right clicked the folder and copied it to my Projects folder with a new name.*

Once I knew it was backed up so I could restore it if my attempt at fixing things failed I sent the .mozilla folder to the trash. Then the next time I started Firefox it created a new .mozilla.

Of course then all of my bookmarks and personalized settings were gone so I went to my backup and copied the places.sqlite profile (that's bookmarks - find in .mozilla > firefox > 8random#.default > places.sqlite) to my new .mozilla which restored my bookmarks. Of course I then had to manually change all of my other personalized settings: font prefs, home page, etc. back to what I had previously.

**Of course if you use Thunderbird mail (I don't) you may not want to do that! I'm not sure where Thunderbird resides but I'd bet in .mozilla!**

---

### Post by camper365 on 2009-09-22
Well, I made a backup of my config, removed the config from .mozilla, and restarted it. I logged out and back in, and it still started.
Apparently, Ubuntu One was trying to get a password from me and started Firefox. I tried to restore the backup, but it wasn't there :( so now I have a Firefox with completely new settings that I need to fix :cry:

---

### Post by kansasnoob on 2009-09-22
That's one of the reasons I go to the trouble of manually creating my own backup of the entire .mozilla. That and I can use that backup to transfer from one machine to another by burning a CD or DVD.

I much prefer that to just doing a ".backup" or something like that.

I've yet to try Ubuntu One.

---

### Post by LKjell on 2009-09-22
See if you have someting in ~/.config/gnome-session

---

