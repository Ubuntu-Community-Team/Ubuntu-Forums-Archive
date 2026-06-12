---
title: "&quot;Open with jEdit&quot; still bad in Nautilus"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2012-04-30
The Nautilus script packaged with jEdit in 12.04 still has the problem that opening a file in jEdit from the Nautilus right-click menu doesn't reuse the existing jEdit window if already running. This stupid behaviour has now persisted through several Ubuntu versions. Installing jEdit using the deb file available from the jedit.org web site changes the behaviour to be correct, and has always done so.

---

### Post by rijidij on 2012-12-14
I had this problem too when I installed the mighty jEdit from the Software Centre.
It is easily fixed by (sudo) editing the [FONT="Courier New"]/usr/share/applications/jedit.desktop[/FONT] file.
Just add the -reuseview parameter to the Exec line like so:
```
Exec=jedit -reuseview %U
```
Save the file and everything should be shiny..

---

