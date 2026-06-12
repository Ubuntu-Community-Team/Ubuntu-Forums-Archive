---
title: "upgrading to kubuntu from ubuntu."
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by smitty423 on 2007-01-22
[FONT="Georgia"][SIZE="3"][COLOR="Navy"][/COLOR][/SIZE][/FONT] i just got my kubuntu disk and currently running Ubuntu on a duel partition with vista can i install kubuntu over the old Ubuntu os without removing the other or will it rewrite over it?:guitar:

---

### Post by atoponce on 2007-01-22
You don't need the cd.  Pull up a terminal and type:

```
sudo aptitude install kubuntu-desktop
```

---

### Post by smitty423 on 2007-01-22
> **atoponce said:**
> You don't need the cd.  Pull up a terminal and type:

```
sudo aptitude install kubuntu-desktop
```[FONT="Georgia"][SIZE="3"][COLOR="Sienna"][/COLOR][/SIZE][/FONT]
i didn't know that it would be that simple to do i thought i need the disk? that's for the info.....=D>

---

### Post by Pobega on 2007-01-22
You also may want to remove the ubuntu-desktop metapackage, if you're interested in saving HDD space.

---

### Post by atoponce on 2007-01-23
> **Pobega said:**
> You also may want to remove the ubuntu-desktop metapackage, if you're interested in saving HDD space.  Ahh, but when upgrading between Dapper and Edgy, I needed it, otherwise, X broke.  Besides, how much space do you gain by removing the ubuntu-desktop meta package?

---

### Post by linear on 2007-01-23
> **atoponce said:**
> Besides, how much space do you gain by removing the ubuntu-desktop meta package?

Very little, I should think - as a metapackage, it doesn't really contain anything.

---

