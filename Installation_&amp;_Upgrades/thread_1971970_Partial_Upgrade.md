---
title: "Partial Upgrade"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by angus1964 on 2012-05-03
During upgrade from 11.10 to 12.04 my computer crashed. upon restart it now boots into 12.04 but regularly comes up with internal errors. When i run update manager it says their are updates to install but when i click to install a box appears telling me i cant upgrade from oneric to pangolin using this tool. How do i complete the installation?

---

### Post by plucky on 2012-05-03
> **angus1964 said:**
> During upgrade from 11.10 to 12.04 my computer crashed. upon restart it now boots into 12.04 but regularly comes up with internal errors. When i run update manager it says their are updates to install but when i click to install a box appears telling me i cant upgrade from oneric to pangolin using this tool. How do i complete the installation?

Try from a terminal ```
sudo dpkg --configure -a
``` and see if the release upgrade starts again.

Good luck

---

### Post by Balajoe on 2012-05-03
> **plucky said:**
> Try from a terminal ```
sudo dpkg --configure -a
``` and see if the release upgrade starts again.

Good luck

I am having the same problem and I tried to run "sudo dpkg --configure -a" but the recurring problem I am getting is a broken postgresql 8.2 package (see [http://ubuntuforums.org/showthread.php?t=1971888](http://ubuntuforums.org/showthread.php?t=1971888)). It is also giving me option to partial upgrade but when I tried to run the update, I am getting same errors and the update manager exits without any updates

Any way to resolve the postgresql issue which I think not allowing me to fully upgrade to 12.04?

---

### Post by angus1964 on 2012-05-03
I tried that code from a terminal but after putting in my password it went back to a prompt and nothing happened.

---

### Post by plucky on 2012-05-03
> **angus1964 said:**
> I tried that code from a terminal but after putting in my password it went back to a prompt and nothing happened.

That means it didn't find anything to do.

What happens if you run ```
update-manager -d
``` from a terminal?

Does it offer you the Release upgrade?

---

### Post by angus1964 on 2012-05-04
I putin.
```
update-manager -d
```

Exactly the same as my original post happened.

---

### Post by plucky on 2012-05-04
> **angus1964 said:**
> I putin.
```
update-manager -d
```

Exactly the same as my original post happened.

I would seriously consider doing a clean install of 12.04 instead of trying to fix this install.Would save a lot of time.


Good Luck

---

