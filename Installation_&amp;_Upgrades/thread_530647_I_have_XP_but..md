---
title: "I have XP but."
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by jstnwht on 2007-08-20
Ok I have Microsoft Windows XP. But i want this OS it looks cool, is it possible for me to have both on same PC? If it is please let me know how!! THANKS!

---

### Post by Patrick793 on 2007-08-20
Yes. You can. You will have to partion the hard drive though, which would maybe mess up your computer. Or, you could use [Wubi]("http://wubi-installer.org"). Wubi will just make some virtual hard drives in C:\Wubi (or where ever your hard disk is) and edit boot.ini and add Wubi Ubuntu to the list. Then you can choose between Windows, and Ubuntu.

---

### Post by Pumalite on 2007-08-20
Sure. If one hard drive: defrag XP several times, erase temp files, then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to partition your hard drive and install. If you install Grub to MBR (default) it will give you a menu to boot both.

---

### Post by merlinus on 2007-08-20
Read this:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

-merlin

---

