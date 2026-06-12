---
title: "Errors while upgrading from 21.04"
date: 2021-10-16
forum: Installation &amp; Upgrades
---

### Post by MrMosier on 2021-10-16
***Title should be: "Errors while upgrading from 21.04"***

My headless Hirsute Hippo install has been running fine (used as a  Folding@Home rig as well as file server). I went to upgrade it to 21.04 (I usually keep it up to date, but had been busy in April), and once it starts trying to download files, it gets a slew of error messages about permissions as it is checking for partial downloads. There are no partial downloads, and the machine is up to date on Hirsute. Any ideas?

---

### Post by Bashing-om on 2021-10-16
MrMosier; Yukkie

Seeing the errors will be most informative :D

Post back the outputs of the terminal commands:
```

sudo apt update
sudo apt full-upgrade
sudo dpkg -C

```
and we see where we go from here.

[INDENT]a line of text beats my crystal ball every time
[/INDENT]

---

### Post by coffeecat on 2021-10-19
> **MrMosier said:**
> ***Title should be: "Errors while upgrading from 21.04"***

@MrMosier, I've corrected the thread title for you.

---

