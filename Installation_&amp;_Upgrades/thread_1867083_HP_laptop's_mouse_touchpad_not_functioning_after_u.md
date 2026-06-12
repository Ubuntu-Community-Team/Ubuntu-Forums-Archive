---
title: "HP laptop's mouse touchpad not functioning after upgrade"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by pooja on 2011-10-22
Hi there!
I have an **HP Pavilion dv6385ea laptop** (bought in mid 2007) with Ubuntu 11.10. I've actually recently upgraded from 11.04. The mouse touchpad didn't work then and surely doesn't work now except the fact that when Ubuntu 11.10 asks for the login password, the touchpad works perfectly. Once I enter Ubuntu, it stops working and I have to plug in a USB external mouse in order to move around. I'd prefer using the touchpad mouse because it consumes less battery power than the external mouse. 

I tried some tweaks I found on the Internet but the problem persists. There's clearly something in the OS that needs to be configured otherwise why should it work before logging in?

Can anyone please help with this problem? I know I'm not the only one with this issue.

---

### Post by pooja on 2011-10-22
Just found out that the mouse touchpad works flawlessly if I login in the "Guest Session". How come it doesn't when I login with my password?

---

### Post by pooja on 2011-10-22
Hi everyone!
I just got over the problem by referring to[ comment #8 on this page]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400?comments=all").
It worked for me!
Thanks to all the Canonical's big heads!

```
: gsettings set org.gnome.settings-daemon.plugins.mouse active false
Then close your session with: gnome-session-quit
```

---

