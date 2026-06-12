---
title: "Ubuntu installer for Windows wubi.exe installs the 64 bit version"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by currter on 2011-07-03
Ubuntu installer for Windows wubi.exe installs the 64 bit version and there is
no choice to install the 32 bit version as my PC requires.
It apparently installs the ubuntu-11.04-desktop-amd64.iso.torrent file only.
 
Can this be corrected so that one has a choice and not have to burn a CD
to install alongside Windows?
 
Thank you.

---

### Post by Rubi1200 on 2011-07-03
Hi and welcome to the forums :-)

Use the option to install 32bit as outlined here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> either [pre-download the appropriate 32 bit ISO manually]("https://wiki.ubuntu.com/WubiGuide#ManuallyDownloadISO") and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument. To  modify arguments, right-click Wubi.exe and select "Create Shortcut".  Then right-click the shortcut, select Properties, and modify the Target  line, for example: "C:\Documents and  Settings\<user>\Desktop\wubi.exe" --32bit

---

### Post by isafdar on 2011-11-19
Dude follow the steps
1)copy the WUBi.EXE on your desktop
2)right click on the same file & create a shortcut.
3)go to Properties of the shortcut & in the TARGET you'll find something like C:\Users\home\Desktop\wubi.exe
4)instead of the above type the following as mentioned in 5)
5)C:\Users\home\Desktop\wubi.exe --32bit
6)Just a space between exe & --32bit.
7)Click APPLY & then OK
8)Double click & walla it DONE ;)
9)Njoy !

---

### Post by Rubi1200 on 2011-11-19
Hi and welcome to the forums isafdar :)

Thanks for sharing this additional information with the community.

Thread closed.

Reason: necromancy.

---

