---
title: "sync. out of range"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by eruheru on 2005-11-05
i just installed ubuntu and when i start up the computer it says "Sync. out OF Range" in a red box that moves across the screen. when i press the power button it goes back to login for a few seconds, then shuts down. How can i easily fix this?

---

### Post by Xian on 2005-11-05
You need to edit the "Monitor" section of your xorg.conf file.
Make sure that the HorizSync and VertRefresh values are correct.

At the command line enter this to edit the file by hand:

```
$ sudo nano -w /etc/X11/xorg.conf
```

---

### Post by eruheru on 2005-11-05
[QUOTE=Xian]You need to edit the "Monitor" section of your xorg.conf file.
Make sure that the HorizSync and VertRefresh values are correct.

At the command line enter this to edit the file by hand:

```
$ sudo nano -w /etc/X11/xorg.conf
```[/QUOTE]

its coming up as an unrecognized file command.

---

