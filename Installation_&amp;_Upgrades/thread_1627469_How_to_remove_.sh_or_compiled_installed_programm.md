---
title: "How to remove .sh or compiled installed programm?"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by Kangarooo on 2010-11-21
How to remove/purge completly game UltimateStunts ?

Installed Car game ultimatestunts in [http://www.ultimatestunts.nl/index.php?page=2&lang=en](http://www.ultimatestunts.nl/index.php?page=2&lang=en) is written to compile. So since its already installed im downloading Source code with data files (16.0MB) and reading [http://www.ultimatestunts.nl/documentation/en/compile.htm](http://www.ultimatestunts.nl/documentation/en/compile.htm)
untarred tar file
cd to untared folder
./configure without sudo
make without sudo
make uninstall and make remove didnt removed ustunts programm
in INSTALL file is written
  4. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  
but that also didnt removed ustunts programm.
Its not removed couse i can still in terminal write ustunts and in Applications - Games theres still its icon and game can still be opened..

---

### Post by dFlyer on 2010-11-21
If you compiled and installed a game from source you need to manually remove the program from your computer. If I under stand you correctly you install the program in your home folder. In that case just delete the directory and than edit your menu and remove the icon reference from games menu.

---

### Post by Kangarooo on 2010-11-21
Ok in /usr/share/Applications icon Ultimate stunts has:
> 
[Desktop Entry]
Name=Ultimate Stunts
Comment=Ultimate Stunts is a remake of the famous DOS-game stunts.
Exec=ustunts
Icon=/usr/local/share/ultimatestunts/ultimatestunts.png
Terminal=false
Type=Application
Categories=Application;Game;

and
> $ whereis ustunts
ustunts: /usr/local/bin/ustunts
So i can just delete Icon & Desktop Entry
but whole programm how?
> :/usr/local/bin$ ls
ustunts  ustunts3dedit  ustuntsai  ustuntsserver  ustuntstrackedit
So i just need to only to remove all theese files? Will that solve all? Couse they just 16mb..

---

### Post by oldos2er on 2010-11-21
Deletia.

---

