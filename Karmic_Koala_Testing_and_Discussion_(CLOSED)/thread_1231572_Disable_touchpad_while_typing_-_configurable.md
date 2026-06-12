---
title: "Disable touchpad while typing - configurable?"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-08-04
Has anyone found out if there is a way to configure the time a key press blocks the touchpad when "Disable touchpad while typing" in gnome-mouse-properties is activated? IMO it's blocking the touchpad too long. :(

---

### Post by taavikko on 2009-08-04
It calls for "syndaemon" which then "mutes" the keyboard for 0,5 seconds
Needs, further investigating, but should raise a bug for setting in gconf for easier config.

---

### Post by wayne_cat on 2009-08-04
how long is it blocked on your system ... my touchpad is only disabled for about 1 second (or less)

---

### Post by taavikko on 2009-08-04
> **wayne_cat said:**
> how long is it blocked on your system ... my touchpad is only disabled for about 1 second (or less)

ps aux tells that for 0,5sec
```
taavikko  3097  0.0  0.0  19772  1024 ?        S    Aug04   0:11 syndaemon -i 0.5
```

---

### Post by wayne_cat on 2009-08-04
this behavior came with a fix

[http://git.gnome.org/cgit/gnome-settings-daemon/commit/?id=4eb9bd09219afbb56f114a2d10bc585e24db803e](http://git.gnome.org/cgit/gnome-settings-daemon/commit/?id=4eb9bd09219afbb56f114a2d10bc585e24db803e)

---

### Post by MacUntu on 2009-08-04
> **taavikko said:**
> It calls for "syndaemon" which then "mutes" the keyboard for 0,5 seconds
Needs, further investigating, but should raise a bug for setting in gconf for easier config.

Great, thanks. 0.3 feels much better. I think 0.5 is a sane default, but this is really something that should be configurable. Will open a bug.

---

### Post by wayne_cat on 2009-08-04
> **MacUntu said:**
> Great, thanks. 0.3 feels much better. I think 0.5 is a sane default, but this is really something that should be configurable. Will open a bug.

post the link to the bug report ... to confirm it

---

### Post by MacUntu on 2009-08-04
We'll see: [https://bugs.launchpad.net/gnome-settings-daemon/+bug/409086](https://bugs.launchpad.net/gnome-settings-daemon/+bug/409086)

Very happy about this slightly connected fix: [https://bugs.launchpad.net/debian/+source/gnome-settings-daemon/+bug/408095](https://bugs.launchpad.net/debian/+source/gnome-settings-daemon/+bug/408095) =D>

---

### Post by wayne_cat on 2009-08-04
> **MacUntu said:**
> We'll see: [https://bugs.launchpad.net/gnome-settings-daemon/+bug/409086](https://bugs.launchpad.net/gnome-settings-daemon/+bug/409086)

Very happy about this slightly connected fix: [https://bugs.launchpad.net/debian/+source/gnome-settings-daemon/+bug/408095](https://bugs.launchpad.net/debian/+source/gnome-settings-daemon/+bug/408095) =D>

confirmed .... easy to fix ... I think the next version will have it

---

### Post by MacUntu on 2009-08-04
> **wayne_cat said:**
> confirmed

Thanks. [IMG]http://foren.softonic.de/images/smilies/softonic/thumbup.gif[/IMG]

---

### Post by taavikko on 2009-08-05
There's one more thing that needs to be fixed asap.

actually disable the typing when checked.
at the moment it only works on gnome-terminal and maybe few other apps (havent tested much)

Typing isn't disabled while using any browser(firefox-*/arora)/openoffice/etc this is a bit of an problem, do you agree ;)

---

### Post by wayne_cat on 2009-08-14
> **taavikko said:**
> There's one more thing that needs to be fixed asap.

actually disable the typing when checked.
at the moment it only works on gnome-terminal and maybe few other apps (havent tested much)

Typing isn't disabled while using any browser(firefox-*/arora)/openoffice/etc this is a bit of an problem, do you agree ;)

finally ... fixed

```
gnome-settings-daemon (2.27.90-0ubuntu1) karmic; urgency=low

  * New upstream version (LP: #413618):
    - Update gnome-volume-control from gnome-media (Bastien Nocera)
      (#589825).
    - Fix crash in gvc_mixer_stream_is_running() (Chris Coulson)
      (#590073).
    [B][COLOR=Red]- Add '-k' option to syndaemon call for 'Disable touchpad while
      typing' (C de-Avillez) (#590588, LP: #408095).[/COLOR][/B]
    - Low disk space warning bug-fixes (Chris Coulson)
      (#591153, LP: #404340).
  * Removed patches that are merged upstream now:
    - 60_ldsm_notification_fixup.patch
    - 62_fix_media_keys_memory_errors.patch
  * Removed 11_sleepkey.patch - there is no key assigned to sleep by
    default and gdm-signal does not exist on the default install.
  * Refreshed patches:
    - 61_fix_volume_notification.patch
    - 70_migrate_touchpad_config.patch
    - 90_autoreconf.patch
  * debian/control:
    - Add versioned build-dep on libpulse-dev (>= 0.9.15).
  * Also fixes LP: #404340.

```

---

