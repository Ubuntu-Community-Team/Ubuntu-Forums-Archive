---
title: "Few problems"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by heartwarmer on 2009-04-03
hello people
I'm having some problems:
**1.** my wireless disconnects and reconnects every 10-20 minutes,my card is intel 3945
**2.** i dual boot with 8.10, and when i'm on it,it cant mount the ext4 drive,its not supported.
**3.** in my brothers pc, he has geforce 6150 card, with 180.44 driver, he used to set the screen to 75 refresh rate, but since 180.37(i think) he has only one option -> 60.

---

### Post by hyl4me on 2009-04-03
Try to run update. There have been well over 200 updates since the release of beta 9.04

```
 sudo apt-get update 
```

> **heartwarmer said:**
> hello people
I'm having some problems:
**2.** i dual boot with 8.10, and when i'm on it,it cant mount the ext4 drive,its not supported.


You need kernel 2.6.28 or later to read ext4.  I think 8.10 uses 2.6.27

To see your kernel your running
```
 uname -r 
```

---

### Post by heartwarmer on 2009-04-04
i have all the updates installed, and i know that ext4 was produced
in .28 but i thought they would add support for reading it to older
kernels :)

---

### Post by phenest on 2009-04-04
> **heartwarmer said:**
> **3.** in my brothers pc, he has geforce 6150 card, with 180.44 driver, he used to set the screen to 75 refresh rate, but since 180.37(i think) he has only one option -> 60.

Where does it say that? System > Preferences > Screen Resolution? If so, I wouldn't worry, because it sometimes gets it wrong. Try using System > Administration > NVIDIA X Server Settings instead.

---

