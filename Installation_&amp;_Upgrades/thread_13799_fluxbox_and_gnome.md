---
title: "fluxbox and gnome?"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by Josh101 on 2005-02-02
How do i get ubuntu to boot fluxbox automatically/at all ?

---

### Post by Sepero on 2005-02-02
If it doesn't exist, create the file "~/.xinitrc". Add this to end of that file:
exec fluxbox


If for some strange reason that doesn't work, try the full path:
exec /usr/bin/fluxbox

---

### Post by Josh101 on 2005-02-03
That works, it allows me to startx manually start it but how do i make it appear in the gdm menu the fluxbox documentation describes doing using a file which doesnt exsist :(

---

### Post by dusu on 2005-02-03
By doing apt-get install fluxbox, the fluxbox menu in gdm should appear.
If not can you check whether or not the file 
/usr/share/xsessions/fluxbox.desktop
exists ?

---

### Post by Sepero on 2005-02-03
Sorry, I didn't know that GDM would stop you. (I don't login with gdm. Using commandline helps scare little kids away from my pc. ;))

I did a little digging for you and found out what you should do. First, create the file "/etc/gdm/Sessions/fluxbox", then put this in the file:```
#!/bin/sh
#
# /etc/gdm/Sessions/fluxbox
#
# global fluxbox session file -- used by gdm

exec /etc/X11/Xsession /usr/bin/fluxbox
```

---

### Post by Josh101 on 2005-02-04
[QUOTE=Sepero]Sorry, I didn't know that GDM would stop you. (I don't login with gdm. Using commandline helps scare little kids away from my pc. ;))

I did a little digging for you and found out what you should do. First, create the file "/etc/gdm/Sessions/fluxbox", then put this in the file:```
#!/bin/sh
#
# /etc/gdm/Sessions/fluxbox
#
# global fluxbox session file -- used by gdm

exec /etc/X11/Xsession /usr/bin/fluxbox
```[/QUOTE]
 I have found a stange solution to the problem of course as im not good with debian, gentoo is what i know where id do rc-update del xdm default boot but as its debian ive no idea so i just got the init script for gdm and commented it all out so i dont run gdm on startup and im noww happy with fluxbox :D ah yes 

(debian is the only thing which is practical on my g3 400 mhz gentoo is better but too slow at compiling, macos9 sucks and os x 10.2 is far too slow under load with incificant programs developed for it with messed up program instalation.)

---

### Post by Sepero on 2005-02-05
[QUOTE=Josh101]I have found a stange solution to the problem of course as im not good with debian, gentoo is what i know where id do rc-update del xdm default boot but as its debian ive no idea so i just got the init script for gdm and commented it all out so i dont run gdm on startup and im noww happy with fluxbox :D ah yes[/QUOTE]I'm not very familiar with Gentoo, but I would guess that they copied this from Debian. Here's the Debian command:
update-rc.d gdm remove

---

### Post by shmonkey on 2005-02-05
To get fluxbox to show up in GDM create a new file /usr/share/xsessions/fluxbox.desktop.

Then add the following to it :

[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Exec=fluxbox
TryExec=fluxbox
# no icon yet, only the top three are currently used
Icon=
Type=Application

---

