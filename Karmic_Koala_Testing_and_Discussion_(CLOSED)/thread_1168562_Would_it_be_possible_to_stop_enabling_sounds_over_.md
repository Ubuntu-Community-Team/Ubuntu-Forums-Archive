---
title: "Would it be possible to stop enabling sounds over and over again?"
date: 2009-05-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-05-24
Every so often I get surprised by the ubuntu startup sound - which is totally uncool when sitting e.g. in the library.

Could you please stop enabling sounds when the related package gets updated?

---

### Post by psyke83 on 2009-05-24
> **excogitation said:**
> Every so often I get surprised by the ubuntu startup sound - which is totally uncool when sitting e.g. in the library.

Could you please stop enabling sounds when the related package gets updated?

You're using an alpha in a "production environment"??? :P

---

### Post by tajreed on 2009-05-24
Go to preferences/sound and turn it off.

---

### Post by ranch hand on 2009-05-24
psyke83
+1
Got a couple on the forum here that appear to have balls from hell.

excogitation
I can sympathize with your problem.  Up until 9.04 when I booted I got terrible noise because the didgital output jack on my audigy card was always enabled.  Knock you of your chair noisy.

The only thing I can suggest is to unplug the speekers or disable them in bios (if you do not need them for your session).

No one is going to disable those sounds as default.  It appears that YOU MUST HAVE SOUNDS.  Beats me, I turn the buggers off.

---

### Post by psyke83 on 2009-05-24
> **excogitation said:**
> Every so often I get surprised by the ubuntu startup sound - which is totally uncool when sitting e.g. in the library.

Could you please stop enabling sounds when the related package gets updated?

Ok ok, teasing aside ;). What you can do is set up a dpkg diversion for the desktop login sound, which should survive package upgrades.

To add diversion:
```
$ sudo dpkg-divert --add --rename --divert /usr/share/sounds/ubuntu/stereo/desktop-login.ogg.disabled /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```

To remove diversion:
```
sudo dpkg-divert --remove --rename/usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```

You're not going to get the attention of package maintainers in a forum posting, and it's not really reasonable to ask for the package not to reset settings. Upgrading between distributions will require some packages to reset settings to defaults, and it's a small price to pay during the testing process.

---

### Post by excogitation on 2009-05-24
> **psyke83 said:**
> You're using an alpha in a "production environment"??? :P

No, of course not - I have it on an USB stick and just boot it from time to time to test and run updates to see how it progresses.

Thanks for your comments.

I still think user made changes in preferences of any program shouldn't be reset by a new version - unless that setting has changed/isn't available anymore.

---

### Post by psyke83 on 2009-05-24
> **excogitation said:**
> No, of course not - I have it on an USB stick and just boot it from time to time to test and run updates to see how it progresses.

Thanks for your comments.

I still think user made changes in preferences of any program shouldn't be reset by a new version - unless that setting has changed/isn't available anymore.

In the development phase, there is less emphasis on the transition between newversion-ubuntu1 and newversion-ubuntu2 releases, but more on oldversion-ubuntu12 to newversion-ubuntu3 (for example).

---

### Post by plun on 2009-05-24
Another option is to use another sound-theme  ;)

Sound-theme-freedesktop is within karmics repo

Package Info
[http://packages.ubuntu.com/karmic/sound-theme-freedesktop](http://packages.ubuntu.com/karmic/sound-theme-freedesktop)


--

---

