---
title: "I can't update from 6.06 to 6.10"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by lordvolo on 2007-12-16
the update manager tstarts to download the update tool, it works for a bit the says it failed to fetch some thing from medibuntu

---

### Post by PmDematagoda on 2007-12-16
Please disable all third-party repositories before carrying out an upgrade. Open the sources.list for editing using:-

```
sudo gedit /etc/apt/sources.list
```

Then uncomment the Medibuntu addresses and any others **except for the Ubuntu ones** by typing # in front of them.

Once you have edited the sources.list file, save it and do:-
```

sudo apt-get update
```

After that is done you can try upgrading Ubuntu again.

---

### Post by lordvolo on 2007-12-16
the terminal tells me that gedit is not a command

---

### Post by Partyboi2 on 2007-12-16
> **lordvolo said:**
> the terminal tells me that gedit is not a command
ubuntu  text editor = gedit
kubuntu text editor = kate
xubuntu text editor = mousepad
 
So if you are using kubuntu you would do this:
```
gksudo kate /etc/apt/sources.list
``` or you can use nano

```
nano /etc/apt/sources.list
```

---

