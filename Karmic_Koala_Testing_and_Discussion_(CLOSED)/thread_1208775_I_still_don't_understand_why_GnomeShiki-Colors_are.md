---
title: "I still don't understand why Gnome/Shiki-Colors are not included by default..."
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-07-09
Why do the good theme and icon sets end up in the community-themes or separate packages, but all the old and aesthetically challenged themes get included out-of-box?

---

### Post by pferraro on 2009-07-09
> **Starks said:**
> Why do the good theme and icon sets end up in the community-themes or separate packages, but all the old and aesthetically challenged themes get included out-of-box?

It is a *good* thing that gnome/shiki-colors are packaged separately.  That way these themes can evolve at their own pace, without having to wait on the update of some umbrella package, e.g. gnome-themes-extras, community-themes, etc.  Whether or not it gets installed by default is a matter of adding a recommended/suggests dependency in the ubuntu-desktop package.

---

### Post by psyke83 on 2009-07-09
> **Starks said:**
> Why do the good theme and icon sets end up in the community-themes or separate packages, but all the old and aesthetically challenged themes get included out-of-box?

Disk space alone is a reason, but there are probably others.

By the way, aren't the "old and aesthetically challenged" themes already omitted from the default install of Karmic?

The artwork changes usually come later in the development cycle, so anything can happen.

---

### Post by rudenko_ruslan on 2009-07-09
It seems, that "arc-colors" package is useless for now - there is no way to enable this theme to a new GDM in Karmic :(

---

### Post by wayne_cat on 2009-07-09
> **rudenko_ruslan said:**
> It seems, that "arc-colors" package is useless for now - there is no way to enable this theme to a new GDM in Karmic :(

Unfortunately they have removed the "theming part" from gdm 2.26. The arc-* packages are useless on Karmic at the moment ;)

---

### Post by pferraro on 2009-07-09
> **rudenko_ruslan said:**
> It seems, that "arc-colors" package is useless for now - there is no way to enable this theme to a new GDM in Karmic :(
Not completely useless - the arc-* packages contain background images.

---

### Post by DanaG on 2009-07-10
Actually, it's not all that hard to configure the new GDM; it's just not documented.  Here's how to do it: Go to the login screen, then switch to a TTY and run:
DISPLAY=:0 sudo -u gdm xterm  (gnome-terminal won't work -- no gconf daemon running.)

Then you can run gconf-editor (and enable the gnome media-keys thingy / volume-control thingy) somewhere in /apps/gdm -- and you can also run gnome-appearance-properties.

(In fact, I set metacity to run a console on ctrl-shift-F10, and then edited the entry in /etc/passwd to give gdm user a real /bin/bash shell.)

---

### Post by wayne_cat on 2009-07-10
> **DanaG said:**
> Actually, it's not all that hard to configure the new GDM; it's just not documented.  Here's how to do it: Go to the login screen, then switch to a TTY and run:
DISPLAY=:0 sudo -u gdm xterm  (gnome-terminal won't work -- no gconf daemon running.)

Then you can run gconf-editor (and enable the gnome media-keys thingy / volume-control thingy) somewhere in /apps/gdm -- and you can also run gnome-appearance-properties.

(In fact, I set metacity to run a console on ctrl-shift-F10, and then edited the entry in /etc/passwd to give gdm user a real /bin/bash shell.)

You can enable one of the arc-colors themes?

---

### Post by DanaG on 2009-07-10
You should be able to, as long as the themes are in /usr/share/themes.

---

### Post by wayne_cat on 2009-07-10
> **DanaG said:**
> You should be able to, as long as the themes are in /usr/share/themes.

Are you sure? the new gdm is a rewrite, and the latest version does not support gdmgreeter style XML themes. ;)

---

### Post by DanaG on 2009-07-10
Heh, why don't you give it a try?  DISPLAY=:0 sudo -u gdm gnome-appearance-properties (though you have to have gdm AT the login screen for this to work.)

Essentially, the new GDM uses a locked-down gnome session and gnome-settings-daemon; that's how it manages the wallpaper, and all that.  In fact, if you set the wallpaper the same as that at your desktop, it'll even be more consistent than the old one could ever be.

---

### Post by plun on 2009-07-10
> **Starks said:**
> Why do the good theme and icon sets end up in the community-themes or separate packages, but all the old and aesthetically challenged themes get included out-of-box?

It must be room for plain "crap"........

Be happy with Crux, Glider and Glossy....:lolflag:

---

