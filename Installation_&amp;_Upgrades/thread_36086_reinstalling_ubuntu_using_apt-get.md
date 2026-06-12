---
title: "reinstalling ubuntu using apt-get"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by libertymethod on 2005-05-21
After a crash, a few essential system files were corrupted. As a result, my system is a bit messed up. GDM sometimes fails to start, and other miscellaneous errors occur. I think the problem could be fixed if I knew which files needed to be replaced. So my question is, is there any way to use apt-get to reinstall the entire system? I've tried "apt-get --reinstall install packagename" for reinstalling a few particular packages, but I would like to reinstall the entire system. Something like "apt-get --reinstall dist-upgrade" (which, of course, doesn't work). My aim is to force apt to download and replace every package, despite the fact that my system is already up to date. Any ideas would be greatly appreciated.

---

### Post by bored2k on 2005-05-21
[QUOTE=libertymethod]After a crash, a few essential system files were corrupted. As a result, my system is a bit messed up. GDM sometimes fails to start, and other miscellaneous errors occur. I think the problem could be fixed if I knew which files needed to be replaced. So my question is, is there any way to use apt-get to reinstall the entire system? I've tried "apt-get --reinstall install packagename" for reinstalling a few particular packages, but I would like to reinstall the entire system. Something like "apt-get --reinstall dist-upgrade" (which, of course, doesn't work). My aim is to force apt to download and replace every package, despite the fact that my system is already up to date. Any ideas would be greatly appreciated.[/QUOTE]
 Reinstalling ubuntu-desktop and xorg might be good..

---

### Post by libertymethod on 2005-05-21
I did this, sadly to no effect. I really would like to be able to redeploy all the packages somehow. Anyone?

---

### Post by Pitbull11188 on 2005-05-24
You could always reformat. It may not be the best way but it will solve many of your problems. Justcopy down the programs you have and then reinstall them.

---

