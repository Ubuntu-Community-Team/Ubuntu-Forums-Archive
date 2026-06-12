---
title: "[SOLVED] Problems – installation from source code."
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by prabath_fun on 2008-07-21
I got Firefox 3 source code to install. I followed following steps:
1) Extracted tar.bz2 inside a folder  ./prabath. (Did through GUI, by right clicking on firefox-3.0.1.tar.bz2)
2) cd prabath/firefox-3.0.1
3) ./configure
4) sudo make
5) sudo make install.

All above went fine.

Problem: Even after restart, I am getting Firefox 2 beta5 only. 

By same way I tried to install wine0.9.15 from source code. It is not installed. I had seen some where, that wine will be added under application menu list. I have not got it.
Please provide me the solution.



Solution for firefox installation: I tried following link
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
I got it installed and now I am getting Firefox 3.0.1.

---

### Post by Sef on 2008-07-21
Thank you for providing your solution.

---

### Post by prabath_fun on 2008-07-21
I am looking solution for second problem - Wine installation.
Prabath

---

### Post by Sef on 2008-07-21
It is best to place one problem in one thread.  Your WINE question should be put in the WINE forum.

---

### Post by Bachstelze on 2008-07-21
> **Sef said:**
> It is best to place one problem in one thread.  Your WINE question should be put in the WINE forum.

I think it's fine here, as it's not really WINE-specific.


prabath_fun : when you compile a program from source, it will not always be put into your menu. Can you run it from a terminal, like [font="Courier New"]wine /foo/bar.exe[/font] ?

---

### Post by prabath_fun on 2008-07-21
Hi HymnToLife,
   Thanks.
   Really, I am looking for GUI based operation. As, I recently migrated from windows.
  Also, if it is only way to launch the source code installed application through command prompt means, It is not so easy to remember the commands for each application by me.  

I faced same problem with Mplayer source code as well. But, I got it solved by installing .deb package from [www.package.ubuntu.com](www.package.ubuntu.com).

Even, for wine, .deb package is available. But, I want to install it from source code for training purpose to install other application available in source code form only.

So, I am looking for GUI based launcher. Please help me.

---

### Post by Bachstelze on 2008-07-22
Wall, there is no GUI laucher for WINE that I know of. You might be able to define a "Launch with WINE" action for EXE files in your graphical environment, but I can't help you with that (assuming you're running Gnome). The applications you have installed in WINE should show up in your menu, however.

As a side-note, to have mplayer appear in your menu, you must compile it with the GUI enabled (i.e. with the --enable-gui configure option).

---

### Post by prabath_fun on 2008-07-22
Hi,
  Thanks for your reply.
  Please refer the link [http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml](http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml) were wine is in menu and application installed on it.
  I am looking something like this with source code instalation. In above refered webpage, they used .deb package, I believe.

Please clear me.

Prabath

---

### Post by prabath_fun on 2008-12-16
solved by adding list in menu from installed location using "main menu" from system -> preferances.
My understanding is that, If installation is carried out from source code, it will not add link in application menu. 
  I came to know that by installing .deb package will provide link in menu.

---

