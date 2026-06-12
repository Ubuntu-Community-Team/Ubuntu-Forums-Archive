---
title: "Ubuntu doesn't Recognize Windows Partion"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Sonicrulz12 on 2011-10-14
When trying to install Ubuntu 11.10, it does  not give me the option to install side by side with windows 8, so i'm guessing Ubuntu doesn't recognize the NTFS windows partion?
:confused::confused::confused::(:(:(

---

### Post by Sonicrulz12 on 2011-10-14
can anybody help me

---

### Post by Hakunka-Matata on 2011-10-14
Can you run Ubuntu off the Install/liveCD?  If so use Ubuntu's gparted program to examine your hard discs>

---

### Post by Sonicrulz12 on 2011-10-14
okay

---

### Post by Sonicrulz12 on 2011-10-14
okay i am at gparted

---

### Post by Sonicrulz12 on 2011-10-14
[FONT=Comic Sans MS]???????[/FONT]

---

### Post by vasa1 on 2011-10-14
> **Sonicrulz12 said:**
> [FONT=Comic Sans MS]???????[/FONT]

Guess the experts are busy (or at the cafe)!

Before using gparted, you should do a couple of sudos and paste the output information here between code tags:
So, while using the LiveCD, press ctrl+alt+T together to bring up the terminal window and type:
```
sudo fdisk -l
```
You'll be asked to provide your password. Do so and hit enter. You won't see anything on the screen while typing your password, but hit enter in any case.
Then use the mouse to copy the output and paste it here between code tags.
Repeat as above:
```
sudo parted -l
```

---

### Post by Sonicrulz12 on 2011-10-16
well actually i already installed ubuntu by shrinking the windows partion but thanks anyways

---

