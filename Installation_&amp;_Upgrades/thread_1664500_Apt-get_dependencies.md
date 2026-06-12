---
title: "Apt-get dependencies"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2011-01-11
Recently I force removed pulseaudio from my system, because it was doing awful and terrible things to it. I've had no problems since with audio... ALSA seems to be working perfectly.

However, apt-get no longer works properly. I get this error message:
```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ubuntu-desktop : Depends: gstreamer0.10-pulseaudio but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

How can I tell my system that I don't *want* that lousy stinking piece of software that destroys my audio output (and freezes my video to boot)?

---

### Post by Taijitu on 2011-01-11
Hey. You should just remove the ubuntu-desktop package causing the error message. Don't worry, it is only a "meta package" to pull in alle the software for the standard ubuntu dekstop.

```
sudo apt-get remove ubuntu-desktop
```

Hope this helps :)

---

