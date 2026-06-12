---
title: "couple of minor things"
date: 2009-07-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-07-26
anyone else have this or is there a setting i need to change that i've missed or can't find.

1.  while playing movies, either with vlc, movie player (totem), or kaffeine (in gnome) screensaver doesn't automatically disable itself for the movie or video clip.  (I prefer vlc, with screensaver set to 5 minutes it will start in 5 minutes while the movie is running)

2.  I can't eject my cd/dvd rom without entering my sudo password.  If I right click on the cdrom on the desktop and select eject, it asks for admin password.  pushing the open tray button on the cdrom tray has no effect.

EDIT:  just tried typing "eject" into terminal and it ejected without sudo rights.  but right clicking on the cdrom icon on desktop still wants sudo rights, any ideas?

---

### Post by jaakan on 2009-07-26
for 1. I think there might be a setting for that

for 2. Did you do a clean install or upgrade?

try doing a clean install with the latest daily live CD if you can and see if that doesn't happen.

---

### Post by JOHNNYG713 on 2009-07-26
HI for #1 I have always had to disable the screensaver to watch videos And for # 2 try going into SYSTEM > ADMINISTRATIONS > AUTHORIZATIONS > EJECT REMOVABLE MEDIA and set permissions to yes

---

### Post by buzzmandt on 2009-07-26
> **jaakan said:**
> for 1. I think there might be a setting for that

for 2. Did you do a clean install or upgrade?

try doing a clean install with the latest daily live CD if you can and see if that doesn't happen.

clean install alpha 3 plus current updates.

---

### Post by buzzmandt on 2009-07-26
> **JOHNNYG713 said:**
> HI for #1 I have always had to disable the screensaver to watch videos And for # 2 try going into SYSTEM > AUTHORIZATIONS > EJECT REMOVABLE MEDIA and set permissions to yes

I don't have system > authorizations
I have system > preferences, administrative but neither of those has authorizations or eject removable media

---

### Post by lonniehenry on 2009-07-26
you should have System, Administration, Authorizations in your main menu. If you don't then do System, Preferences, Main Menu.  check the box to put it in the main menu. 
Then you will be able to open authorizations and set the eject media permissions to yes.

---

### Post by budluva04 on 2009-07-26
> **buzzmandt said:**
> I don't have system > authorizations
I have system > preferences, administrative but neither of those has authorizations or eject removable media

System>Administration>Authorizations

is what you are looking for...then navigate to...

org>freedesktop>hal>storage>eject removable media

---

