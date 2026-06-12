---
title: "install picasa 3.6 in 9.10"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by gregpo on 2010-07-01
tryed to install picasa 3.6 4different times the final was using tweak5.41 &the windows version read about it a help forum still did/nt work I/ve got picasa3 allready  but it is all grey tryed to update but nothing anyone give me a way to install it please

---

### Post by meoconvn38 on 2010-07-01
This one worked fine for me 

[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)
:popcorn:

---

### Post by oldfred on 2010-07-01
[http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019)    [LEFT][http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html](http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html)[/LEFT]
   
   


From my history:

114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
    [LEFT]  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/LEFT]
    [LEFT]  116  sudo chmod 777 winetricks[/LEFT]
    [LEFT]  117  sudo apt-get install cabextract wine wine-gecko[/LEFT]
    [LEFT]  118  winetricks allfonts fontsmooth-rgb gecko allfonts[/LEFT]
    [LEFT]Then download picasa for windows and move into .wine programs and install.
 ([http://dl.google.com/picasa/picasa36-setup.exe]("http://dl.google.com/picasa/picasa35-setup.exe"))
 run it, and the installer should start.[/LEFT]
    [LEFT]
[/LEFT]
    [LEFT][/LEFT]

---

