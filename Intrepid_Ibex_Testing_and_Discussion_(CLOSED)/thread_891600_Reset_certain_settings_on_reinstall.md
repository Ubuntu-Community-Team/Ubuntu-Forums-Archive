---
title: "Reset certain settings on reinstall"
date: 2008-08-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MALEADt on 2008-08-16
Hi all,

Having set-up Ubuntu to have it's /home directory on a separate partition, a reinstallation has certain nasty consequences. Some examples:
[list]
[*] File associations remain intact, even if the application does not exist / is not installed yet;
[*] Menu entries are preserver too, even if the application does not exist / is not installed yet.
[/list]
Now I have a defunct "gThumb" entry in Gnome's menu, and .mkv files are being opened with the unavailable "gnome-mplayer".

Wouldn't it be better if certain settings (like file associations, and menu entries) got reset (or at least verified) by the installer?

maleadt

EDIT: I have made [a brainstorm idea](http://brainstorm.ubuntu.com/idea/12258/) too.

---

### Post by Nullack on 2008-08-16
Create a new account and turf the old one will clean out the settings or do it manually with all the hidden . files in home.

---

### Post by cariboo on 2008-08-16
I clean out all the dot files, except for~/.mozilla and ~/.mozilla-thunderbird.

Jim

---

### Post by MALEADt on 2008-08-16
Yes, I know how to do it manually, and I'm intentionally using a separate home partition to preserve most settings (like desktop wallpaper, evolution settings, rhythmbox database, ...). I think however that certain settings should be overridden by the installer, or at least checked for their consistency.

---

### Post by ronacc on 2008-08-16
sounds like a good idea to me .

---

