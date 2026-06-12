---
title: "Panel jacked-up after upgrade"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2008-05-25
I decided to try the upgrade on cloned hard disk. There are a few problems, so I am going to try to solve those problems before going truly live.

This is the first problem I want to solve. I chose the upgrade option from the update manager. After reboot, the panel at the bottom of the screen is colored completely white, no notification area, notta. Until I right click, goto properties, and click on show autohide buttons. 

The top panel is fine. 

What could be causing this?

---

### Post by lsutiger on 2008-05-26
???

---

### Post by lsutiger on 2008-05-28
??? Anybody? Bueller? Bueller? Bueller?

---

### Post by lsutiger on 2008-05-29
OK Gmail manager is now available. If I can get the other problems fixed, I am sold!
Somebody, anybody, hook a fellow Ubuntu user UP!

---

### Post by lsutiger on 2008-06-03
??

---

### Post by iaculallad on 2008-06-03
Drop to your terminal:

```
sudo gconftool-2 --shutdown
suro rm -rf ~/.gconf/panel
sudo pkill gnome-panel
```

Hope this will fix your panel problem.

---

### Post by lsutiger on 2008-06-07
Thanx for the reply!

It worked temporarily...until I rebooted. Now I can't fix it the way I did before.

There are a ton of updates to do ( I am using the cloned drive again )...I'll be back

---

### Post by lsutiger on 2008-06-07
Update fixed the panel problem, killed something else (virtual box)

---

