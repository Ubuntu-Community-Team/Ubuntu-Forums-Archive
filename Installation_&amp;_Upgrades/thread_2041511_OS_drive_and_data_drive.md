---
title: "OS drive and data drive"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by Kaail on 2012-08-12
Is it possible to install games and the like on a separate, larger, hard drive? I ask this because the software centre automatically installs them in /opt and I would preferably like to choose where the games are installed.

---

### Post by Paddy Landau on 2012-08-19
You cannot change where the package manager installs the programs. However, you can change the location of [FONT=Lucida Console]/opt[/FONT] to reside on your larger disk.

I need some more information before I can help you do this.

[LIST]
[*]Where is your larger partition (e.g. [FONT=Lucida Console]/dev/sdb2[/FONT])?
[*]Have you set it to automatically mount at boot (*before* log-in) or not?
[*]How is that partition formatted, e.g. [FONT=Lucida Console]ext3[/FONT]?
[/LIST]

It would help me if you would:

[LIST=1]
[*]Enter the following command in a terminal and paste the results here (between [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT]).```
sudo parted --list
```
[*]Likewise, paste the contents of [FONT=Lucida Console]/etc/fstab[/FONT] here (again, between [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT]). You can find the contents of that file by opening it with your Text Editor.
[/LIST]

Why do you want to change the location of the installed programs, BTW? Applications are not usually large enough in Linux to cause space problems.

---

