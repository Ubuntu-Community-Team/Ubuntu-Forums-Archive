---
title: "[SOLVED] kubuntu intrepid: where are the title bars of windows"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by linomac on 2008-10-06
after the upgrade from kubuntu hardy, windows have no titlebar, so also no possibility to move them. minimize, maximize, etc.

- is there somewhere a setting?
- is it some desktop effect?
- or is it a bug?

thanks

---

### Post by linomac on 2008-10-07
kwin --replace & disown 
at konsole resolves the problem at least temporarily

---

### Post by dabl on 2008-10-07
In KMenu > System Settings > Advanced > Session Manager there's a Window Manager drop-down toward the bottom -- is that set to "Kwin"?

If you're running Compiz, there were updates last night, and you might need to review your CCSM settings (I haven't checked mine yet today).

---

### Post by linomac on 2008-10-07
yes it it at kwin
what is ccsm?

a permanent solution is to delete all the ~/.kde,
but what about a more elegant solution?
i dont want to loose alll the settings?

in which text file is supposed to be this setting that makes 'no border' for all windows?

thanks

---

### Post by marttali on 2008-10-08
check if you have kwin-kde4 still installed, remove it if it's there, reinstall kwin

---

### Post by linomac on 2008-10-08
no kwin-kde4 was not installed

---

