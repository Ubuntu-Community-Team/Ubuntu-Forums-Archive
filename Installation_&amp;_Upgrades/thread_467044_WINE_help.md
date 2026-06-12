---
title: "WINE help"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by arisejesus on 2007-06-07
i know Microsoft Office is not free neither is it openSource but i need it because i will be representing school on a competition that requires Microsft Power Point, I installer PP in my linux (Ubuntu 7.04) through WINE but i dun know where to start PP. can anyone help me? am still new to linux and thus new to WINE too.

---

### Post by Suthern on 2007-06-07
If you hit the 'programs' button at the top left is there a 'Wine' menu? It should be in there.

If not, you may have to go searching in your home directory. You may find it in \home\$user\.wine\c_drive\Program Files\Microsoft Office\Office 10 (That's where my 2002 version would be).

Once you know where it is, open a terminal window and type in ```
wine "~\.wine\c_drive\Program Files\ ..etc"
```
Does that help?

---

### Post by arisejesus on 2007-06-07
how do ur install ur wine? i mean configurate, i dun see any folder called wine in my /home/$user

---

### Post by TravMan63 on 2007-06-12
The config file is in usr/bin (winecfg)
the programs you install (i.e. powerpoint) will be in the /home/username/.wine (sub)folder(s) (note the '.' - and in my file manager - I had to enable 'show hidden files')

If the file does not show in the menu - then you will need to create a launcher for it (or use terminal to launch it)
 
I installedd ppt by using wine file - from the same /usr/bin directory.
It then placed a shortcut/launcher in my menu - under 'other' (I am using xubuntu)

also see
[http://ubuntuforums.org/showthread.php?t=467631](http://ubuntuforums.org/showthread.php?t=467631)
[http://ubuntuforums.org/showthread.php?t=459832](http://ubuntuforums.org/showthread.php?t=459832)
[http://ubuntuforums.org/showthread.php?t=470842](http://ubuntuforums.org/showthread.php?t=470842)

hth
TM

---

### Post by Zenerek on 2007-06-12
First off, does not open office support powerpoint files?if so why not use that?

To know if wine is installed go into a terminal and use this command and note that actual command is called "type"    

type wine

it should give you the path to it's installation(meaning it's installed)

TravMan63 is correct, the folder where the windows programs are placed for wine to use are in .wine in your home folder, hit ctrl+h to view hidden files 

oh and there are two ways to type the path of files but.....it seems i've forgotten how hard it is to manually type in paths for wine....it needs some special syntaxing for spacing....sigh

easy way to start winapp with wine,right click on it and pick start with wine

---

### Post by Pumalite on 2007-06-12
> **Zenerek said:**
> First off, does not open office support powerpoint files?if so why not use that?

To know if wine is installed go into a terminal and use this command and note that actual command is called "type"    

type wine

it should give you the path to it's installation(meaning it's installed)

TravMan63 is correct, the folder where the windows programs are placed for wine to use are in .wine in your home folder, hit ctrl+h to view hidden files 

oh and there are two ways to type the path of files but.....it seems i've forgotten how hard it is to manually type in paths for wine....it needs some special syntaxing for spacing....sigh

easy way to start winapp with wine,right click on it and pick start with wine

Install wine with synaptic, then try this:

pumalite@pumalite-desktop:~$ winecfg
wine: creating configuration directory '/home/pumalite/.wine'...
wine: '/home/pumalite/.wine' created successfully.
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
pumalite@pumalite-desktop:~$

---

### Post by gimmy_bond on 2007-06-12
OpenOffice/ Impress which you already have on your drive, does exactly what MS PP does and it is fully compatible with PP. Here is the link to learn more.

[Why OpenOffice?](http://why.openoffice.org/why_great.html)

---

### Post by TravMan63 on 2007-06-12
> **gimmy_bond said:**
> OpenOffice/ Impress which you already have on your drive, does exactly what MS PP does and it is fully compatible with PP. Here is the link to learn more.

[Why OpenOffice?](http://why.openoffice.org/why_great.html)


Well, it's close, but not 'exact' or 'fully' (but it is free)
For example - opening powerpoint files with embedded sounds won't play without editing the file.
Media playback is quite jerky (on slower machines) (tested on 700mhz PIII)
Some media files (mpg, wmv) will only playback about 6 seconds of some files...

I'm using Office Small Business 2003 - and powerpoint runs much faster with transitions, text animation etc...
... if I can just get it to play/load mpgs and wmv's I'll be happy...  (this is the main purpose of this machine - showing presentations created in powerpoint - with heavy media content)

TM
---- edit
see this post for more info on installing office apps:
[http://ubuntuforums.org/showthread.php?t=470842](http://ubuntuforums.org/showthread.php?t=470842)

---

