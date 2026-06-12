---
title: "Xubuntu autologin"
date: 2016-04-17
forum: Installation &amp; Upgrades
---

### Post by cpdondo on 2016-04-17
Is there some xubuntu way to set up autologin?

I went by the autologin setup on installation and now I want to enable it, but I'm struggling.  

Dpkg-reconfigure doesn't do it.

What does?

---

### Post by cpdondo on 2016-04-18
More details:

I set up /etc/lightdm/lightdm-gtk-greeter.conf.d/10_autologin.conf:

[Seat:*]
autologin-user=crat
autologin-user-timeout=0
user-session=xubuntu

No joy.  I also tried adding those lines to lightdm-gtk-greeter.conf; it's as if the config files are being ignored.  Nothing like dpkg-reconfigure user-setup or dpkg-reconfigure lightdm brings up any sort of dialog that allows autologin.

I remember seeing it on install, so I know it's in there somewhere......

---

