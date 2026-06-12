---
title: "problem installing limewire"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by white pony on 2008-08-23
i tried to install Limewire and the first time the installer froze so i rebooted my comp. then the second time i tried to install i keep getting this message "only one software management tool is allowed to run at a time." there are no other programs running on my comp when this happens. help please.

---

### Post by Partyboi2 on 2008-08-23
Open up System Monitor (System>Admin>System Monitor) and check if any package manager is running. If there is right click on it and choose to kill process.

---

### Post by white pony on 2008-08-23
theres no package managers running. turns out i cant install anything. it brings up the same error every time.

---

### Post by Partyboi2 on 2008-08-23
Ok, try removing the lock file, open a terminal (Applications>Accessories>Terminal) and type[FONT=monospace]
[/FONT]```
sudo rm  /var/lib/dpkg/lock
```

---

### Post by white pony on 2008-08-23
i entered the code, but i still get the same error. If it is any consolation, the installer was stopped while doing something with java.

---

### Post by Partyboi2 on 2008-08-23
ok try
```
sudo dpkg --configure -a
```

---

### Post by white pony on 2008-08-23
i don't know if it is supposed to do this, but the terminal is taking a very long time to execute the command you specified. It is saying "Setting up java-common (0.28ubuntu3) ..." and not doing anything else.

---

### Post by white pony on 2008-08-23
it took a while but it works now. thank you.

---

