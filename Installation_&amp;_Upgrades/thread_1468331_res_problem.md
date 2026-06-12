---
title: "res problem"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by 2roombas on 2010-05-01
Hi... I did the i915.modeset=0 xforcevesa thing and yippie, it worked!:) However the res is all messed up (see attached) and only a 640x480 monitor is detected. 

Before I click the "install" icon to install this on this desktop, how can I fix that?  And am I even to assume that that clicking the install icon is all I need to do now?

---

### Post by P4man on 2010-05-01
Chances are you will have the exact same problem after installing. Have you tried with just i915.modeset=0 ?

---

### Post by 2roombas on 2010-05-01
> **P4man said:**
> Chances are you will have the exact same problem after installing. Have you tried with just i915.modeset=0 ?

I just did that and so far so good. Thank you!:)

---

### Post by P4man on 2010-05-01
You will probably need to apply that same fix after installing. 
If so, edit /etc/default/grub 

Find this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0"

youll have to run ```
sudo update-grub 
```after that

---

