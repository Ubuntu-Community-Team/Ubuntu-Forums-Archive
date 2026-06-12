---
title: "Ubuntu 13.04 update made desktop background white?"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by Jamie_Edwards on 2013-05-03
Hi guys,

Ubuntu 13.04 recently updated itself and something weird happened... The desktop went whit. Everything else works but when it comes to the background, it just doesn't want to use any other pictures.

Any ideas?

Ubuntu 13.04 ( 64 bit )
Unity DE,
Gnome Shell DE

NOTE: I even tried loading the Gnome Shell DE with exactly the same outcome.

Any ideas?

---

### Post by matt_symes on 2013-05-03
Hi

Is the draw background flag set ?

Install dconf-tools

```
sudo apt-get install dconf-tools
```

or use software center.

Run it with

```
dconf-editor
```

Navigate to ```
org->gnome->desktop->background->draw background 
``` and make sure it's checked.

It's been a while since i used Unity so this may have changed and I'm relying on my notes of the time but I think it's worth a check.

Kind regards

---

### Post by Jamie_Edwards on 2013-05-04
Yeah, it's checked but when I clicked on it, it said in the description that it's deprecated and also ignored. :L

---

### Post by markbl on 2013-05-04
Are you running with the gnome 3 ppa for your GNOME DE? That picks up Nautilus 3.8 which breaks your backgrounds. There are a few threads about it. E.g [http://ubuntuforums.org/showthread.php?t=2130575](http://ubuntuforums.org/showthread.php?t=2130575) and [http://ubuntuforums.org/showthread.php?t=2132631](http://ubuntuforums.org/showthread.php?t=2132631).

---

### Post by Jamie_Edwards on 2013-05-05
I have to use either Unity or Gnome not both..? That sucks.

---

### Post by markbl on 2013-05-05
> **Jamie_Edwards said:**
> I have to use either Unity or Gnome not both..? That sucks.
No, that's not what I or anybody is saying. You can install gnome-shell and login to GNOME session without issue. You will only (currently) have a problem if you add the GNOME 3 PPA.

---

### Post by Jamie_Edwards on 2013-05-05
Sorry XD, that's what I meant :L So really the only way to get my unity background back is to not get the ppa version of GS?

---

