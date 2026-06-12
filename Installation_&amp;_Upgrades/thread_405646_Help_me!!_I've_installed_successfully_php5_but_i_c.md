---
title: "Help me!! I've installed successfully php5 but i cannot find where the files resides."
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by jetro2k5 on 2007-04-10
friends,

Good Day to all!!

i've two problem in configuration php, apache, and symfony

1:
I've newly installed apache,php5, and symfony (php framework), im using symfony in windows by importing php.exe file before any command (e.g. D:/php5/php symfony <command>)  which i think same way in Ubuntu, i just needed to know sirs where i can find the php folder and its files.

2:
I doing php script in gedit text editor and i want it to save all my files in /var/www directory. But I cannot create file, save, edit, or delete files and folders in /var/www which is my document root directory.Unless i login as root. All my php files and images must be saved on that directory. 

Sorry im just newbie in Linux
Please help me guys.



If confusion is the first step to knowledge, i must be a genius.
-Larry Leissner

---

### Post by haricharan on 2007-04-10
use gksudo before gedit like ```
gksudo gedit
``` to save in /var/www directory

---

