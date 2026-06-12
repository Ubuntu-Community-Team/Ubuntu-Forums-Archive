---
title: "[SOLVED] Compiz Fusion not retained after reboot"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2008-07-29
Hi,

If I select Compiz Fusion it works fine.  If I then reboot or logoff/login it is no longer selected.

Using NVIDIA driver 177 on a GeForce 8800GTS.

Any suggestions please?

---

### Post by ronacc on 2008-07-29
already reported as bug#249265 . no workaround yet that I know of .

---

### Post by DavidONE on 2008-07-29
Thanks, ronacc.  I added a comment to the bug so that others can find it for 'compiz fusion': [https://bugs.launchpad.net/ubuntu/+bug/249265](https://bugs.launchpad.net/ubuntu/+bug/249265)

---

### Post by Coleop on 2008-07-30
I had the same problem. I don't know if this will help but if you had compiz-fusion running before hand, go to the systems menu and then Preferences, then Sessions and add a new Startup Program item and name it CompizFusion with "compiz --replace" as the command line and save, it should start after a reboot.  I did this and it loads at bootup and has worked for me :) Hope it works for you.

---

### Post by DavidONE on 2008-07-31
That fixed it!  There was no Compiz entry in Sessions.  D'oh!

Thanks, Coleop. :)

[edit] Bug created - [https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-bcop/+bug/253606](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-bcop/+bug/253606)

---

### Post by chrisccoulson on 2008-08-01
The changes to gnome-session mean that the default window manager is now stored in a GConf key. The proper workaround (I think) is to actually modify those keys (as opposed to adding a session entry). Adding a session entry means that Metacity is loaded and then Compiz is loaded afterwards.

To set the keys manually:
```
gconftool-2 --set --type=string /desktop/gnome/session/required-components/windowmanager compiz
gconftool-2 --set --type=list --list-type=string /desktop/gnome/session/default-session [gnome-settings-daemon,compiz,gnome-panel,nautilus]
```

---

