---
title: "Laptop upgraded to 14.04, blank screen on wake up from hibernation"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by cpdondo on 2014-04-22
I have an eeePC 901 laptop that ran xubuntu 13.10 great.  I enabled hibernation and everything worked fine.  Yesterday I upgraded to 14.04, and now when the laptop wakes up from hibernation I get a graphical unlock screen that prompts me to enter my password.  I enter my password, and the screen goes black.  Utterly black as if it's powered off.

I've re-enabled hibernation in polkit:

```
# cat localauthority/10-vendor.d/com.ubuntu.desktop.pkla
[snip]

[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
# 
```

And changed systemd to either ignore or hibernate on lid switch; both hibernate the machine but neither wakes it up properly.

If I close the lid while the screen is black the laptop will hibernate correctly, but again, will go to a black powered down screen once I enter my password in the unlock screen.

I can ssh into the laptop with no problems.  Everything works, no errors in the log files, but nothing on the screen.

This seems to be a fairly common problem with 14.04 but the solutions so far don't work for me.  This could be an issue with xubuntu lock screen or lightdm or a backlight driver....

system:

xubuntu
eeepc 901

---

### Post by cpdondo on 2014-04-22
HAH!  xubuntu has changed to "light locker" for display management.  I turned it off completely and all is well.

---

### Post by jacobmar1ey on 2014-04-25
I'm having the same problem on an Acer Aspire V5-171. How did you turn off light locker and what other features does that effect?

---

### Post by jacobmar1ey on 2014-04-25
Ah, found it in the Settings Manager. I too had no problems once it was disabled. However that means that my screen does not lock on sleep, which is not acceptable to me.

---

