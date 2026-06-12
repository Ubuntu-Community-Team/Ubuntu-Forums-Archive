---
title: "About suspend/hibernate.."
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2010-03-12
I tested using sleep/hibernate in gnome menu and indicator power management menu, on my thinkpad, the screen locks, apparently it tried to hibernate, somehow fails.

Then, I tried this:

> 
sudo su
echo mem > /sys/power/state
and the laptop slept in 2 secs, wake up also works..

maybe its a temporary work arround for those "who can't sleep properly" like myself.:popcorn:
so heres the commands:

minimum power saving, fastest resuming:
```

echo standby > /sys/power/state

```
or
save state to memory, medium power saving, medium resume:
```

echo mem > /sys/power/state

```
or
save to disk, shuts down:
```

echo disk > /sys/power/state

```

---

### Post by handaxe on 2010-03-12
> **Vanishing said:**
> save to disk, shuts down:
```

echo mem > /sys/power/state

```

You meant: ```
echo disk > /sys/power/state
```

---

### Post by Vanishing on 2010-03-12
> **handaxe said:**
> You meant: ```
echo disk > /sys/power/state
```

right...my bad..:p

---

