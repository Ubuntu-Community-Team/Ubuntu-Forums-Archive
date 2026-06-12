---
title: "UBUNTU 17.10 cannot enter admin password in popup"
date: 2017-11-13
forum: Installation &amp; Upgrades
---

### Post by IRONMAN28 on 2017-11-13
after typing "gksu nautilus", unable to type Admin password in resulting popup
all typing goes to terminal window

(screenshot included)

[ATTACH=CONFIG]277518[/ATTACH]

---

### Post by ajgreeny on 2017-11-13
Are you using a wayland session?  You may find that logging into an xorg session allows that to work again.

There is a similar problem using synaptic package manager in wayland which can be solved by adding the command ```
xhost +si:localuser:root
``` to your startup applications; you can just add that command in the box and name the addition as you wish.

[https://ubuntuforums.org/showthread.php?t=2367294](https://ubuntuforums.org/showthread.php?t=2367294)

---

