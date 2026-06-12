---
title: "Fast-user-switch-applet and gdm issue..."
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shifty_powers on 2009-07-21
I had a bunch of updates being held back.

So like a fool i decided to use aptitude to install them, so they'd stop bugging me whenever i check for updates.

problem is they removed my fast-user-switch-applet, and stopped me automatically logging in.

i also have two volume controls in my sys tray....

when i try to reinstall the above, it says that the gdm package is broken...

any ideas? (see attached piccies).

edit: oh and my trash doesn't work, it crashes whenever i try to launch it and can't seem to empty it...

---

### Post by taavikko on 2009-07-21
F-U-S-A doesn't work with the new gdm at the moment, so no worries.

Update via main-server, so you'll get the latest at all times (local repos might be out of sync)
ubuntuone-client is to blame on nautilus crashing.

Trash can be emptied via CLI
```
rm -r ~/.local/share/Trash*
```

for volume-applets, i'm still uncertain...

---

### Post by shifty_powers on 2009-07-21
heh, didn't know that about the ubuntu-one client and nautilus...

so when gdm is updated will it reinstall the applet?

or will i need to reinstall it myself?

and i knew that command, but problem is i keep flitting between os's, i'm notorious for it, and had temporarily forgotten it :D

many thanks. can live with the volumes for now..

---

### Post by taavikko on 2009-07-21
gdm and fusa is no doubt being worked on. you'll notice when it's been fixed.
Just make sure that "ubuntu-desktop" package is installed so you'll reap the benefits.

---

### Post by shifty_powers on 2009-07-21
funnily enough, an update for ubuntu-one just came out and fixed the trash issue.

as for the rest, can live with it for now :D

---

