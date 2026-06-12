---
title: "Black widges in some Qt applications after upgrading to kubuntu 20.04"
date: 2020-05-08
forum: Installation &amp; Upgrades
---

### Post by ranmak on 2020-05-08
After upgrading my kubuntu 19.10 to 20.04, lots of widgets were not rendered in many Qt applications.
Instead of showing icons or pictures, there were just black blocks.
They seem to be Qml based programs.
All problematic applications have this error message:
QSGTextureAtlas: texture atlas allocation failed

I compared the installed packages on my PC with a fresh-installed VM and found the problem might be libqt5quick5.
Replacing libqt5quick5-gles with libqt5quick5 solved my problem.
I hope this helps.

---

