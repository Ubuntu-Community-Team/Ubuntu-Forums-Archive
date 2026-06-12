---
title: "Cannot install anything due to dpkg error"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by nivekyru on 2008-07-05
whenever i try to install anything on Ubuntu 8.04 i get this error

dpkg: parse error, in file `/var/lib/dpkg/status' near line 26071 package `ekiga':
 `Depends' field, reference to `libice6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

thank you, help would be very much appreciated

---

### Post by Tanker Bob on 2008-07-05
It sounds like libice6 didn't install correctly or was corrupted. You could try:

```
sudo aptitude reinstall libice6
```

That will cleanup any libice6 library and dependency issues.

---

### Post by arashiko28 on 2008-07-05
try > dpkg --configure -a

---

### Post by avtolle on 2008-07-05
That should be```
sudo dpkg --configure -a
```

---

### Post by nivekyru on 2008-07-07
Thank you; Tanker Bob, arashiko28, avtolle. i've tried the possible solutions you have recommended, i get the same error. is there a way i can do a "system restore" like operation?

---

### Post by Frak on 2008-07-07
Try

```
sudo apt-get install -f
```

That *should *fix your issues.

---

### Post by nivekyru on 2008-07-07
unfortunately, that too i have now tried, my system is still giving me this error

kevin@kevin-desktop:~$ sudo apt-get install -f
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/status' near line 26071 package `ekiga':
 `Depends' field, reference to `libice6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
kevin@kevin-desktop:~$

---

### Post by Partyboi2 on 2008-07-07
> **nivekyru said:**
> unfortunately, that too i have now tried, my system is still giving me this error

kevin@kevin-desktop:~$ sudo apt-get install -f
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/status' near line 26071 package `ekiga':
 `Depends' field, reference to `libice6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
kevin@kevin-desktop:~$
Another option could be to replace /var/lib/dpkg/status with /var/lib/dpkg/status-old
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-broke
```
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
```

---

### Post by Tanker Bob on 2008-07-07
Based on your error, here's another thing to try:

```
sudo apt-get uninstall ekiga
sudo apt-get install ekiga
```

Sounds like that package is causing the issue. If you don't mind losing your VOIP settings, you could try:

```
sudo apt-get purge ekiga
sudo apt-get install ekiga
```

If that doesn't work, you could try:

```
sudo apt-get uninstall ekiga libice6
sudo apt-get install ekiga libice6
```

These may work with minimum collateral damage.

---

### Post by nivekyru on 2008-07-08
tried the three methods you gave, Tanker Bob. they are yet to resolve my problem, i get the same error as before

---

### Post by Tanker Bob on 2008-07-08
Sorry about that. Paryboi2's suggestion is a good next move. I can't think of any other limited-effect approaches. You've tried all the easy fixes of which I can think at the moment.

---

