---
title: "Problem to permit execution of an executable file. Please Suggest Some Idea!!"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by BRizwi on 2010-10-29
I want to install cyberlink power director on ubuntu 10.10. Problem is that when i check the box in the properties of .exe file to make it executable it automatically unchecked in no time. Now what should i do now.

---

### Post by jmacdallas on 2010-10-31
I am experiencing the exact same problem. Any one have ideas?

---

### Post by P4man on 2010-10-31
Its probably on a read only medium like a CD? You could copy the cd contents to your harddrive, or just execute it from a terminal. Open a terminal, browse to your cd folder and run

```
wine ./whateverthenameoftheinstaller.exe
```

I dont think it actually works under wine, but at least you can try.

---

### Post by jmacdallas on 2010-10-31
Nope - mine is on a separate HDD, not mounted in Fstab so I can't imagine that any read only flags were set or something like that.

I also tried running Wine from the command prompt, but the I would like to change other file properties as well. Even emblems, for example, won't take. Literally every property resets itself automatically.

Edit: I'm not trying to run Cyberlink power director, I just have the same problem regarding file properties resetting themselves. And it affects the entire drive - not just the one application.

---

