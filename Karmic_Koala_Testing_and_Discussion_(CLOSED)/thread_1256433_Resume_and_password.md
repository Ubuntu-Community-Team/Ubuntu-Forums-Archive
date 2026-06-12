---
title: "Resume and password"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Arla on 2009-09-02
I've done a scan and couldn't find this mentioned, so wanted to throw it out there.

I've noticed of late (certainly since .8 release) that when I can resume from standby (sometimes it works, sometimes not, but that's already a bug) sometimes it doesn't ask me for a password? Is there any logic that, being a linux newbie, I'm missing? I know I thought in the original Alpha 4 it always asked for a password on resume?

---

### Post by berthiggins on 2009-09-03
my observation is that if I manually suspend the machine from a menu then I do not get asked for a password but if it suspends when I shut the lid it does.

---

### Post by scaine on 2009-09-03
Not tried this on Karmic, but the settings that govern it in Jaunty (and certainly do appear in Karmic too) are in gconf-editor, under apps/gnome-power-manager/lock.

You should tick "use_screensaver_settings" and then you can turn on the password-after-resume prompt by changing your screensaver settings.  It's unticked by default.

On the other hand, if you want to have a password when your screensaver comes on, but not when you suspend, try unticking "suspend" instead.

---

### Post by phelin4 on 2009-09-17
I still see this issue with current Karmic, but now the behaviour is constant. When I resume the laptop from suspend it neveer asks for a password anymore. I have tried to set the gnome-powermanager to use lock when resuming from suspend as well as use the screensaver-settings and setting lock in the screensaver properties. But neither seems to work. Has anyone else experience on this same issue? Any bug reports yet?

---

### Post by tekstr1der on 2009-09-17
Launchpad bug:

[https://bugs.launchpad.net/ubuntu/+bug/407315](https://bugs.launchpad.net/ubuntu/+bug/407315)


Looks to be fixed upstream in gnome-session:

[http://git.gnome.org/cgit/gnome-session/commit/?id=fc11487acb6584f7c9deb705e8bdf46aeee0aa75](http://git.gnome.org/cgit/gnome-session/commit/?id=fc11487acb6584f7c9deb705e8bdf46aeee0aa75)

---

### Post by phelin4 on 2009-09-17
Thanks!

---

