---
title: "CHROMIUM keeps crashing &amp; freezing"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by wfriedwaldgmail.c on 2018-07-10
running Ubuntu 18.

whenever I open the CHROMIUM app, it automatically freezes and crashes.

I tried deleting & re-installing the app, but it still keeps happening.  My guess is that it's some kind of preference file issue?

is there any way to prevent this from happening?  Need to run CHROMIUM!

thanks, as always, for any help.

w

---

### Post by ajgreeny on 2018-07-10
Try closing chromium then renaming the hidden folder in your home, ~/.config/chromium as a backup (just in case you need anything in it) ~/.config/chromium-backup.
Now open chromium again.
Any better? If so it shows your configuration was corrupt in some way.

---

### Post by wfriedwaldgmail.c on 2018-07-11
thanks!

but RATS!  I know I am doing something wrong, I opened the ".config" folder and there doesn't seem to be a CHROMIUM item in there, unless it's double hidden or something!

thanks again.  will keep trying!


[ATTACH=CONFIG]280356[/ATTACH]

---

### Post by deadflowr on 2018-07-11
Sounds like the snap version.
Look for the snap config at ~/snap/chromium/current/.config/chromium

EDIT:
You can install the normal debian/apt version
```
sudo apt install chromium-browser
```

I think the snap version is a new default app for Ubuntu.
(for whatever reason)

You can remove the snap version if you want
```
sudo snap remove chromium
```
and then use only the apt version.

Many users prefer using the tried and true apt version, as it's tried and true.
snap packages are new and goofy.

---

### Post by wfriedwaldgmail.c on 2018-07-11
you know your business, boy!

yes, that seems to have worked!  thanks very much indeed!

w

---

### Post by ajgreeny on 2018-07-11
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

