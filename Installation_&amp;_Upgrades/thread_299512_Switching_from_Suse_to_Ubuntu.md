---
title: "Switching from Suse to Ubuntu"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by taddy_porter on 2006-11-14
I currently have a Suse 10.1.5 system. I got caught in some package management messes and have now gotten my gnome desktop screwey. KDE is alright, although I have some crashes, etc.

I plan on just formating the / partition and installing Ubuntu. I used Ubuntu back in the Hoary days and liked it better than Suse. I have my /home on a seperate HDD. I plan on keeping my /home.

My question is, since I have some Gnome issues, if I install Ubuntu will I keep my gnome problems (mainly I get errors when I trying to load themes from the control center). I don't want to loose my KDE settings or my data on /home. I don't really care about my gnome settings though. I had been using KDE exclusively and just recently tried out Gnome and liked it.

---

### Post by bernied on 2006-11-14
I suggest that backups are your answer. Install your shiny new ubuntu, then before you try to use your old home (ie don't mount that other hard drive), take a copy of the home that ubuntu makes for you (maybe read up on the 'tar' command). In fact, you could just mount your other hard drive over the top of the ubuntu /home directory.

You need to be aware however that user and group ids are not stored with files as names, rather as numbers, so if you switch between distros, you will probably find that user and group ids are very different (because different distros use different numbering systems). Better to use entirely different partitions for different distros, and copy what you want from the old onto the new (as your new user - that way the permissions get set right).

---

### Post by Azriphale on 2006-11-14
Another thing, all user setting are stored in the user's home directory. For instance, gnome settings are all in /home/bob/.gnome2 (assuming a username of "bob"). If you find that your gnome session is still broken, try moving the directory ".gnome2" to another location, or renaming it, whatever. Do something like this in the command line:
```

$ mv .gnome2 dot_gnome2

```

Perhaps do the same to the directory ".gnome".

When you next log in to a gnome session, it should recreate that directory with the default settings.

---

