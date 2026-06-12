---
title: "New Boot Splash Not Showing Up"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dbulante on 2009-03-19
I have heard about the new boot splash, but since I've upgraded the boot splash has disappeared.  I wonder if it's because I changed the boot splash in Intrepid.  How can I re-install the new boot splash?

---

### Post by dentaku65 on 2009-03-19
> **dbulante said:**
> I have heard about the new boot splash, but since I've upgraded the boot splash has disappeared.  I wonder if it's because I changed the boot splash in Intrepid.  How can I re-install the new boot splash?

You can install startupmanager utility
```
sudo apt-get install startupmanager
```

Then:
```
sudo startupmanager
```
select Appearance -> Usplash themes -> usplash-theme-ubuntu
Close
Reboot

---

### Post by dbulante on 2009-03-19
Thanks for the tip.  I got it installed.

---

