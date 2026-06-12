---
title: "Session bombing out upon upgrade"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by leftystrat on 2013-07-01
Upgraded 5 machines to 13.04.  At least three of them simply bomb out.  I can log in, then when I bring up a program or terminal, I get sent back to login.  I send in reports when this happens but it's getting hard to get work done when the session crashes.

---

### Post by dino99 on 2013-07-01
you said "upgraded" , which let me think about possible old config/setting/lib left behind : so boot in recovery mode and clean the system as much as you can : clean/autoclean/autoremove/gtkorphan/bleachbit
also check the /etc/apt/sources.list (easier done with synaptic) about possible incompatible entries , like ppas used before dist-upgrade

---

### Post by Bucky Ball on 2013-07-01
*Thread moved to **Installation & Upgrades**.*

_**Reason:**_ Unrelated to Desktop Environments.

Just wondering if this is a production environment. If so, was there a specific reason to upgrade from the LTS, if that's what you were using?

---

### Post by leftystrat on 2013-07-01
I'll give the cleaning a shot, thanks.

---

### Post by leftystrat on 2013-07-01
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

_**Reason:**_ Unrelated to Desktop Environments.

Just wondering if this is a production environment. If so, was there a specific reason to upgrade from the LTS, if that's what you were using?

Not a production environment.  I usually upgrade and never have problems like this.

---

### Post by dannyboy79 on 2013-07-01
whenever it bombs you back to login, that most times means there's no room left on / to write temp files to. that's not the case is it?

---

### Post by leftystrat on 2013-07-01
> **dannyboy79 said:**
> whenever it bombs you back to login, that most times means there's no room left on / to write temp files to. that's not the case is it?

not the case, thanks.

---

### Post by Vormeph on 2013-07-01
This is actually a bug with the Desktop Environment that's quite recent. It can be fixed with a patch. I received the same sort of bug when I open the terminal; xfce simply crashes to the log-in screen. 

This is what I did to fix the bug. USE AT YOUR OWN RISK:

```
sudo add-apt-repository ppa:ricardo.teixmas/xfce4-session
sudo apt-get update
```

You should then receive updates: install them and reboot. Because you can't use the default xfce terminal, use another terminal. Hit CTRL+ALT+F1 if you want, then CTRL+ALT+F7 to return to the GUI.

[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1172018](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1172018)

There are multiple things causing the crash. On my part it was because I had Firefox/Thunderbird open at the same time. I hope this fixes your problem.

---

### Post by leftystrat on 2013-07-02
> **Vormeph said:**
> This is actually a bug with the Desktop Environment that's quite recent. It can be fixed with a patch. I received the same sort of bug when I open the terminal; xfce simply crashes to the log-in screen. 


[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1172018](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1172018)

There are multiple things causing the crash. On my part it was because I had Firefox/Thunderbird open at the same time. I hope this fixes your problem.

Thanks for the info.  Hopefully they'll get this fixed.  This is a definite first for me and Xubuntu.

---

### Post by Vormeph on 2013-07-03
> **leftystrat said:**
> Thanks for the info.  Hopefully they'll get this fixed.  This is a definite first for me and Xubuntu.

Has your issue been fixed? Did my solution work?

---

