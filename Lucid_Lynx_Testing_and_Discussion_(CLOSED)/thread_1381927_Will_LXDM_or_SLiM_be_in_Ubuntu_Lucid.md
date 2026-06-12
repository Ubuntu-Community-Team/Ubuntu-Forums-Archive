---
title: "Will LXDM or SLiM be in Ubuntu Lucid?"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Psumi on 2010-01-15
it would be nice to have a good DM rather than have to rely on GDM or GNOME depends; or have ugly ones like XDM or WDM, which don't work if you choose to logout.

LXDM should be included in the ubuntu repos to be honest. What do you all think? Sorry, but I'm not putting this in the mailing list, I don't see why I must do so to get my ideas across to the devs, and in fact, I've only had bad experiences with mailing lists.

---

### Post by VMC on 2010-01-15
Not quite sure what your after. You want only LXDM instead of Gnome, and to get rid of any gnome related stuff?

If you want a pure LDXE have you checked out [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") ? I tried it some time last year in its infancy.

---

### Post by BwackNinja on 2010-01-15
This is talking about LXDM the desktop manager as a replacement for GDM in Lubuntu, which would allow Lubuntu to not depend on GDM and its dependencies that are much more suitable and actually used in a Gnome desktop.

I hope this can get through. Good luck.

---

### Post by snowpine on 2010-01-15
[http://packages.ubuntu.com/lucid/slim](http://packages.ubuntu.com/lucid/slim)

---

### Post by VMC on 2010-01-15
> **snowpine said:**
> [http://packages.ubuntu.com/lucid/slim](http://packages.ubuntu.com/lucid/slim)
There you go. Talk about slim pickens, this looks promising.

---

### Post by Psumi on 2010-01-15
> **snowpine said:**
> [http://packages.ubuntu.com/lucid/slim](http://packages.ubuntu.com/lucid/slim)

Thank you goddess, I was beginning to think that the ubuntu repos would never have any good lightweight DM.

---

### Post by Hero of Time on 2010-02-04
While you're at it, check [http://packages.ubuntu.com/lucid/lxdm](http://packages.ubuntu.com/lucid/lxdm), exactly what you're looking for.

Only thing I'm having issues with, is my PATH variable. When I log in to a TTY, it has the /sbin and /usr/sbin, but in X, I don't. All I have is /bin, /usr/bin and /usr/local/bin. Currently looking for a solution. I didn't have this with GDM, nor with SLiM, but with the latter, I know I put the PATH in it's config file, but I can't seem to get the same info for lxdm.conf.

Edit:
Got the PATH variable working, put it in /etc/lxdm/Xsession.

---

