---
title: "How to install a program package ?"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by AlexeySol on 2011-07-26
Hello, 

I know how to use the Software Center, and it's great. 

But the program I wanted to install now is not available via this tool, unfortunately. 

It's AVIRA AntiVir Personal -  Free *Antivirus* für *Linux* 3.1.3.5, freeware for personal use. 

I downloaded the package (gz archive), but I don't know how to get the program to install.
 
There is a large install text file within the archive, but clicking on "Execute" does not execute anything, apparently. 

I hope you can help me, I got a multiboot installation (Windows x86,  Windows x64 and Ubuntu x64) and want to scan my Windows drives for  virusses with Ubuntu !   :sad:

---

### Post by lisati on 2011-07-26
> **AlexeySol said:**
> 
 
There is a large install text file within the archive, but clicking on "Execute" does not execute anything, apparently. 


Is the "install" file a text file with instructions?

---

### Post by AlexeySol on 2011-07-26
> **lisati said:**
> Is the "install" file a text file with instructions?

No, it contains many many pages of computer code. I  tried to copy it and paste it into the Terminal, but nothing happens after pasting it there and clicking Enter.

---

### Post by AlexeySol on 2011-07-26
It's the program you can download here, from the site of CHIP, a German computer magazine: 

[http://www.chip.de/downloads/AntiVir-Personal-Free-Antivirus-fuer-Linux_23188958.html](http://www.chip.de/downloads/AntiVir-Personal-Free-Antivirus-fuer-Linux_23188958.html)

I don't understand why it's not available via the Software Center, since it's a very popular and freeware program.

---

### Post by pommie on 2011-07-26
There is a file called README in the folder, in that text it states,

install           <- install script

simply double click the "install" file and "Run in Terminal" if that doesn't work then you will have to open a terminal, navigate your way into the folder and run it from there.

Should be ....  sh ./install

If that command is wrong someone will correct me fairly quickly, I didn't try it as I do not want to install it.

Cheers David

Edit:- It will never be in the repo's, its not foss, also if you do read the license agreement it is very restrictive in its use, so while it is free to use its not free in the Linux sense (foss).

---

### Post by AlexeySol on 2011-07-26
When I click on it and chose "Run in Terminal", the Terminal pops up for a split-second and closes right down again. Nothing else happens. Program does not install ! :(

---

### Post by fdrake on 2011-07-26
> **AlexeySol said:**
> When I click on it and chose "Run in Terminal", the Terminal pops up for a split-second and closes right down again. Nothing else happens. Program does not install ! :(

open the terminal in the same directory(right click and open terminal), and type:

```

sh ./install

```
post here the output

---

