---
title: "Plymouth Update/FSCK problem on Aspire One netbook"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by teejay17 on 2010-04-06
I updated Lucid last night. This morning, when I rebooted, it started doing a FSCK check in the Plymouth screen and it seems to have entered a never ending loop, going up to 3% over and over and over again *ad infinitum*. Pressing C does not stop it. Pressing Esc. only freezes it. 
This is on an Acer Aspire 1, with 10" screen and a 160 gig hard drive. 
I'm not the best beta tester as I don't have any formal education in computers; I won't be able to answer all the technical details. 
Nonetheless, this seems like a pretty worthwhile bug.
My other test machine, on the other hand, an older T41 Thinkpad, did not suffer the same fate with this update so it might be hardware specific. 
I have reformatted the netbook and will wait until the official release of Lucid Lynx before reinstalling.

---

### Post by VMC on 2010-04-06
[http://ubuntuforums.org/showthread.php?t=1444879](http://ubuntuforums.org/showthread.php?t=1444879)

---

### Post by teejay17 on 2010-04-06
> **VMC said:**
> [http://ubuntuforums.org/showthread.php?t=1444879](http://ubuntuforums.org/showthread.php?t=1444879)
So does this mean it will be fixed before the official launch? I won't be able to install Lucid Lynx if not.

---

### Post by VMC on 2010-04-06
> **teejay17 said:**
> So does this mean it will be fixed before the official launch? I won't be able to install Lucid Lynx if not.

Try booting from livecd and from a terminal type(replace ? with you install)

```
sudo fsck /dev/sda?
```

for the installed os.

---

### Post by teejay17 on 2010-04-06
> **VMC said:**
> Try booting from livecd and from a terminal type(replace ? with you install)

```
sudo fsck /dev/sda?
```for the installed os.
I already wiped the drive and reinstalled Windows. I won't reinstall Lucid until that FSCK bug is fixed...I was so disappointed when Lucid crashed and burned.

---

