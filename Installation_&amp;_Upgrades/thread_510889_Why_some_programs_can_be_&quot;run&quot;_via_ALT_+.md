---
title: "Why some programs can be &quot;run&quot; via ALT + F2 -- others cannot"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by Average_Joe on 2007-07-27
Hello --

I use i386 Ubuntu 7.04.  The package in question is the popular game Freeciv (Civilization 2 mimic).
I am using the stable version of Freeciv ver. 2.0.9 .

In order to use Freeciv, one first has to install a bunch of Debian libraries.  (I have listed those at bottom.)
Then, you have to " ./configure " and " make " the Freeciv package.

After installation, you can run the game by hitting ALT + F2 and acquire the GUI command line interface.  In this case, you can type "civclient" and the game will fire up.

I've installed Freeciv 4 separate times (with fresh Ubuntu reinstalls each time, as I am experimenting and learning) but only on one occasion have I got that ALT + F2 thing to work.  Grrrrrrrrrr.  The other three times it tells me it can't find the file.  But I *can* play the game even in those cases, I just have to  get the program to run by navigating to the folder in which it is installed, finding the file named "civ" and then right clicking on it to choose "Open" from the context menu.  But that's the only way I can get it to start.  And the game runs fine, I just have to go through all that browsing to make it start. :-(

I really enjoyed (previously) just tapping Alt + F2 and typing civclient and pressing Enter, and vroom I was off to play.

What did I do wrong?  OIr, a different question, since I do have it installed and working fine, what can I do to "tie" the program in to a GUI command line execution?  I'd really appreciate help to make this work again.

The packages I installed on top of virgin Ubuntu 7.04 were:
   libc6-dev
   libreadline5-dev
   zlib1g-dev
   xlib6g-dev_4.1.0-16woody7_all.deb
   gdk-imlib11-dev
   imlib-progs_1.9.14-16.2_i386.deb
   libgtk2.0-dev
And then I "./configure" and "make" the freeciv-2.0.9 package.

THANKS!!!

---

### Post by 505 on 2007-07-27
With the alt+F2 menu you can only run programs that are in your path directories. Other programs cannot be found. The find out what directories that are, type in a terminal 'echo $PATH'.
If you have Freeciv installed in one directory, not included in path, you can either:
1- include that directory in your PATH variable:
```

PATH=$PATH:/dir/to/freeciv
export PATH

```
2- Add a symbolic link to Freeciv in one of the path directories:
```

cd /usr/local/bin
sudo ln -s /path/to/freeciv/freeciv-program

```

---

### Post by sargentdean on 2007-07-27
> **Average_Joe said:**
> Hello --

I use i386 Ubuntu 7.04.  The package in question is the popular game Freeciv (Civilization 2 mimic).
I am using the stable version of Freeciv ver. 2.0.9 .

In order to use Freeciv, one first has to install a bunch of Debian libraries.  (I have listed those at bottom.)
Then, you have to " ./configure " and " make " the Freeciv package.

After installation, you can run the game by hitting ALT + F2 and acquire the GUI command line interface.  In this case, you can type "civclient" and the game will fire up.

I've installed Freeciv 4 separate times (with fresh Ubuntu reinstalls each time, as I am experimenting and learning) but only on one occasion have I got that ALT + F2 thing to work.  Grrrrrrrrrr.  The other three times it tells me it can't find the file.  But I *can* play the game even in those cases, I just have to  get the program to run by navigating to the folder in which it is installed, finding the file named "civ" and then right clicking on it to choose "Open" from the context menu.  But that's the only way I can get it to start.  And the game runs fine, I just have to go through all that browsing to make it start. :-(

I really enjoyed (previously) just tapping Alt + F2 and typing civclient and pressing Enter, and vroom I was off to play.

What did I do wrong?  OIr, a different question, since I do have it installed and working fine, what can I do to "tie" the program in to a GUI command line execution?  I'd really appreciate help to make this work again.

The packages I installed on top of virgin Ubuntu 7.04 were:
   libc6-dev
   libreadline5-dev
   zlib1g-dev
   xlib6g-dev_4.1.0-16woody7_all.deb
   gdk-imlib11-dev
   imlib-progs_1.9.14-16.2_i386.deb
   libgtk2.0-dev
And then I "./configure" and "make" the freeciv-2.0.9 package.

THANKS!!!

You can also create a launcher for your program. That way all you have to do is click on an icon to start the program. 

> To do this right click on the desktop and select create launcher. Then give it a name and browse to the directory where the program is and select the file that runs it. Close the create launcher app and voila your done.

Hope this has helped;

Sarge :cool:

---

