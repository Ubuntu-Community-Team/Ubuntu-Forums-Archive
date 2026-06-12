---
title: "Login Screen gone..."
date: 2005-02-21
forum: Installation &amp; Upgrades
---

### Post by KelteN on 2005-02-21
I took my Ubuntu machine for a reboot and it came back to a terminal login, instead of the usualy Ubuntu login screen.

How do get it to boot back to the login screen?

Thanks

---

### Post by lao_V on 2005-02-21
Do you get any message stating why the graphical manager has not started?
 Try typing startx once logged in and report back on any error messages you get

---

### Post by KelteN on 2005-02-21
startx took me straight into gnome, rather then the login screen where I then go into KDE =x

---

### Post by KelteN on 2005-02-21
[QUOTE=KelteN]startx took me straight into gnome, rather then the login screen where I then go into KDE =x[/QUOTE]
 Alright, I got back in using /etc/init.d/kdm start. Now I just need to figure out how to make it boot kdm.

Also figure out how to get my Audigy 2 soundcard working properly with ALSA...

If anyone knows the answer to any of these questions, please share your knowledge ;P

Thanks

---

