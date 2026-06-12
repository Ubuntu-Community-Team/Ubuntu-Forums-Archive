---
title: "Lubuntu 13.10 -- Video Mode Problems on Older Laptop"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by ParkerT on 2014-02-26
Version:
     Lubuntu-13.10-alternate-i386
Installing from CD-r

Machine Specs:
     Dell Inspiron 2500
     Pentium III 847.4MHz
     190 SDRAM
     Intel 815EM Chipset

[SIZE=4]When I attempt the install, I am shown:[/SIZE]
[FONT=arial black]
Undefined video mode number: 314
Press <ENTER> to see video modes available, <SPACE> to continue, or wait 30 sec
Mode:  Resolution:   Type:
0 F00      80x25         VGA
1 F01      80x50         VGA
2 F02      80x43         VGA
3 F03      80x28         VGA
4 F05      80x30         VGA
5 F06      80x34         VGA
6 F07      80x60         VGA
Enter a video mode or "scan" to scan for additional modes:

[/FONT][SIZE=4]If I input any of the mode values or "scan" at this point, it sends me to the blinking cursor of death for all eternity.

I have no idea what number it wants, but tweaking the VGA parameter of the command line results in the same screen with [/SIZE][FONT=arial black]Undefined video mode number:[/FONT][SIZE=4] showing a new value. 
[/SIZE]

---

### Post by mörgæs on 2014-02-27
I would say that such hardware is too old to be of any meaningful use, sorry. 

If you want to play with it as a learning experiment I suggest beginning with the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

---

