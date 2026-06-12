---
title: "Uninstalled Python package, reinstalled with pip, and now cannot upgrade computer"
date: 2018-05-28
forum: Installation &amp; Upgrades
---

### Post by raequin on 2018-05-28
In order to address a problem with ROS, I uninstalled pyassimp via

```
sudo dpkg --remove --force-depends python-pyassimp
```

and installed it with pip using

```
sudo pip install pyassimp
```

That works for my problem with ROS but now sudo apt upgrade yields

```
The following packages have unmet dependencies: ros-kinetic-moveit-commander : Depends: python-pyassimp but it is not installed

E: Unmet dependencies. Try using -f.
```

Please tell me what I should do to fix this.

---

### Post by raequin on 2018-05-29
ROS still works after using the "-f" option with apt.  Computer upgraded fine via

```
sudo apt -f dist-upgrade
```

---

