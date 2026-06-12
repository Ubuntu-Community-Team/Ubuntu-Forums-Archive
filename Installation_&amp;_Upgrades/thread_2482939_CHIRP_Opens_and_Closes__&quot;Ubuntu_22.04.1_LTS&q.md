---
title: "CHIRP Opens and Closes  &quot;Ubuntu 22.04.1 LTS&quot;"
date: 2023-01-14
forum: Installation &amp; Upgrades
---

### Post by Billisnice on 2023-01-14
Ham Radio CHRIP 

When I open it closes on its own. Any solutions?

---

### Post by MAFoElffen on 2023-01-14
Are you saying when you open the CHIRP application, that the program crashes and closes? Or that the OS crashes and shuts down?

---

### Post by MAFoElffen on 2023-01-14
Do you have a working serial port device?
```

grep -i 'ttyS' /var/log/dmesg

```
> This is the official PPA archive for the CHIRP project.

 READ THIS: [COLOR=#ff0000]If you are on 20.04 Focal or later,[/COLOR] Ubuntu has removed  some packages that are required for CHIRP to run. Most of them are  available in another PPA, located here:

   [https://launchpad.net/~nrbrtx/+archive/ubuntu/python2-stuff](https://launchpad.net/~nrbrtx/+archive/ubuntu/python2-stuff)


If from PPA, Are all the packages installed? Which begs to ask how it is installed from which form? The app is available from many sources, and different formats... From the main project (Downloaded), Ubuntu PPA, Snap, Flatpak...

---

### Post by Billisnice on 2023-01-14
When I open the program crashes and closes

---

### Post by Billisnice on 2023-01-14
Yes Serial port works.

---

