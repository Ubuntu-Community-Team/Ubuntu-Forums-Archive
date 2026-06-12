---
title: "Reading Package Error"
date: 2022-11-17
forum: Installation &amp; Upgrades
---

### Post by jeff742 on 2022-11-17
I have seen this closed before but I'm Still having massive issues with this problem.

I'm getting a Reading Package Error when I'm either Updating or trying to upgrade.  I have done all the forums helps but I'm hitting a brick wall.  Any help would be greatly accepted.

Reading package list... Error!
[COLOR=#ff0000]E[/COLOR]: Read Error - read (21: Is a Directory)
[COLOR=#ff0000]E: [/COLOR]The package lists or status fle could not be parsed or open.

Also I'm running Ubuntu 22.04.1 LTS with Gnome 42.4

---

### Post by ajgreeny on 2022-11-18
Please open a terminal and run command
```
sudo apt update && apt list --upgradable
```
Then copy the full terminal output back here using code tags.
There is a **How to** for code tags in my signature below.

---

