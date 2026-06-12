---
title: "Update Manager broken"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by Qwertinsky on 2007-10-06
I somehow broke the update manager in Ubntu 6.06

When I launch it I get a mesage that says:

[COLOR="SandyBrown"]Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.
[/COLOR]
But nothing else is running, even right after a fresh reboot I get this message.

---

### Post by MrFSL on 2007-10-07
Close everything and try:

```
sudo apt-get update
```

Check for errors and directions at the end.

---

### Post by taurus on 2007-10-07
> **Qwertinsky said:**
> I somehow broke the update manager in Ubntu 6.06

When I launch it I get a mesage that says:

[COLOR="SandyBrown"]Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.
[/COLOR]
But nothing else is running, even right after a fresh reboot I get this message.

Then post the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by 1/0 on 2007-11-14
Try:

```

sudo dpkg --configure -a
sudo apt-get update

```

---

