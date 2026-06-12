---
title: "Can't Install any Packages from UBUNTU Software Center...!"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by Its_Rishi on 2011-01-07
[SIZE="2"]*I can't able to install any software from the ubuntu software center even i download the packages from online i can't able to install them, there it shows the [COLOR="Red"]following error[/COLOR].*[/SIZE]


[B][SIZE="4"][COLOR="Magenta"]Failed to lock the package manager

Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.[/COLOR][/SIZE][/B]
**[SIZE="4"][COLOR="DarkRed"]Details: The package indexes are currently changed by apt-get.[/COLOR][/SIZE]**

[COLOR="DimGray"][SIZE="3"]Can i install "tar.gz" for ubuntu...?[/SIZE][/COLOR]

---

### Post by tekkidd on 2011-01-07
The error means you are running another package manager (eg. synaptic, update manager).

Try: ```
sudo killall synaptic
``` and ```
sudo killall update-manager
```

If that does not work then try restarting the computer and turning off automatic updates if they are turned on.

---

### Post by Its_Rishi on 2011-01-07
Thank You!!!

---

