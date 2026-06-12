---
title: "DVD drive does not open"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by Ubu_Fester on 2010-02-13
I have a new PC build with a fresh install of Ubuntu 9.10.  

I can open up the DVD drive to insert a DVD.  However, the DVD button does not work when I need to eject.  I need to eject through software.  

Thanks in advance.

---

### Post by moongia on 2010-02-13
I have the same problem,i just go to places>home,from there i just hit the unmount button next to the cd or dvd i have in..That's the only way i know how to get it out..

---

### Post by Rhubarb on 2010-02-13
try using the **eject** command in the terminal.
```
eject
```

If that doesn't work, sometimes having root privilege forces it to eject:
```
sudo eject
```
Note, if you run sudo, you'll be prompted for your password, enter this in and it should eject for you.

---

### Post by Satoru-san on 2010-02-14
drive has to be UNmounted to remove the disk, this is the same for every linux out there.

```
sudo umount -f /dev/sr0
```

---

### Post by Larsm1980 on 2010-02-15
> **Satoru-san said:**
> drive has to be UNmounted to remove the disk, this is the same for every linux out there.

```
sudo umount -f /dev/sr0
```

Or just rightclick the ikon on the desktop that aperd when you put the dvd drive in. and press unmount from the menu :)

---

### Post by jblinux on 2010-02-16
The funny thing is, the eject button worked just fine in 9.04.  It didn't stop working until I upgraded to 9.10!  Now, after watching a movie, neither of my DVD drives will open w/ the eject button.  Seems to be a glitch in 9.10.  Also, when I put in a movie in 9.04 (or earlier), the title would show up on the desktop as an icon (as mentioned above).  Now in 9.10, it no longer does, so there's no icon to right click for a menu!

---

### Post by Ubu_Fester on 2011-01-29
I upgraded to 10.10 and it works again.

---

