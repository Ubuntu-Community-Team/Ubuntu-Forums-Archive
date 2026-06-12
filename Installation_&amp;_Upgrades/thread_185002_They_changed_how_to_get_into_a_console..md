---
title: "They changed how to get into a console."
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by yatt on 2006-05-30
Or at least it changed on my machine. During an update my fglrx driver's screwed up (again), and usually, I just press <ctrl><atl>F1 and run a script that will install and configure the driver. When I did that today, X restarted, I then tried <ctrl><atl>F2 and X restarted. I tried up to F7 and even <ctrl><atl>Backspace (to see if they just switched the two). Any idea how I can get to a consol so I can fix my drivers, then change the settings so that pressing <ctrl><alt><Function Key> will bring me to a console?

---

### Post by slavik on 2006-05-30
you can open the terminal from within X and then do the stuff there. then restart the X server.

---

### Post by CP-Geek on 2006-05-30
cheked your keyboard shortcuts? Perhaps they got messed up? (Happened to me once on update too) Alltho they might be right, assign them again and do a re-test.

---

### Post by yatt on 2006-05-30
[QUOTE=slavik]you can open the terminal from within X and then do the stuff there. then restart the X server.[/QUOTE]
The script cannot run if X is running. If I try to, it returns this message:
```

Can`t be run within X! Use a text console (ALT-CTRL-F1)

```

---

### Post by yatt on 2006-05-31
[QUOTE=CP-Geek]cheked your keyboard shortcuts? Perhaps they got messed up? (Happened to me once on update too) Alltho they might be right, assign them again and do a re-test.[/QUOTE]
I donnot see any option for them in System->Admin->Keyboard Shortcuts. How else could I set them?

Is there just a terminal command I could use?

---

### Post by Tamihania on 2006-05-31
...try init 3 or sudo init 3...

tami

---

### Post by xaverx on 2006-05-31
run gnome-terminal and type: sudo /etc/init.d/gdm stop
then run your script and type sudo /etc/init.d/gdm start
thats all.

---

