---
title: "NUC can't boot when connected to TV!!!"
date: 2019-01-13
forum: Installation &amp; Upgrades
---

### Post by germ65 on 2019-01-13
Recently bought Intel NUC 8i3BEH (Core i3 8th generation), 8 GB RAM, 240 GB SSD to replace my Gigabyte mini-PC which died an unexpected and early death after 3 years of service. It was running previous Ubuntu version and had to tweak xrandr to try to get a good image but otherwise never had a problem.

TV is old Sony KDF E50A10. Connection is via HDMI, not the separate RGB+audio inputs designated "PC" on the TV. This is also how the Gigabyte mini-PC was connected. 

So I setup Ubuntu 18.10 on a separate computer monitor. Everything runs great, including Logitech wireless keyboard/trackpad. Then I connect to TV and get this:



What is this? After some search it seems this is how systemd signals that something when wrong when booting?!?

What do I do now?

---

### Post by wildmanne39 on 2019-01-13
I do not believe the forum volunteers can see the error message in the image.

Please post the terminal output using code tags instead of using images- if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by germ65 on 2019-01-13
Here's the code on the screen as best as I can read it:
```
 Ubuntu 18.10
                                                                 .   .   .   .[   OK  ] Created slice User Slice of UID 1000.
] Created slice system-user\xZdruntime\xZddir.slice.
] Started /run/user/1000 mount wrapper.
  Starting User Manager for UID 1000...
] Started Session 1 of user xxxxx.
] Started User Manager for UID 1000.

```

First line is shifted to the right of the screen. Following lines are missing a few characters. Too bad I can't see what's inside the []--I suppose that may be useful.

---

