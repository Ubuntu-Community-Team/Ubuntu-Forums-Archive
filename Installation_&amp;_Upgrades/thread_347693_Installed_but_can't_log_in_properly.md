---
title: "Installed but can't log in properly"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by PelicanLake on 2007-01-27
Hello, 

I am new to ubuntu and the forms, I have installed 6.10 on my laptop (Toshiba Satellite P-10) and Grub appears to work fine,ubuntu log-in loads, but after I enter my user name and password it (Gnome?) appears to get hung, and I am left looking at a brown-ish orange screen.  

However, I can press Ctrl+Alt+BkSp to get back to the log-in screen. The only way I can log-in at all is under the fail-safe terminal. I would like to be able to log-in normally, can some one tell me how to fix this?

---

### Post by taurus on 2007-01-27
Boot into recovery mode from GRUB menu and run

```
aptitude update
aptitude install ubuntu-desktop
shutdown -r now  <-- to reboot
```

---

